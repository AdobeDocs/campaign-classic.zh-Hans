---
product: campaign
title: 测试迁移
description: 测试迁移
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 4%

---

# 迁移测试{#testing-the-migration}

![](../../assets/v7-only.svg)

## 一般程序 {#general-procedure}

根据您的配置，可以通过多种方式执行迁移测试。

您应该拥有测试/开发环境来执行迁移测试。 Adobe Campaign环境需遵守以下许可：查看您的许可合同或与您的Adobe代表联系。

1. 停止所有正在进行的开发，并将其转移到生产环境。
1. 备份开发环境数据库。
1. 停止开发实例上的所有Adobe Campaign进程。
1. 备份生产环境数据库并将其恢复为开发环境。
1. 在启动Adobe Campaign服务之前，请运行 **freezeInstance.js** 烧蚀脚本，用于清除数据库中启动备份时正在运行的任何对象。

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >默认情况下，命令会在 **干燥** 模式，并列出该命令执行的所有请求，而无需启动它们。 要执行烧灼请求，请使用 **运行** 中。

1. 通过尝试恢复备份，确保备份正确无误。 确保可以访问数据库、表、数据等。
1. 在开发环境中测试迁移过程。
1. 如果开发环境的迁移成功，您可以迁移生产环境。

>[!CAUTION]
>
>由于对数据结构进行了更改，因此在v5平台和v7平台之间无法导入和导出数据包。


## 迁移工具 {#migration-tools}

通过各种选项，您可以衡量迁移的影响并确定潜在的问题。 将执行以下选项：

* 在 **配置** 命令：

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* 或在升级后：

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>* 您必须使用 **-instance:`<instanceame>`** 选项。 我们不建议使用 **-allinstances** 选项。
>* Adobe Campaign更新命令(**postupgrade**)可让您同步资源并更新架构和数据库。 此操作只能在应用程序服务器上执行一次且只能执行一次。 同步资源后， **postupgrade** 命令可让您检测同步是否生成任何错误或警告。


### 非标准或缺少的对象

* 的 **-showCustomEntities** 选项显示所有非标准对象的列表：

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   已发送消息的示例：

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* 的 **-showDeletedEntities** 选项显示数据库或文件系统中缺少的所有标准对象的列表。 对于每个缺失的对象，指定路径。

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
>您可以忽略JST-310040代码的所有警告和错误。

将搜索以下表达式（区分大小写）：

<table> 
 <thead> 
  <tr> 
   <th> 表达式<br /> </th> 
   <th> 错误代码<br /> </th> 
   <th> 日志类型<br /> </th> 
   <th> 评论<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 投放个性化不再支持此类语法。 <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 不得使用此库。<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(logon)<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 必须不再使用此连接方法。<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 仅当在从 <strong>sessionTokenOnly</strong> 模式。<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> 错误<br /> </td> 
   <td> 此类错误会导致迁移失败。<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> 错误<br /> </td> 
   <td> 不再支持此类部署。 Office 365和内部部署Microsoft CRM连接器部署类型现已弃用。 
   </br>如果您在外部帐户中使用其中一种已弃用的部署类型，则应删除此外部帐户，然后应运行 <b>postupgrade</b> 命令。 
   </br>要更改Web API部署，请参阅 <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Web应用程序</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> 错误<br /> </td> 
   <td> Microsoft CRM、Salesforce、Oracle CRM On Demand 操作活动不再可用。要配置Adobe Campaign与CRM系统之间的数据同步，您需要使用 <a href="../../workflow/using/crm-connector.md" target="_blank">CRM连接器</a> 定位活动。<br /> </td>
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
