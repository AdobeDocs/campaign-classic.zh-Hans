---
title: 一般导入和导出
seo-title: 一般导入和导出
description: 一般导入和导出
seo-description: null
page-status-flag: never-activated
uuid: e98753bb-1f14-4ec7-aa3b-d5e4f1ebaef7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: a21576c7-e94c-4fe1-9e31-d89116e427f6
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 55%

---


# 一般导入和导出{#generic-imports-and-exports}

Adobe Campaign 提供了一个数据导出模块，可以轻松提取客户或潜在客户清单（例如，在定位操作之后），然后他们将成为目标人群的一部分。

Adobe Campaign 还提供了一个导入模块，可让您使用外部文件为数据库提供数据。

>[!NOTE]
>
>Exports and imports are configured in dedicated templates executed through workflows via the **[!UICONTROL Import]** and **[!UICONTROL Export]** activities. 它们可以根据时间表自动重复，例如用于在多个信息系统之间自动交换数据。If necessary, you can create an occasional import or export via the **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** node of the Adobe Campaign tree.

您可以：

* 创建导入或导出模板并对其进行配置（参见下文）。
* 创建导入或导出：请参阅导 [出数据](../../platform/using/exporting-data.md) 或 [导入数据](../../platform/using/importing-data.md)。
* 启动导入或导出并监视其执行。 请参阅 [执行跟踪](#execution-tracking)。

>[!CAUTION]
>
>Campaign 中的数据导入应通过工作流程执行，以确保数据一致性并提高效率。有关详细信息，请参见[导入数据](../../workflow/using/importing-data.md)、[导入最佳实践](../../workflow/using/importing-data.md#best-practices-when-importing-data)和[导入模板示例](../../workflow/using/importing-data.md#setting-up-a-recurring-import)部分。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](../../platform/using/exporting-and-importing-profiles.md#import-profiles-video)

## 创建作业模板 {#creating-a-job-template}

Import and export templates are stored in the **[!UICONTROL Resources > Templates > Job templates]** directory of the Adobe Campaign tree.

默认情况下，此目录中存在三个导入模板和一个导出模板。不得更改它们。You can duplicate them to create your own templates or create a new template via the **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** menu.

![](assets/s_ncs_user_export_wizard_template_create.png)

创建流程模板的过程以导出向导和 [导入向导](../../platform/using/exporting-data.md#export-wizard)[形式](../../platform/using/importing-data.md#import-wizard)。

>[!NOTE]
>
>本机模 **[!UICONTROL Import denylist]** 板已配置为导入已添加到列表的电子邮件地址阻止列表。
> 
>通过 **[!UICONTROL New text import]** 和 **[!UICONTROL New text export]** 模板，您可以从头开始配置导入或导出。

## 创建新的导入/导出 {#creating-a-new-import-export}

配置模板后，可以在 Adobe Campaign 中的不同内容中启动导入和导出操作。

所有这些操作都会打开[导入](../../platform/using/importing-data.md)或[导出](../../platform/using/exporting-data.md#export-wizard)向导。

* In the **[!UICONTROL Profiles and targets]** section of Adobe Campaign workspace, click the **[!UICONTROL Jobs]** link: this takes you to the list of existing imports and exports.

   Click the **[!UICONTROL Create]** button and select the type of job you want to perform.

   ![](assets/s_ncs_user_import_from_home.png)

* 您还可以从工作区的“监督”部分启动导入和导出：可以通过两个专用链接直接启动导入或导出。

   ![](assets/s_ncs_user_import_from_production.png)

* 也可以从 Adobe Campaign Explorer 启动导入和导出。

   要导出／导入数据，请单 **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** 击节点，然 **[!UICONTROL New]** 后单击图标，并选 **[!UICONTROL Export]** 择或 **[!UICONTROL Import]**。 这将打开相应的向导。

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## 执行追踪 {#execution-tracking}

您可以在此编辑器的上半部分查看执行的追踪。您可以通过导入/导出作业列表关闭导出向导并查看作业的执行情况。

![](assets/s_ncs_user_export_list_and_details.png)

* The **[!UICONTROL Log]** tab lets you look at log messages concerning execution.
* The **[!UICONTROL Rejects]** tab contains the rejected records. See [Behavior in the event of an error](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>Import/export job statuses are presented in [Job statuses](../../platform/using/importing-data.md#job-statuses).

