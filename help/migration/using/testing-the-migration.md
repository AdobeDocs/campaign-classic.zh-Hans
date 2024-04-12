---
product: campaign
title: 测试迁移
description: 测试迁移
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# 迁移测试{#testing-the-migration}



## 一般程序 {#general-procedure}

根据您的配置，可通过多种方法来执行迁移测试。

您应该有一个测试/开发环境来执行迁移测试。 Adobe Campaign环境受许可证约束：请检查您的许可证合同或联系您的Adobe代表。

1. 停止所有正在进行的开发并将其转移到生产环境。
1. 备份开发环境数据库。
1. 停止开发实例上的所有Adobe Campaign进程。
1. 制作生产环境数据库的备份，并将其恢复为开发环境。
1. 在启动Adobe Campaign服务之前，请运行 **freezeInstance.js** 烧灼脚本，用于清除启动备份时正在运行的任何对象的数据库。

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >该命令默认在中启动 **干燥** 模式，并列出该命令执行的所有请求，而不启动它们。 要执行烧灼请求，请使用 **运行** 在命令中。

1. 尝试恢复备份以确保其正确。 确保您可以访问数据库、表格、数据等。
1. 在开发环境中测试迁移过程。
1. 如果开发环境的迁移成功，则可以迁移生产环境。

>[!CAUTION]
>
>由于对数据结构进行了更改，无法在v5平台和v7平台之间导入和导出数据包。


## 迁移工具 {#migration-tools}

您可以使用各种选项衡量迁移的影响并确定潜在问题。 将执行以下选项：

* 在 **config** 命令：

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* 或在升级后：

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* 您必须使用 **-instance：`<instanceame>`** 选项。 我们不建议使用 **-allinstances** 选项。
>* Adobe Campaign update命令(**升级后**)用于同步资源并更新架构和数据库。 此操作只能在应用程序服务器上执行一次。 同步资源后， **升级后** 命令用于检测同步是否生成任何错误或警告。

### 非标准或缺少对象

* 此 **-showCustomEntities** 选项显示所有非标准对象的列表：

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  已发送消息的示例：

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* 此 **-showDeletedEntities** 选项显示数据库或文件系统中缺少的所有标准对象的列表。 对于每个缺少的对象，指定路径。

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  已发送消息的示例：

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### 验证过程 {#verification-process}

在升级后命令中作为标准流程集成，此过程允许您显示可能导致迁移失败的警告和错误。 **如果显示错误，则表示尚未执行迁移。** 如果发生这种情况，请更正所有错误，然后重新启动升级后。

您可以使用命令自行启动验证过程（无需迁移）：

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>您可以使用JST-310040代码忽略所有警告和错误。

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
   <td> 投放个性化中不再支持此类语法。 <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 不得使用此库。<br /> </td> 
  </tr> 
  <tr> 
   <td> 登录(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 必须不再使用此连接方法。<br /> </td> 
  </tr> 
  <tr> 
   <td> 新SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 仅当在的安全区域中执行的JavaScript代码中使用此函数时，才支持使用此函数。 <strong>sessionTokenOnly</strong> 模式。<br /> </td> 
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
   <td> 不再支持此类型的部署。 Office 365和内部部署Microsoft CRM连接器部署类型现已弃用。 
   </br>如果您在外部帐户中使用这些已弃用的部署类型之一，则应删除此外部帐户，然后运行 <b>升级后</b> 命令。 
   </br>要更改为Web API部署，请参阅 <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Web应用程序</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> 错误<br /> </td> 
   <td> Microsoft CRM、Salesforce、OracleCRM按需操作活动不再可用。 要配置Adobe Campaign与CRM系统之间的数据同步，您需要使用 <a href="../../workflow/using/crm-connector.md" target="_blank">CRM连接器</a> 定位活动。<br /> </td>
  </tr> 
 </tbody> 
</table>

还进行了数据库和模式一致性检查。

### 恢复选项 {#restoration-option}

此选项允许您恢复现成对象（如果已修改）。 对于每个已恢复的对象，更改备份将存储在所选文件夹中：

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>我们强烈建议使用绝对文件夹路径并保留文件夹树结构。 例如：backupFolder\nms\srcSchema\billing.xml。

### 恢复迁移 {#resuming-migration}

如果在迁移失败后重新启动升级后，它将从停止的位置恢复。
