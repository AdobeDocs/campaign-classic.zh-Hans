---
product: campaign
title: 调整配置
description: 了解如何在迁移到Campaign v7前后调整配置
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 3%

---

# 调整配置{#configuring-your-platform}

![](../../assets/v7-only.svg)

Adobe Campaign v7中的某些主要更改需要特定配置。 在迁移之前或之后，可能需要这些配置。

从Campaign v5或v6迁移时，将在Adobe Campaign v7中执行的详细配置可在 [本页](general-configurations.md).


在迁移期间， **NmsRecipient** 表是根据架构定义重建的。 对此表的SQL结构在Adobe Campaign外所做的任何更改都将丢失。

要检查的元素示例：

* 如果已在 **NmsRecipient** 表格，但您尚未在架构中详细说明该内容，因此不会保存该表格。
* 的 **表空间** 默认情况下，属性会返回其值，即在部署向导中定义的值。
* 如果已将引用视图添加到 **NmsRecipient** 表格，则必须在迁移之前将其删除。


## 迁移之前 {#before-the-migration}

迁移到Adobe Campaign v7时，必须配置以下元素。 在启动 **postupgrade**.

* 时区

   从v5.11平台迁移期间，您必须指定在升级后期间使用的时区。

   如果您希望使用“多时区”模式，请参阅 [此部分](../../migration/using/general-configurations.md#time-zones).

   如果将Oracle用作数据库，请检查Oracle时区文件是否已在应用程序服务器和数据库服务器之间正确同步。 [了解详情](../../migration/using/general-configurations.md#oracle)

* 安全区

   出于安全考虑，Adobe Campaign平台默认不再可访问：您必须配置安全区，这要求在迁移之前收集用户IP地址。 [了解详情](../../migration/using/general-configurations.md#security)

* 语法

   由于使用了新的解释器，v7版本中可能不再接受某些Javascript代码。 [了解详情](../../migration/using/general-configurations.md#javascript)。

   同样，Adobe Campaign v7中引入了新语法来替换基于SQLData的语法。 如果将代码元素与此语法一起使用，则必须调整它们。 [了解详情](../../migration/using/general-configurations.md#sqldata)

* 密码

   您必须配置 **管理员** 和 **内部** 密码。 [了解详情](../../migration/using/before-starting-migration.md#user-passwords)

* 树结构

   如果从v5.11平台迁移，则必须根据Adobe Campaign v6规范重新组织树结构文件夹。 [了解详情](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)。

* 互动

   如果您是从Campaign v6.02迁移，并使用  **互动** 模块中，您必须删除v7中不再存在的所有6.02架构引用。 [了解详情](../../migration/using/general-configurations.md#interaction)

## 迁移后 {#after-the-migration}

运行后 **postupgrade**，请检查并配置以下元素：

* 镜像页面

   镜像页面个性化块已随v6.x发生更改。此新版本可提高访问这些页面时的安全性。

   如果在消息中使用v5个性化块，则镜像页面显示将失败。 Adobe强烈建议在消息中插入镜像页面时使用新的个性化块。

   但是，作为临时解决方法（以及由于镜像页面仍处于实时状态），您可以通过更改选项返回到旧的个性化块以避免此问题 **[!UICONTROL XtkAcceptOldPasswords]** 将其设置为 **[!UICONTROL 1]**. 这不会影响新v6.x个性化块的使用。

* 语法

   如果遇到与语法相关的任何错误，则在升级后期间必须临时激活 **allowSQLInjent** 选项 **serverConf.xml** 文件，因为这样您就有时间重写代码。 修改代码后，请确保重新激活安全性。 [了解详情](../../migration/using/general-configurations.md#sqldata)

* 冲突

   迁移是通过升级后执行的，冲突可能会显示在报表、表单或Web应用程序中。 这些冲突可以从控制台中解决。 [了解详情](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   如果您自定义了安装文件夹，请确保检查迁移后文件夹是否正确更新。 [了解详情](../../migration/using/general-configurations.md#tomcat)

* 报告

   当前所有现成的报表都使用v6.x渲染引擎。 如果您已将JavaScript代码添加到报表中，则某些元素可能会受到影响。 [了解详情](../../migration/using/general-configurations.md#reports)

* Web应用程序

   在升级后，如果在连接到已识别的Web应用程序时遇到任何问题，则必须激活 **allowUserPassword** 和 **sessionTokenOnly** 选项 **serverConf.xml** 文件。 要避免出现任何安全问题，必须在问题解决后重新激活这两个选项。 [了解详情](../../migration/using/general-configurations.md#identified-web-applications)

   根据Web应用程序的类型及其配置，必须执行其他操作以确保它们正常工作。 [了解详情](../../migration/using/general-configurations.md#web-applications)

   如果从v5.11平台迁移，则必须执行其他配置。 [了解详情](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* 安全区

   启动服务器之前，必须配置安全区。 [了解更多](../../installation/using/security-zones.md) 和 [请参阅此处](../../migration/using/general-configurations.md#security)

* 工作流

   如果从v5.11平台迁移，则必须检查工作流文件夹。 [了解详情](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* 跟踪

   如果从v5.11平台迁移，则必须配置跟踪模式。 [了解详情](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* 互动

   如果您使用 **互动**，则迁移后必须调整任何参数。 [了解详情](../../migration/using/general-configurations.md#interaction)

* 功能板

   如果出现客户端错误，您必须使用新的Adobe Campaign v7代码更新功能板，或手动将以下文件从v6.02实例复制到v7实例：

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## 从v5.11到v7的特定配置{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

本节详细介绍从v5.11迁移时需要的其他配置。您还应在 [一般配置](../../migration/using/general-configurations.md) 中。

### Web 应用程序 {#web-applications-v5}

迁移期间将自动显示以下警告：

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Web应用程序的某些组件（例如各种公式字段）具有@id属性。 这些代码用于Web应用程序的XML代码中，并且不再以相同的方式生成。 它们在界面中不可见，您通常不得使用它们。 但是，在某些情况下，@id属性可能已用于个性化Web应用程序的渲染，例如通过样式表或使用JavaScript代码。

在迁移期间，您 **必须** 检查警告中指定的日志文件路径：

* **文件不为空**:其中包含有关迁移前记录的不一致且仍然存在的警告。 这可以是引用不存在ID的Web应用程序中的JavaScript代码。 必须检查并更正每个错误。
* **文件为空**:这意味着Adobe Campaign未检测到任何问题。

无论文件是否为空，您都必须检查这些ID是否不用于其他位置的配置（如果是，则调整配置）。

### 工作流 {#workflows}

由于Adobe Campaign安装目录的名称已更改，因此迁移后某些工作流可能无法工作。 如果工作流在其活动之一中引用了nl5目录，则会引发错误。 将此引用替换为 **构建**. 您可以运行SQL查询以标识这些工作流（PostgreSQL示例）：

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>使用此引擎从版本6.02或5.11迁移时，v7仅作为主数据库引擎支持MySQL。

MySQL默认不管理时区。 要启用时区管理，请运行以下命令：

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>有关更多信息，请参阅 [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) 页面。

如果对数据库结构进行了修改，例如在配置期间（创建特定索引、创建SQL视图等），则在迁移时应采取某些预防措施。 事实上，某些修改可能因与迁移过程的不兼容性而产生。 例如，创建包含 **时间戳** 字段与 **usetimestamptz** 选项。 因此，我们建议您遵循以下建议：

1. 在开始迁移之前，请备份数据库。
1. 删除SQL更改。
1. 执行升级后
   >[!NOTE]
   >
   >您必须按照 [此部分](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. 重新集成SQL更改。

在本例中， **NmcTrackingLogMessages** 视图已创建，且 **时间戳** 字段名称 **tslog**. 在这种情况下，迁移过程失败，并出现以下错误消息：

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

要确保后期升级正常工作，您必须在迁移之前删除视图，并在迁移后重新创建视图，同时将其调整为带有时区的TIMESTAMP模式。

### 跟踪 {#tracking}

跟踪公式已修改。 迁移时，旧公式(v5)将被新公式(v7)替换。 如果您在Adobe Campaign v5中使用个性化公式，则必须在Adobe Campaign v7(**NmsTracking_ClickFormula** 和 **NmsTracking_OpenFormula** 选项)。

Web跟踪管理也已修改。 迁移到v7后，必须启动部署向导才能完成Web跟踪的配置。

![](assets/migration_web_tracking.png)

提供了三种模式：

* **会话Web跟踪**:如果 **[!UICONTROL Leads]** 包尚未安装，默认情况下选中此选项。 就性能而言，此选项是最理想的选项，它允许您限制跟踪日志的大小。
* **永久Web跟踪**
* **匿名Web跟踪**:如果 **[!UICONTROL Leads]** 包安装后，此选项默认处于选中状态。 这是最耗资的选项。 如上所述， **sSourceId** 列必须已编入索引(在跟踪表和 **CrmIncomingLead** 表)。

>[!NOTE]
>
>有关这三种模式的详细信息，请参阅 [此部分](../../configuration/using/about-web-tracking.md).

### Adobe Campaign v7树结构 {#campaign-vseven-tree-structure}

在迁移过程中，将根据v7标准自动重组树结构。 将添加新文件夹，删除过时的文件夹，并将其内容放在“要移动”文件夹中。 迁移后，必须检查此文件夹中的所有项目，顾问必须决定保留或删除每个项目。 然后，要保留的项目必须移动到正确的位置。

添加了一个选项，用于禁用导航树的自动迁移。 此操作现在为手动操作。 不会删除过时的文件夹，也不会添加新文件夹。 仅当现成的v5导航树发生了太多更改时，才应使用此选项。 在迁移前，在控制台的 **[!UICONTROL Administration > Options]** 节点：

* 内部名称：NlMigration_KeepFolderStructure
* 数据类型：整数
* 值（文本）：1

如果使用此选项，则在迁移后，必须删除过时的文件夹，添加新文件夹并运行所有必要的检查。

**新文件夹列表**:

迁移后需要添加以下文件夹：

| 内部名称 | 标签 | 条件 |
|---|---|---|
| nmsAutoObjects | 自动创建的对象 | - |
| nmsCampaignAdmin | 营销活动管理 | - |
| nmsCampaignMgt | 营销活动管理 | - |
| nmsCampaignRes | 营销活动管理 | - |
| nmsModels | 模板 | - |
| nmsOnlineRes | 在线 | - |
| nmsProduction | 生产 | - |
| nmsProfilProcess | 流程 | - |
| xtkDashboard | 功能板 | - |
| xtkPlatformAdmin | 平台 | - |
| nmsLocalOrgUnit | 组织实体 | - |
| nmsMRM | MRM | 已安装MRM |
| nmsOperations | 活动 | 已安装Campaign |

**过时文件夹列表**:

迁移后要删除的过时文件夹如下：

>[!NOTE]
>
>必须检查过时文件夹的整个内容，并且顾问会决定是保留还是删除每个项目。 必须将要保留的项目移动到相应的位置。

| 内部名称 | 标签 | 条件 |
|---|---|---|
| nmsAdministration | 管理 | - |
| nmsDeliveryMgt | 促销活动执行 | - |
| ncmContent | 内容管理 | 已安装内容管理器 |
| ncmForm | 输入表单 | 已安装内容管理器 |
| ncmImage | 图像 | 已安装内容管理器 |
| ncmJavascript | JavaScript代码 | 已安装内容管理器 |
| ncmJst | JavaScript模板 | 已安装内容管理器 |
| ncmParameters | 配置 | 已安装内容管理器 |
| ncmSrcSchema | 数据模式 | 已安装内容管理器 |
| ncmStylesheet | XSL样式文件 | 已安装内容管理器 |
| nmsAdminPlan | 管理 | 已安装Campaign |
| nmsResourcePlan | 资源 | 已安装Campaign |
| nmsResourcesModels | 模板 | 已安装Campaign |
| nmsRootPlan | 营销活动管理 | 已安装Campaign |
| nmsOperator | 营销运营商 | 已安装MRM |


## 从v6.02到v7的特定配置{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

以下部分详细介绍了从v6.02迁移时需要的其他配置。您还应当配置 [本页](../../migration/using/general-configurations.md).

### Web 应用程序 {#web-applications-v6}

如果您从v6.02迁移，则可能会显示有关概述类型Web应用程序的错误日志。 错误消息示例：

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

这些Web应用程序使用SQLData，并且由于安全性较高而与v7不兼容。 这些错误将导致迁移失败。

如果您未使用这些Web应用程序，请运行以下清理脚本并重新运行后级：

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

如果您已修改这些Web应用程序并希望继续在v7中使用它们，则必须激活 **allowSQLInjent** 选项，然后重新启动升级后。 请参阅 [SQLData](../../migration/using/general-configurations.md#sqldata) 的详细信息。

### 消息中心 {#message-center}

迁移消息中心控制实例后，必须重新发布事务型消息模板才能使用。

在v7中，执行实例上事务型消息模板的名称已发生更改。 它们当前由与在其上创建它们的控制实例对应的运算符名称来前缀，例如 **control1_template1_rt** (其中 **control1** 是运算符的名称)。 如果您有大量模板，我们建议在控制实例中删除旧模板。