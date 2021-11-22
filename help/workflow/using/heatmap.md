---
product: campaign
title: 营销活动工作流热图
description: 使用Workflow HeatMap监控您的工作流
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: f1016ddf-0c87-4611-a878-d01f3684935f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 3%

---

# 工作流热图 {#workflow-heatmap}

![](../../assets/common.svg)

Campaign Workflow HeatMap以颜色编码的图形形式表示当前运行的所有工作流。 它仅可用于 **Campaign管理员**.

了解在中监控Campaign流程的其他方法 [本页](../../production/using/monitoring-guidelines.md).

## 工作流热图入门 {#about-the-workflow-heatmap}

通过提供并发工作流数的快速概述，Workflow HeatMap使Adobe Campaign平台管理员能够监控实例的负载并相应地规划工作流。

更准确地说，它有助于平台管理员：

* 查看和了解并发工作流
* 按持续时间筛选工作流，以查看哪些工作流可能遇到问题
* 按持续时间筛选活动，以查看哪些活动可能遇到问题
* 轻松查找个别工作流和所有相关活动（及持续时间）
* 按工作流类型过滤： [技术工作流](building-a-workflow.md#technical-workflows) 或 [活动工作流](building-a-workflow.md#campaign-workflows)
* 查找要分析的特定工作流

>[!NOTE]
>
>除 **工作流热图**，则可以创建一个工作流，用于监视一组工作流的状态并向主管发送定期消息。 有关更多信息，请参阅 [专用部分](supervising-workflows.md).

使用工作流热图需要对以下概念有很好的了解： [工作流](about-workflows.md), [活动](about-activities.md) 和 [工作流最佳实践](workflow-best-practices.md).

## 自定义工作流热图 {#using-the-heatmap}

>[!NOTE]
>
>如果工作流热图中未显示任何数据，请单击 **[!UICONTROL Load data]** 按钮。

1. 转到 **[!UICONTROL Monitoring]** ，然后单击 **[!UICONTROL Workflow HeatMap]** 用于显示 **[!UICONTROL Campaign Workflow HeatMap]** 页面。

   ![](assets/wkf_monitoring_path.png)

1. 单击日历以选择日。

   默认情况下，页面会显示当天的工作流活动。 您可以更改它，并选择过去的任何日期。

   >[!NOTE]
   >
   >只有尚未被 **[!UICONTROL Database cleanup]** 工作流可见。 有关数据库清理工作流的详细信息，请参阅 [此部分](../../production/using/database-cleanup-workflow.md).\
   >默认情况下，工作流热图时区是为当前管理员用户定义的时区。 例如，如果您与正在处理的营销用户不在同一区域，则可能需要更改该区域。

1. 单击 **[!UICONTROL Filters]** 按钮。

   ![](assets/wkf_monitoring_filters.png)

1. 使用滑块将最短持续时间从0秒设置为1小时。 这样，您就可以仅搜索运行时间超过特定秒或分钟的工作流。

   ![](assets/wkf_monitoring_filters_duration.png)

1. 您还可以从 **[!UICONTROL Workflows]** 下拉列表。

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >的 **[!UICONTROL Min duration]** 过滤器。 如果找不到特定的工作流，请将最小持续时间重置为0，以便所有工作流都显示在列表中。

1. 您还可以在 **[!UICONTROL Workflow type]** :

   * **[!UICONTROL Technical]** :仅 [现成的技术工作流](building-a-workflow.md#technical-workflows) 和 [数据管理工作流](targeting-data.md#data-management) 中。
   * **[!UICONTROL Marketing]** :仅链接到营销活动(称为 [活动工作流](building-a-workflow.md#campaign-workflows)，则会显示。

1. 要按名称搜索特定工作流，您还可以使用 **[!UICONTROL Workflow name filter]** 字段。

1. 如果您在这两个工作流之间的时间中编辑了一些工作流，请单击 **[!UICONTROL Reload data]** 按钮来刷新网格中显示的数据。

## 解释工作流热图 {#reading-the-heatmap}

营销活动工作流热图是一个自然可读的网格，从左上角到右下角，允许查找具有绿色到红色编码范围的“热区”。

* 较深的红色单元格对应于同时运行大量工作流的时段。
* 灰色单元格对应于未运行工作流的时段。

要了解如何应用颜色代码以及如何导航热图，请单击 **[!UICONTROL Help]** 按钮。

![](assets/wkf_monitoring_legend.png)

每行代表一天的一小时，每个单元格代表该小时的5分钟。

网格会显示这些5分钟时段中每个时段同时运行的所有工作流。

在以下示例中，从上午8点到上午8:05点，运行了三个工作流（无论其各自的持续时间如何）：

![](assets/wkf_monitoring_ex_8am.png)

1. 单击彩色单元格以显示在此期间运行的所有并发工作流的详细信息。

   ![](assets/wkf_monitoring_details.png)

   对于每个工作流，都会列出其包含的所有活动及其持续时间。

1. 单击工作流ID或名称，以直接打开工作流。
1. 返回到 **[!UICONTROL Campaign Workflow HeatMap]** 视图，单击 **[!UICONTROL Home]** 按钮。

## 用例：使用热图执行操作 {#use-cases--using-the-heatmap-to-take-actions}

在以下两种主要情况下，营销活动工作流热图非常有用。

### 减少并发工作流的数量 {#reducing-the-number-of-concurrent-workflows}

作为Campaign管理员，Workflow HeatMap可以帮助您了解实例的负载情况，并在适当时规划现有或新的工作流。

1. 从 **[!UICONTROL Campaign Workflow HeatMap]** 视图，单击 **[!UICONTROL Filters]** 按钮。
1. 将持续时间设置为几秒或几分钟。
1. 通过增加持续时间过滤器来排除没有意义的最短工作流。

   ![](assets/wkf_monitoring_short_duration.png)

1. 浏览结果以了解实例的负载并采取适当的操作：

   * 如果您遇到性能问题，并且网格中显示了一个或多个红色单元格，请考虑更改多个工作流的开始时间。 要求营销用户将工作流从繁忙（“热”）时段手动移至更多可用时段。 这应该能够保持当天的活动稳定级别。
   * 要避免出现峰值并防止实例过载，请在规划新工作流之前查看HeatMap并选择最佳时间。 考虑网格中与灰色或绿色单元格对应的时隙，以启动新工作流。

### 查找影响性能的长时间运行的工作流 {#finding-long-running-workflows-that-impact-performance}

作为Campaign管理员，工作流热图可帮助您查找可能会减慢活动速度的最长工作流。

1. 从 **[!UICONTROL Campaign Workflow HeatMap]** 视图，单击 **[!UICONTROL Filters]** 按钮。
1. 将持续时间设置为1小时。

   ![](assets/wkf_monitoring_long_duration.png)

1. 通过降低 **[!UICONTROL Min duration]** 过滤器。
1. 浏览结果以查找最长的工作流，这些工作流可能对服务器和数据库资源（CPU、RAM、网络、IOPS等）产生更大的影响。
1. 采取适当的措施：

   * 建议营销用户拆分最长的工作流，以缩短处理时间。
   * 开始对特定工作流和特定活动（例如JavaScript、导入、导出等）进行更深入的分析，以隔离问题并更轻松地解决问题。

## 使用HeatMap改进工作流规划 {#example--using-the-heatmap-to-improve-workflow-planning}

以下示例显示了在使用Adobe Campaign Workflow HeatMap时，如何更高效地进行规划以及如何提高性能。

在这种情况下，许多用户都在抱怨工作流的性能。 您需要检查哪些因素会减慢活动速度以及如何解决问题。

1. 转到 **[!UICONTROL Monitoring]** ，然后单击 **[!UICONTROL Workflows]** 用于显示 **[!UICONTROL Campaign Workflow HeatMap]** 页面。
1. 设置 **[!UICONTROL Min duration]** 过滤到5分钟。
1. 设置 **[!UICONTROL Workflow type]** 筛选 **[!UICONTROL Marketing]** .
1. 从热图网格中，观察以下内容：

   ![](assets/wkf_monitoring_without.png)

   * 50个持久（超过5分钟）的营销活动工作流在上午10点运行。
   * 其中大多数具有待处理状态（默认情况下，并发限制设置为20）。
   * 需要每天手动重新启动挂起的工作流。
   * 性能很低。

1. 从上午10点开始，不再有50个工作流，而是在一天的其余时间平均分配工作流的开始时间。
1. 返回到 **[!UICONTROL Campaign Workflow HeatMap]** 页面，然后单击 **[!UICONTROL Reload data]** 按钮。
1. 现在，请注意以下事项：

   ![](assets/wkf_monitoring_with.png)

   * 上午10点，只有18个持久的营销活动工作流仍在运行。
   * 不再有工作流处于挂起状态（并发限制仍设置为20）。
   * 工作流开始时间会平均分布在一天中。
   * 不再有用户抱怨性能问题。
