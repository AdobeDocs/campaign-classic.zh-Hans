---
title: 测试迁移
seo-title: 测试迁移
description: 测试迁移
seo-description: null
page-status-flag: never-activated
uuid: 3ee6a10b-dea2-41c6-9aef-ee3ac922b459
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 30e3082f-a367-4c3b-bff2-208ccf97acd4
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 1%

---


# 测试迁移{#testing-the-migration}

## 一般程序 {#general-procedure}

根据您的配置，可通过多种方式执行迁移测试。

您应具有测试／开发环境来执行迁移测试。 开发环境需遵守许可：检查您的许可合同或与Adobe Campaign的销售服务联系。

1. 停止所有正在进行的开发，并将其交付到生产环境。
1. 备份开发环境库。
1. 停止开发实例上的所有Adobe Campaign进程。
1. 备份生产环境环境库，并将其恢复为开发。
1. 在启动Adobe Campaign服务之前，请运 **行freezeInstance** .js烧灼脚本，该脚本允许您清除启动备份时正在运行的任何对象的数据库。

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >默认情况下，该命令以 **干** 模式启动，并列表该命令执行的所有请求，而不启动它们。 要执行烧灼请求，请 **在命令** 中使用run。

1. 通过尝试恢复备份，确保备份正确无误。 确保您可以访问数据库、表、数据等。
1. 在开发环境测试迁移过程。

   迁移到Adobe Campaign7部分的先决条件 [中详细介绍了完整的过程](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。

1. 如果开发环境迁移成功，则可以迁移生产环境。

>[!IMPORTANT]
>
>由于对数据包结构进行了更改，在v5平台和v7平台之间无法导入和导出数据。

>[!NOTE]
>
>Adobe Campaign更新命令(**postupgrade**)可让您同步资源并更新模式和数据库。 此操作只能在应用程序服务器上执行一次。 同步资源后， **postupgrade命令** 允许您检测同步是否生成任何错误或警告。

## 迁移工具 {#migration-tools}

通过各种选项，您可以衡量迁移的影响并确定潜在问题。 将执行以下选项：

* 在config **命令** :

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* 或者在postupgrade:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>必须使用 **实例：`<instanceame>`** 选项。 我们不建议使用- **allinstances选项** 。

### -showCustomEntities和-showDeletedEntities选项 {#showcustomentities-and--showdeletedentities-options}

* - **showCustomEntities** 选项显示所有非标准对象的列表:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   已发送消息的示例：

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* - **showDeletedEntities** 选项显示列表库或文件系统中缺失的所有标准对象的。 对于每个缺少的对象，指定路径。

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   已发送消息的示例：

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### 验证过程 {#verification-process}

该过程作为postupgrade命令中的标准集成，允许您显示可能导致迁移失败的警告和错误。 **如果显示错误，则迁移尚未执行。** 如果发生这种情况，请更正所有错误，然后重新开始错误。

您可以使用以下命令开始验证过程（不进行迁移）:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>请忽略包含JST-310040代码的所有警告和错误。

搜索以下表达式（区分大小写）:

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
   <td> 投放个性化不再支持此类语法。 请参阅 <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>。 否则，检查值类型是否正确。<br /> </td> 
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
   <td> 此连接方法必须不再使用。 请参阅已识 <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">别的Web应用程序</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 仅当在从处于sessionTokenOnly模式的安全区域执行的JavaScript代码中使用此函数时，才 <strong>支持此函</strong> 数。<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> 错误<br /> </td> 
   <td> 此类型的错误导致迁移失败。 请参阅 <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> 错误<br /> </td> 
   <td> 此类型的错误导致迁移失败。 请参阅 <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>。 如果获得概述类型的Web应用程序错误日志（从v6.02迁移），请参阅 <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Web 应用程序</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

还进行了数据库和模式一致性检查。

### 恢复选项 {#restoration-option}

通过此选项，可以恢复现成的对象（如果已修改）。 对于每个还原的对象，更改的备份会存储在所选文件夹中：

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>我们强烈建议使用绝对文件夹路径并保留文件夹树结构。 例如：backupFolder\nms\srcSchema\billing.xml。

### 恢复迁移 {#resuming-migration}

如果在迁移失败后重新启动程序升级，它将从停止的同一位置恢复。
