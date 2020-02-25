---
title: v5.11中的特定配置
seo-title: v5.11中的特定配置
description: v5.11中的特定配置
seo-description: null
page-status-flag: never-activated
uuid: d6920beb-a766-4aec-8a8e-d32e47b545a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: fc280640-528d-44de-87d8-52f443772abd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# v5.11中的特定配置{#specific-configurations-in-v5-11}

本节详细介绍了从v5.11迁移时需要的其他配置。您还应配置“常规配置”部分中详细 [的设置](../../migration/using/general-configurations.md) 。

## Web应用程序 {#web-applications}

迁移期间将自动显示以下警告：

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Web应用程序的某些组件（例如各种公式字段）具有@id属性。 这些代码用于Web应用程序的XML代码中，不再以相同的方式生成。 它们在界面中不可见，您通常不能使用它们。 但是，在某些情况下，@id属性可能已用于个性化Web应用程序的呈现，例如通过样式表或使用JavaScript代码。

迁移期间，必 **须检查** （警告）中指定的日志文件路径：

* **文件不为空**:它包含警告，这些警告涉及迁移前记录的不一致，并且仍然存在。 这可以是引用不存在的ID的Web应用程序中的JavaScript代码。 必须检查并更正每个错误。
* **文件为空**:这意味着Adobe Campaign未检测到任何问题。

无论文件是否为空，您必须检查这些ID是否未用于其他位置的配置（如果是，请调整配置）。

## 工作流 {#workflows}

由于Adobe Campaign安装目录的名称已更改，因此在迁移后，某些工作流可能无法工作。 如果某个工作流在其某个活动中引用了nl5目录，则这将引发错误。 将此引用替换为 **内部版本**。 您可以运行SQL查询以标识这些工作流（PostgreSQL示例）:

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## 用户友好性 {#user-friendliness}

Adobe Campaign v5.11主页不再可用。

尽管不推荐，但如果您希望保留Adobe Campaign v5.11中的特定界面，则会有某些解决方案。如需更多信息，请联系我们。

## MySQL {#mysql}

>[!IMPORTANT]
>
>使用此引擎从版本6.02或5.11迁移时，MySQL仅作为主数据库引擎在v7中受支持。

默认情况下，MySQL不管理时区。 要启用时区管理，请运行以下命令：

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>有关详细信息，请参阅https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html [页面](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) 。

如果对数据库结构进行了修改，例如在配置（创建特定索引、创建SQL视图等）期间，迁移时应采取某些预防措施。 事实上，某些修改可以从与迁移过程的不兼容性中产生。 例如，创建包含 **Timestamp** 字段的SQL视图与 **usetimestamptz选项不兼容** 。 因此，我们建议您遵循以下建议：

1. 在开始迁移之前，请备份数据库。
1. 删除SQL更改。
1. 根据迁移到Adobe Campaign 7的先决条件部分中详细 [介绍的过程执行配置](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。
   >[!NOTE]
   >
   >您必须遵循迁移到Adobe Campaign 7的先决条件 [部分中介绍的迁移步骤](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。
1. 重新集成SQL更改。

在此示例中，已创 **建NmcTrackingLogMessages** 视图，该视图具有名为tslog的 **Timestamp** 字 **段**。 在这种情况下，迁移过程将失败，并显示以下错误消息：

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

要确保配置升级正常工作，您必须在迁移前删除视图，并在迁移后重新创建视图，同时使其适应TIMESTAMP WITH TIMEZONE模式。

## 跟踪 {#tracking}

跟踪公式已修改。 迁移时，旧公式(v5)将替换为新公式(v7)。 如果您在Adobe Campaign v5中使用个性化的公式，则必须在Adobe Campaign v7中调整此配置(**NmsTracking_ClickFormula** 和 **NmsTracking_OpenFormula** 选项)。

Web跟踪管理也进行了修改。 迁移到v7后，必须启动部署向导以完成Web跟踪的配置。

![](assets/migration_web_tracking.png)

有三种模式可用：

* **会话Web跟踪**:如果尚 **[!UICONTROL Leads]** 未安装该包，则默认情况下会选择此选项。 在性能方面，此选项最理想，它允许您限制跟踪日志的大小。
* **永久Web跟踪**
* **匿名Web跟踪**:如果安 **[!UICONTROL Leads]** 装了包，则默认情况下会选择此选项。 这是最耗资的选项。 如上所述，必 **须索引sSourceId** 列(在跟踪表和 **** CrmIncomingLead表中)。

>[!NOTE]
>
>有关这三种模式的详细信息，请参 [阅本节](../../configuration/using/about-web-tracking.md)。

## Adobe Campaign v7树结构 {#campaign-vseven-tree-structure}

在迁移过程中，将根据v7标准自动重新组织树结构。 将添加新文件夹，删除废弃的文件夹，并将其内容放在“移动”文件夹中。 迁移后，必须检查该文件夹中的所有项目，顾问必须决定保留或删除每个项目。 待保存的物品必须移到正确的位置。

已添加一个选项以禁用导航树的自动迁移。 此操作现在为手动操作。 不会删除过时的文件夹，也不会添加新文件夹。 仅当现成的v5导航树进行了太多更改时，才应使用此选项。 在迁移之前，在节点中向控制台添加以下 **[!UICONTROL Administration > Options]** 选项：

* 内部名称：NlMigration_KeepFolderStructure
* 数据类型：整数
* 值（文本）:1

如果您使用此选项，则在迁移后，您必须删除废弃的文件夹，添加新文件夹并运行所有必要的检查。

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
| xtkDashboard | 仪表板 | - |
| xtkPlatformAdmin | 平台 | - |
| nmsLocalOrgUnit | 组织单位 | - |
| nmsMRM | MRM | 已安装MRM |
| nmsOperations | 营销活动 | 已安装营销活动 |

**过时文件夹列表**:

迁移后要删除的过时文件夹如下：

>[!NOTE]
>
>必须检查废弃文件夹的整个内容，并且顾问会决定是保留还是删除每个项目。 要保存的物品必须移到相应的位置。

| 内部名称 | 标签 | 条件 |
|---|---|---|
| nmsAdministration | 管理 | - |
| nmsDeliveryMgt | 营销活动执行 | - |
| ncmContent | 内容管理 | 已安装Content Manager |
| ncmForm | 输入表单 | 已安装Content Manager |
| ncmImage | 图像 | 已安装Content Manager |
| ncmJavascript | JavaScript代码 | 已安装Content Manager |
| ncmJst | JavaScript模板 | 已安装Content Manager |
| ncmParameters | 配置 | 已安装Content Manager |
| ncmSrcSchema | 数据架构 | 已安装Content Manager |
| ncmStylesheet | XSL样式文件 | 已安装Content Manager |
| nmsAdminPlan | 管理 | 已安装营销活动 |
| nmsResourcePlan | 资源 | 已安装营销活动 |
| nmsResourcesModels | 模板 | 已安装营销活动 |
| nmsRootPlan | 营销活动管理 | 已安装营销活动 |
| nmsOperator | 营销运营商 | 已安装MRM |

