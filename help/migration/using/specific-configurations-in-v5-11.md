---
product: campaign
title: v5.11 中的特定配置
description: v5.11 中的特定配置
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 978e1249-f79b-4f5f-9a94-3bb2510785de
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 3%

---

# v5.11 中的特定配置{#specific-configurations-in-v5-11}

本节详细介绍从v5.11迁移时需要的其他配置。您还应当配置[常规配置](../../migration/using/general-configurations.md)部分中详细的设置。

## Web 应用程序 {#web-applications}

迁移期间将自动显示以下警告：

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Web应用程序的某些组件（例如各种公式字段）具有@id属性。 这些代码用于Web应用程序的XML代码中，并且不再以相同的方式生成。 它们在界面中不可见，您通常不得使用它们。 但是，在某些情况下，@id属性可能已用于个性化Web应用程序的渲染，例如通过样式表或使用JavaScript代码。

在迁移期间，您&#x200B;**必须**&#x200B;检查警告中指定的日志文件路径：

* **文件不为空**:其中包含有关迁移前记录的不一致且仍然存在的警告。这可以是引用不存在ID的Web应用程序中的JavaScript代码。 必须检查并更正每个错误。
* **文件为空**:这意味着Adobe Campaign未检测到任何问题。

无论文件是否为空，您都必须检查这些ID是否不用于其他位置的配置（如果是，则调整配置）。

## 工作流 {#workflows}

由于Adobe Campaign安装目录的名称已更改，因此迁移后某些工作流可能无法工作。 如果工作流在其活动之一中引用了nl5目录，则会引发错误。 将此引用替换为&#x200B;**build**。 您可以运行SQL查询以标识这些工作流（PostgreSQL示例）：

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## 用户友好性{#user-friendliness}

Adobe Campaign v5.11主页不再可用。

虽然不建议使用，但是如果您希望保留Adobe Campaign v5.11中的特定界面，则有一些解决方案。有关详细信息，请与我们联系。

## MySQL {#mysql}

>[!IMPORTANT]
>
>使用此引擎从版本6.02或5.11迁移时，v7仅作为主数据库引擎支持MySQL。

MySQL默认不管理时区。 要启用时区管理，请运行以下命令：

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>有关更多信息，请参阅[https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html)页面。

如果对数据库结构进行了修改，例如在配置期间（创建特定索引、创建SQL视图等），则在迁移时应采取某些预防措施。 事实上，某些修改可能因与迁移过程的不兼容性而产生。 例如，创建包含&#x200B;**Timestamp**&#x200B;字段的SQL视图与&#x200B;**usetimestamptz**&#x200B;选项不兼容。 因此，我们建议您遵循以下建议：

1. 在开始迁移之前，请备份数据库。
1. 删除SQL更改。
1. 根据[迁移到Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)的先决条件部分中详述的过程执行升级后。
   >[!NOTE]
   >
   >您必须按照[迁移到Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)的先决条件部分中介绍的迁移步骤操作。
1. 重新集成SQL更改。

在此示例中，已创建&#x200B;**NmcTrackingLogMessages**&#x200B;视图，该视图具有名为&#x200B;**tslog**&#x200B;的&#x200B;**Timestamp**&#x200B;字段。 在这种情况下，迁移过程失败，并出现以下错误消息：

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

要确保后期升级正常工作，您必须在迁移之前删除视图，并在迁移后重新创建视图，同时将其调整为带有时区的TIMESTAMP模式。

## 跟踪 {#tracking}

跟踪公式已修改。 迁移时，旧公式(v5)将被新公式(v7)替换。 如果您在Adobe Campaign v5中使用个性化公式，则必须在Adobe Campaign v7（**NmsTracking_ClickFormula**&#x200B;和&#x200B;**NmsTracking_OpenFormula**&#x200B;选项）中调整此配置。

Web跟踪管理也已修改。 迁移到v7后，必须启动部署向导才能完成Web跟踪的配置。

![](assets/migration_web_tracking.png)

提供了三种模式：

* **会话Web跟踪**:如果尚 **[!UICONTROL Leads]** 未安装包，则默认情况下会选中此选项。就性能而言，此选项是最理想的选项，它允许您限制跟踪日志的大小。
* **永久Web跟踪**
* **匿名Web跟踪**:如果安 **[!UICONTROL Leads]** 装了包，则默认情况下会选中此选项。这是最耗资的选项。 如上所述，必须对&#x200B;**sSourceId**&#x200B;列进行索引（在跟踪表和&#x200B;**CrmIncomingLead**&#x200B;表中）。

>[!NOTE]
>
>有关这三种模式的详细信息，请参阅[此部分](../../configuration/using/about-web-tracking.md)。

## Adobe Campaign v7树结构{#campaign-vseven-tree-structure}

在迁移过程中，将根据v7标准自动重组树结构。 将添加新文件夹，删除过时的文件夹，并将其内容放在“要移动”文件夹中。 迁移后，必须检查此文件夹中的所有项目，顾问必须决定保留或删除每个项目。 然后，要保留的项目必须移动到正确的位置。

添加了一个选项，用于禁用导航树的自动迁移。 此操作现在为手动操作。 不会删除过时的文件夹，也不会添加新文件夹。 仅当现成的v5导航树发生了太多更改时，才应使用此选项。 在迁移前，在&#x200B;**[!UICONTROL Administration > Options]**&#x200B;节点中向控制台添加选项：

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
| nmsProduction | 制作 | - |
| nmsProfilProcess | 流程 | - |
| xtkDashboard | 功能板 | - |
| xtkPlatformAdmin | 平台 | - |
| nmsLocalOrgUnit | 组织单位 | - |
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
