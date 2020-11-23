---
solution: Campaign Classic
product: campaign
title: v5.11 中的特定配置
description: v5.11 中的特定配置
audience: migration
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 3%

---


# v5.11 中的特定配置{#specific-configurations-in-v5-11}

本节详细介绍了从v5.11迁移时需要的其他配置。您还应配置“常规配置”一节中 [详细介绍的](../../migration/using/general-configurations.md) 设置。

## Web 应用程序 {#web-applications}

迁移期间将自动显示以下警告：

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Web应用程序的某些组件（例如各种公式字段）具有@id属性。 这些代码用于Web应用程序的XML代码，不再以相同的方式生成。 它们在界面中不可见，通常不能使用它们。 但是，在某些情况下，@id属性可能已用于个性化Web应用程序的呈现，例如通过样式表或使用JavaScript代码。

迁移过程中， **必须** 检查警告中指定的日志文件路径：

* **文件不为空**:它包含警告，这些警告涉及迁移前记录的不一致情况，并且仍然存在。 这可以是引用不存在ID的Web应用程序中的JavaScript代码。 必须检查并更正每个错误。
* **文件为空**:这意味着Adobe Campaign未检测到任何问题。

无论文件是否为空，您必须检查这些ID是否未用于其他位置的配置（如果是，则调整配置）。

## 工作流 {#workflows}

由于Adobe Campaign安装目录的名称已更改，因此迁移后某些工作流可能无法工作。 如果工作流在其某个活动中引用了nl5目录，将引发错误。 将此引用替换为 **内部版本**。 您可以运行SQL查询来标识这些工作流（PostgreSQL示例）:

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## 方便用户 {#user-friendliness}

Adobe Campaignv5.11主页不再可用。

尽管不推荐，但如果您希望保留Adobe Campaignv5.11中的特定界面，则存在某些解决方案。有关详细信息，请与我们联系。

## MySQL {#mysql}

>[!IMPORTANT]
>
>使用此引擎从6.02或5.11版迁移时，MySQL仅作为主数据库引擎在v7中受支持。

默认情况下，MySQL不管理时区。 要启用时区管理，请运行以下命令：

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>有关详细信息，请参阅 [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) 页面。

如果对视图库结构进行了修改，例如在配置（创建特定索引、创建SQL等）期间，迁移时应采取某些预防措施。 事实上，某些修改可以由与迁移过程的不兼容性产生。 例如，创建包含Timestamp字段 **的SQL视图** ，与usetimestamptz选 **项不兼容** 。 因此，我们建议您遵循以下建议：

1. 在开始迁移之前，备份数据库。
1. 删除SQL更改。
1. 根据迁移到Adobe Campaign7部分的先决条件中详细 [介绍的过程执行配置](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。
   >[!NOTE]
   >
   >必须遵循迁移到Adobe Campaign7的先决条件部分 [中介绍的迁移步骤](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。
1. 重新集成SQL更改。

在此示例中，已 **创建NmcTrackingLogMessages** 视图，并且该具有名 **为tslog** 的Timestamp **字段**。 在这种情况下，迁移过程将失败，并显示以下错误消息：

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

要确保配置升级正常工作，您必须在迁移前删除视图，并在迁移后重新创建它，同时使其适应TIMESTAMP WITH TIMEZONE模式。

## 跟踪 {#tracking}

已修改跟踪公式。 迁移时，旧公式(v5)将替换为新公式(v7)。 如果您在Adobe Campaignv5中使用个性化的公式，则此配置必须在Adobe Campaignv7(**NmsTracking_ClickFormula** 和 **NmsTracking_OpenFormula选项** )中调整。

Web 跟踪管理也已修改。 迁移到v7后，必须开始部署向导以完成Web跟踪的配置。

![](assets/migration_web_tracking.png)

提供了三种模式：

* **会话Web跟踪**:如果包 **[!UICONTROL Leads]** 尚未安装，则默认情况下会选择此选项。 在性能方面，此选项最理想，它允许您限制跟踪日志的大小。
* **永久Web 跟踪**
* **匿名Web 跟踪**:如果安 **[!UICONTROL Leads]** 装了包，则默认情况下会选择此选项。 这是最耗资的选项。 如上所 **述** ，必须索引sSourceId列(在跟踪表和 **CrmIncomingLead表中** )。

>[!NOTE]
>
>有关这三种模式的详细信息，请参 [阅本节](../../configuration/using/about-web-tracking.md)。

## Adobe Campaignv7树结构 {#campaign-vseven-tree-structure}

在迁移过程中，将根据v7标准自动重新组织树结构。 将添加新文件夹，删除过时的文件夹，并将其内容放在“移动”文件夹中。 迁移后，必须检查此文件夹中的所有项目，顾问必须决定保留或删除每个项目。 待保存的物品必须移到正确的位置。

已添加一个选项，用于禁用导航树的自动迁移。 此操作现在为手动操作。 不删除已废弃的文件夹，也不添加新文件夹。 仅当现成的v5导航树进行了太多更改时，才应使用此选项。 在迁移之前，在节点中将选项添加到控制台 **[!UICONTROL Administration > Options]** 中：

* 内部名称：NlMigration_KeepFolderStructure
* 数据类型：整数
* 值（文本）:1

如果使用此选项，则迁移后必须删除已废弃的文件夹，添加新文件夹并运行所有必要的检查。

**列表新文件夹**:

迁移后需要添加以下文件夹：

| 内部名称 | 标签 | 条件 |
|---|---|---|
| nmsAutoObjects | 自动创建的对象 | - |
| nmsCampaignAdmin | 活动管理 | - |
| nmsCampaignMgt | 活动管理 | - |
| nmsCampaignRes | 活动管理 | - |
| nmsModels | 模板 | - |
| nmsOnlineRes | 在线 | - |
| nmsProduction | Production | - |
| nmsProfilProcess | 流程 | - |
| xtkDashboard | 仪表板 | - |
| xtkPlatformAdmin | 平台 | - |
| nmsLocalOrgUnit | 组织单位 | - |
| nmsMRM | MRM | 已安装MRM |
| nmsOperations | 营销策划 | 活动安装 |

**列表废弃的文件夹**:

迁移后要删除的过时文件夹如下：

>[!NOTE]
>
>必须检查已废弃文件夹的整个内容，顾问会决定是否保留或删除每个项目。 必须将要保存的物品移至相应位置。

| 内部名称 | 标签 | 条件 |
|---|---|---|
| nmsAdministration | 管理 | - |
| nmsDeliveryMgt | 活动执行 | - |
| ncmContent | 内容管理 | 已安装内容管理器 |
| ncmForm | 输入表单 | 已安装内容管理器 |
| ncmImage | 图像 | 已安装内容管理器 |
| ncmJavascript | JavaScript代码 | 已安装内容管理器 |
| ncmJst | JavaScript模板 | 已安装内容管理器 |
| ncmParameters | 配置 | 已安装内容管理器 |
| ncmSrcSchema | 数据模式 | 已安装内容管理器 |
| ncmStylesheet | XSL样式文件 | 已安装内容管理器 |
| nmsAdminPlan | 管理 | 活动安装 |
| nmsResourcePlan | 资源 | 活动安装 |
| nmsResourcesModels | 模板 | 活动安装 |
| nmsRootPlan | 活动管理 | 活动安装 |
| nmsOperator | 营销运营商 | 已安装MRM |

