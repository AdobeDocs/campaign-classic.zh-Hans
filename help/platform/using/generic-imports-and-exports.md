---
solution: Campaign Classic
product: campaign
title: 一般导入和导出
description: 一般导入和导出
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 55%

---


# 一般导入和导出{#generic-imports-and-exports}

Adobe Campaign 提供了一个数据导出模块，可以轻松提取客户或潜在客户清单（例如，在定位操作之后），然后他们将成为目标人群的一部分。

Adobe Campaign 还提供了一个导入模块，可让您使用外部文件为数据库提供数据。

>[!NOTE]
>
>导出和导入在通过&#x200B;**[!UICONTROL Import]**&#x200B;和&#x200B;**[!UICONTROL Export]**&#x200B;工作流执行的专用模板中进行配置。 它们可以根据时间表自动重复，例如用于在多个信息系统之间自动交换数据。如有必要，可以通过Adobe Campaign树的&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]**&#x200B;节点创建临时导入或导出。

您可以：

* 创建导入或导出模板并对其进行配置（参见下文）。
* 创建导入或导出：请参阅[导出数据](../../platform/using/exporting-data.md)或[导入数据](../../platform/using/importing-data.md)。
* 启动导入或导出并监视其执行。 请参阅[执行跟踪](#execution-tracking)。

>[!CAUTION]
>
>Campaign 中的数据导入应通过工作流程执行，以确保数据一致性并提高效率。有关详细信息，请参见[导入数据](../../workflow/using/importing-data.md)、[导入最佳实践](../../workflow/using/importing-data.md#best-practices-when-importing-data)和[导入模板示例](../../workflow/using/importing-data.md#setting-up-a-recurring-import)部分。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](../../platform/using/exporting-and-importing-profiles.md#import-profiles-video)

## 创建作业模板 {#creating-a-job-template}

导入和导出模板存储在Adobe Campaign树的&#x200B;**[!UICONTROL Resources > Templates > Job templates]**&#x200B;目录中。

默认情况下，此目录中存在三个导入模板和一个导出模板。不得更改它们。您可以重复他们创建自己的模板，或通过&#x200B;**[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**&#x200B;菜单创建新模板。

![](assets/s_ncs_user_export_wizard_template_create.png)

创建过程模板的过程在[导出向导](../../platform/using/exporting-data.md#export-wizard)和[导入向导](../../platform/using/importing-data.md#import-wizard)中介绍。

>[!NOTE]
>
>本机模板&#x200B;**[!UICONTROL Import denylist]**&#x200B;已配置为导入已添加到该列表的电子邮件地阻止列表址。
> 
>使用&#x200B;**[!UICONTROL New text import]**&#x200B;和&#x200B;**[!UICONTROL New text export]**&#x200B;模板，可以从头开始配置导入或导出。

## 创建新的导入/导出 {#creating-a-new-import-export}

配置模板后，可以在 Adobe Campaign 中的不同内容中启动导入和导出操作。

所有这些操作都会打开[导入](../../platform/using/importing-data.md)或[导出](../../platform/using/exporting-data.md#export-wizard)向导。

* 在Adobe Campaign工作区的&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;部分，单击&#x200B;**[!UICONTROL Jobs]**&#x200B;链接：这将带您列表现有进出口。

   单击&#x200B;**[!UICONTROL Create]**&#x200B;按钮并选择要执行的作业类型。

   ![](assets/s_ncs_user_import_from_home.png)

* 您还可以从工作区的“监督”部分启动导入和导出：可以通过两个专用链接直接启动导入或导出。

   ![](assets/s_ncs_user_import_from_production.png)

* 也可以从 Adobe Campaign Explorer 启动导入和导出。

   要导出／导入数据，请单击&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]**&#x200B;节点，然后单击&#x200B;**[!UICONTROL New]**&#x200B;图标，然后选择&#x200B;**[!UICONTROL Export]**&#x200B;或&#x200B;**[!UICONTROL Import]**。 这将打开相应的向导。

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## 执行追踪 {#execution-tracking}

您可以在此编辑器的上半部分查看执行的追踪。您可以通过导入/导出作业列表关闭导出向导并查看作业的执行情况。

![](assets/s_ncs_user_export_list_and_details.png)

* 使用&#x200B;**[!UICONTROL Log]**&#x200B;选项卡可以查看有关执行的日志消息。
* **[!UICONTROL Rejects]**&#x200B;选项卡包含被拒绝的记录。 请参阅错误](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error)事件中的[行为。

>[!NOTE]
>
>导入／导出作业状态以[作业状态](../../platform/using/importing-data.md#job-statuses)显示。

