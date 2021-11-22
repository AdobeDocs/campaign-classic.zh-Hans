---
product: campaign
title: 使用上下文
description: 使用上下文
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 3%

---

# 使用上下文{#using-the-context}

![](../../assets/common.svg)

当您想要以 **[!UICONTROL tables]** 或 **[!UICONTROL charts]**，可从两个来源获取：新查询(请参阅 [定义数据的直接过滤器](#defining-a-direct-filter-on-data))或报表上下文(请参阅 [使用上下文数据](#using-context-data))。

## 定义数据的直接过滤器 {#defining-a-direct-filter-on-data}

### 筛选数据 {#filtering-data}

使用 **[!UICONTROL Query]** 构建报表时，类型活动不是强制的。 数据可直接在构成报表的表格和图表中过滤。

这样，您就可以直接通过 **[!UICONTROL Page]** 活动。

为此，请单击 **[!UICONTROL Filter data...]** 链接 **[!UICONTROL Data]** 选项卡：利用此链接，可访问表达式编辑器以定义有关要分析数据的查询。

![](assets/reporting_filter_data_from_page.png)

### 示例：在图表中使用过滤器 {#example--use-a-filter-in-a-chart}

在以下示例中，我们希望图表仅显示在法国居住的收件人用户档案以及当年购买过的收件人用户档案。

要定义此过滤器，请将页面放入图表中并对其进行编辑。 单击 **[!UICONTROL Filter data]** 链接，并创建与要显示的数据匹配的过滤器。 有关在Adobe Campaign中构建查询的更多信息，请参阅 [此部分](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

在此，我们要按选定收件人所在城市显示划分结果。

![](assets/reporting_graph_with_2vars.png)

呈现将如下所示：

![](assets/reporting_graph_with_2vars_preview.png)

### 示例：在数据透视表中使用过滤器 {#example--use-a-filter-in-a-pivot-table}

在此示例中，过滤器允许您在数据透视表中仅显示非巴黎客户，而无需事先使用其他查询。

应用以下步骤：

1. 将页面放入图表中并对其进行编辑。
1. 创建数据透视表。
1. 转到 **[!UICONTROL Data]** 选项卡，然后选择要使用的多维数据集。
1. 单击 **[!UICONTROL Filter data...]** 链接并定义以下查询，以从公司列表中删除Adobe。

   ![](assets/s_ncs_advuser_report_display_03.png)

只有符合筛选条件的收件人才会显示在报表中。

![](assets/s_ncs_advuser_report_display_04.png)

## 使用上下文数据 {#using-context-data}

以 **[!UICONTROL table]** 或 **[!UICONTROL chart]**，则数据可以来自报表上下文。

在包含表或图表的页面中， **[!UICONTROL Data]** 选项卡来选择数据源。

![](assets/s_ncs_advuser_report_datasource_3.png)

* 的 **[!UICONTROL New query]** 选项允许您构建查询以收集数据。 有关更多信息，请参阅 [定义数据的直接过滤器](#defining-a-direct-filter-on-data).
* 的 **[!UICONTROL Context data]** 选项允许您使用输入数据：报表上下文与包含图表或表的页面集客过渡中包含的信息一致。 例如，此上下文可以包含通过 **[!UICONTROL Query]** 活动放在 **[!UICONTROL Page]** 活动，您需要为其指定报表所关注的表和字段。

例如，在查询框中，为收件人构建以下查询：

![](assets/s_ncs_advuser_report_datasource_2.png)

然后，在此示例中指示报表中的数据源： **[!UICONTROL Data from the context]**.

数据位置会自动推断。 如有必要，您可以强制使用数据路径。

![](assets/s_ncs_advuser_report_datasource_4.png)

当您选择统计信息将涉及的数据时，可用字段与查询中指定的数据一致。

![](assets/s_ncs_advuser_report_datasource_1.png)
