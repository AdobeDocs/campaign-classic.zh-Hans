---
product: campaign
title: 测试迁移
description: 测试迁移
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 571dd96d1f3bff5c3dab05dce5319f913f29a670
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 1%

---

# 测试迁移{#testing-the-migration}

## 一般程序 {#general-procedure}

根据您的配置，可以通过多种方式执行迁移测试。

您应该拥有测试/开发环境来执行迁移测试。 开发环境需遵守以下许可：查看您的许可合同或联系Adobe Campaign的销售服务。

1. 停止所有正在进行的开发，并将其转移到生产环境。
1. 备份开发环境数据库。
1. 停止开发实例上的所有Adobe Campaign进程。
1. 备份生产环境数据库并将其恢复为开发环境。
1. 在启动Adobe Campaign服务之前，请运行&#x200B;**freezeInstance.js**&#x200B;烧灼脚本，该脚本允许您清除启动备份时运行的任何对象的数据库。

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >默认情况下，该命令会在&#x200B;**dry**&#x200B;模式下启动，并列出该命令执行的所有请求，而无需启动它们。 要执行烧灼请求，请在命令中使用&#x200B;**run**。

1. 通过尝试恢复备份，确保备份正确无误。 确保可以访问数据库、表、数据等。
1. 在开发环境中测试迁移过程。

   [迁移到Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)的先决条件部分详细介绍了完整过程。

1. 如果开发环境的迁移成功，您可以迁移生产环境。

>[!IMPORTANT]
>
>由于对数据结构进行了更改，因此在v5平台和v7平台之间无法导入和导出数据包。

>[!NOTE]
>
>使用Adobe Campaign update命令(**postupgrade**)可同步资源并更新架构和数据库。 此操作只能在应用程序服务器上执行一次且只能执行一次。 在同步资源后，使用&#x200B;**postupgrade**&#x200B;命令可以检测同步是否生成任何错误或警告。

## 迁移工具 {#migration-tools}

通过各种选项，您可以衡量迁移的影响并确定潜在的问题。 将执行以下选项：

* 在&#x200B;**config**&#x200B;命令中：

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* 或在升级后：

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>必须使用&#x200B;**-instance:`<instanceame>`**&#x200B;选项。 我们不建议使用&#x200B;**-allinstances**&#x200B;选项。

### -showCustomEntities和 — showDeletedEntities选项 {#showcustomentities-and--showdeletedentities-options}

* **-showCustomEntities**&#x200B;选项显示所有非标准对象的列表：

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   已发送消息的示例：

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* **-showDeletedEntities**&#x200B;选项显示数据库或文件系统中缺少的所有标准对象的列表。 对于每个缺失的对象，指定路径。

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   已发送消息的示例：

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### 验证过程 {#verification-process}

此过程作为后级命令中的标准集成，允许您显示可能导致迁移失败的警告和错误。 **如果显示错误，则未执行迁移。** 如果发生这种情况，请更正所有错误，然后重新启动升级后。

您可以使用以下命令自行启动验证过程（不进行迁移）：

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>请忽略所有包含JST-310040代码的警告和错误。

将搜索以下表达式（区分大小写）：

<table> 
 <thead> 
  <tr> 
   <th> 表达式<br /> </th> 
   <th> 错误代码<br /> </th> 
   <th> 日志类型<br /> </th> 
   <th> 注释<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 投放个性化不再支持此类语法。 请参阅<a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>。 否则，请检查值类型是否正确。<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 不得使用此库。<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 必须不再使用此连接方法。 请参阅<a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">已识别的Web应用程序</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 仅当在从<strong>sessionTokenOnly</strong>模式下的安全区域执行的JavaScript代码中使用此函数时，才支持此函数。<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> 错误<br /> </td> 
   <td> 此类错误会导致迁移失败。 请参阅<a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> 错误<br /> </td> 
   <td> 此类错误会导致迁移失败。 请参阅<a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>。 如果您收到概述类型的Web应用程序错误日志（从v6.02迁移），请参阅<a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">配置Campaign</a>。<br /> </td> 
  </tr>
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> 错误<br /> </td> 
   <td> 不再支持此类部署。 Office 365和内部部署Microsoft CRM连接器部署类型现已弃用</a>。 要更改Web API部署，请参阅<a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Web应用程序</a>。<br /> </td>
  </tr> 
 </tbody> 
</table>

还进行了数据库和模式一致性检查。

### 还原选项 {#restoration-option}

利用此选项，可恢复已修改的现成对象。 对于每个已还原的对象，更改的备份将存储在选定的文件夹中：

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>我们强烈建议使用绝对文件夹路径并保留文件夹树结构。 例如：backupFolder\nms\srcSchema\billing.xml。

### 恢复迁移 {#resuming-migration}

如果在迁移失败后重新启动升级后，升级会从停止后的同一位置恢复。
