---
solution: Campaign Classic
product: campaign
title: 活动工作流热图
description: 使用Workflow HeatMap监控工作流
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: f1016ddf-0c87-4611-a878-d01f3684935f
source-git-commit: e6969a3ed61bde692b2f72b3711f12ce46a0025f
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 3%

---

# 工作流热图 {#workflow-heatmap}

活动工作流热图包含当前运行的所有工作流的颜色编码图形表示。 它仅对&#x200B;**活动管理员**&#x200B;可用。

在[本页](../../production/using/monitoring-guidelines.md)中探索监视活动进程的其他方法。

## 开始使用Workflow HeatMap {#about-the-workflow-heatmap}

通过提供并发工作流数的快速概述，Workflow HeatMap使Adobe Campaign平台管理员能够相应地监视实例负载和计划工作流。

更准确地说，它有助于平台管理员：

* 查看和了解并发工作流
* 按持续时间筛选工作流，以查看哪些工作流可能遇到问题
* 按持续时间筛选活动，以查看哪些活动可能遇到问题
* 轻松查找个别工作流和所有相关活动（及持续时间）
* 按工作流类型过滤：[技术工作流](../../workflow/using/building-a-workflow.md#technical-workflows)或[活动工作流](../../workflow/using/building-a-workflow.md#campaign-workflows)
* 查找要分析的特定工作流

>[!NOTE]
>
>除了&#x200B;**工作流热图**&#x200B;之外，您还可以创建一个工作流，通过它可以监视一组工作流的状态并向主管发送循环消息。 有关详细信息，请参阅[专用部分](../../workflow/using/supervising-workflows.md)。

使用Workflow HeatMap需要充分了解以下概念：[工作流](../../workflow/using/about-workflows.md)、[活动](../../workflow/using/about-activities.md)和[工作流最佳实践](../../workflow/using/workflow-best-practices.md)。

## 自定义工作流热图{#using-the-heatmap}

>[!NOTE]
>
>如果Workflow HeatMap中未显示任何数据，请单击&#x200B;**[!UICONTROL Load data]**&#x200B;按钮。

1. 转到&#x200B;**[!UICONTROL Monitoring]**&#x200B;并单击&#x200B;**[!UICONTROL Workflow HeatMap]**&#x200B;链接以显示&#x200B;**[!UICONTROL Campaign Workflow HeatMap]**&#x200B;页。

   ![](assets/wkf_monitoring_path.png)

1. 单击日历以选择日。

   默认情况下，该页面显示当天的工作流活动。 您可以更改它，并选择过去的任何日期。

   >[!NOTE]
   >
   >只有尚未被&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流删除的工作流才可见。 有关数据库清理工作流的详细信息，请参阅[此部分](../../production/using/database-cleanup-workflow.md)。\
   >默认情况下，工作流热图时区是为当前管理员用户定义的时区。 例如，如果您与正在处理的营销用户不在同一区域，则您可能希望对其进行更改。

1. 单击 **[!UICONTROL Filters]** 按钮。

   ![](assets/wkf_monitoring_filters.png)

1. 使用滑块将最短持续时间从0秒设置为1小时。 这样，您只能搜索运行时间超过特定秒或分钟的工作流。

   ![](assets/wkf_monitoring_filters_duration.png)

1. 您还可以从&#x200B;**[!UICONTROL Workflows]**&#x200B;下拉列表中选择特定工作流。

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >应用&#x200B;**[!UICONTROL Min duration]**&#x200B;滤镜。 如果找不到特定的工作流，请将最小持续时间重置为0，以便所有工作流都显示在列表中。

1. 您还可以在&#x200B;**[!UICONTROL Workflow type]**&#x200B;上进行筛选：

   * **[!UICONTROL Technical]** :只 [显示现成的技术工](../../workflow/using/building-a-workflow.md#technical-workflows) 作流 [和](../../workflow/using/targeting-data.md#data-management) 数据管理工作流。
   * **[!UICONTROL Marketing]** :仅显示链接到营销活动(称为工作流) [的活动工作流](../../workflow/using/building-a-workflow.md#campaign-workflows)。

1. 要按名称搜索特定工作流，您还可以使用&#x200B;**[!UICONTROL Workflow name filter]**&#x200B;字段。

1. 如果您在中间时间编辑了一些工作流，请单击&#x200B;**[!UICONTROL Reload data]**&#x200B;按钮刷新网格中显示的数据。

## 解释工作流热图{#reading-the-heatmap}

活动 Workflow HeatMap是一个自然可读的网格，从左上角到右下角，它允许查找具有绿色到红色编码范围的“热点区域”。

* 较暗的红色单元格对应于同时运行大量工作流的时段。
* 灰色单元格与未运行工作流的期间相对应。

要了解如何应用颜色代码以及如何导航热图，请单击&#x200B;**[!UICONTROL Help]**&#x200B;按钮。

![](assets/wkf_monitoring_legend.png)

每行代表一天的一小时，每个单元格代表该小时的5分钟。

网格显示这些5分钟时段中每个时段同时运行的所有工作流。

在以下示例中，在上午8点到上午8点05分之间，有三个工作流正在运行（无论其单独的持续时间如何）：

![](assets/wkf_monitoring_ex_8am.png)

1. 单击一个彩色单元格，以显示在此期间运行的所有并发工作流的详细信息。

   ![](assets/wkf_monitoring_details.png)

   对于每个工作流，将列出它包含的所有活动及其持续时间。

1. 单击工作流ID或名称以直接打开工作流。
1. 要返回&#x200B;**[!UICONTROL Campaign Workflow HeatMap]**&#x200B;视图，请单击&#x200B;**[!UICONTROL Home]**&#x200B;按钮。

## 用例：使用HeatMap执行{#use-cases--using-the-heatmap-to-take-actions}操作

有两种主要情况，活动工作流热图可以很有用。

### 减少并发工作流数{#reducing-the-number-of-concurrent-workflows}

作为活动管理员，Workflow HeatMap可以帮助您了解实例的负载并在适当的时间规划现有或新工作流。

1. 在&#x200B;**[!UICONTROL Campaign Workflow HeatMap]**&#x200B;视图中，单击&#x200B;**[!UICONTROL Filters]**&#x200B;按钮。
1. 将持续时间设置为几秒钟或几分钟。
1. 通过增加持续时间过滤器来排除不显着的最短工作流。

   ![](assets/wkf_monitoring_short_duration.png)

1. 浏览结果，了解实例的负载并采取相应操作：

   * 如果您遇到性能问题，并且网格中显示了一个或多个红色单元格，请考虑更改多个工作流的开始时间。 要求营销用户手动将工作流从忙（“热”）时段移动到更多可用时段。 这应该能够保持稳定的活动水平。
   * 要避免出现峰值并防止实例过载，请在规划新工作流之前查看HeatMap并选择最佳时间。 考虑网格中与灰色或绿色单元格对应的时隙，以开始新工作流。

### 查找影响性能{#finding-long-running-workflows-that-impact-performance}的长期工作流

作为活动管理员，Workflow HeatMap可帮助您找到最长的工作流，从而降低活动速度。

1. 在&#x200B;**[!UICONTROL Campaign Workflow HeatMap]**&#x200B;视图中，单击&#x200B;**[!UICONTROL Filters]**&#x200B;按钮。
1. 将持续时间设置为1小时。

   ![](assets/wkf_monitoring_long_duration.png)

1. 通过减少&#x200B;**[!UICONTROL Min duration]**&#x200B;滤镜来增加效果。
1. 浏览结果，找到最长的工作流，这些数据可能对服务器和数据库资源（CPU、RAM、网络、IOPS等）产生更大的影响。
1. 采取适当的操作：

   * 建议营销用户拆分最长的工作流，以缩短处理时间。
   * 开始对特定工作流和特定活动（如JavaScript、导入、导出等）进行更深入的分析，以隔离问题并更轻松地解决它们。

## 使用HeatMap改进工作流规划{#example--using-the-heatmap-to-improve-workflow-planning}

以下示例显示了在使用Adobe Campaign Workflow HeatMap时如何提高规划效率以及如何改进性能。

在这种情况下，许多用户都在抱怨工作流的性能。 您需要检查是什么降低了活动速度以及如何解决问题。

1. 转到&#x200B;**[!UICONTROL Monitoring]**&#x200B;并单击&#x200B;**[!UICONTROL Workflows]**&#x200B;链接以显示&#x200B;**[!UICONTROL Campaign Workflow HeatMap]**&#x200B;页。
1. 将&#x200B;**[!UICONTROL Min duration]**&#x200B;过滤器设置为5分钟。
1. 将&#x200B;**[!UICONTROL Workflow type]**&#x200B;过滤器设置为&#x200B;**[!UICONTROL Marketing]**。
1. 从热图网格中，观察以下情况：

   ![](assets/wkf_monitoring_without.png)

   * 50个长时间（超过5分钟）活动工作流在上午10点开始运行。
   * 大多数都处于挂起状态（默认情况下，并发限制设置为20）。
   * 需要每天手动重新启动挂起的工作流。
   * 性能低。

1. 不是让50个工作流从上午10点开始，而是在一天的其余时间平均分配工作流的开始时间。
1. 返回至&#x200B;**[!UICONTROL Campaign Workflow HeatMap]**&#x200B;页面并单击&#x200B;**[!UICONTROL Reload data]**&#x200B;按钮。
1. 现在，请注意以下事项：

   ![](assets/wkf_monitoring_with.png)

   * 上午10点，仍只有18名持久活动工作流在进行。
   * 没有更多工作流处于挂起状态（并发限制仍设置为20）。
   * 工作流开始时间在一天中平均分配。
   * 不再有用户抱怨性能问题。
