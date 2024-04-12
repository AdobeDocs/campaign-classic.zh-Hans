---
product: campaign
title: 在报表中使用上下文
description: 了解如何在报告中使用上下文
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Reporting, Monitoring
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# 在报表中使用上下文{#using-the-context}



当您想要以下列形式表示数据时 **[!UICONTROL tables]** 或 **[!UICONTROL charts]**，它可以从两个源获取：新查询(请参阅 [定义数据的直接过滤器](#defining-a-direct-filter-on-data))或报表上下文(请参阅 [使用上下文数据](#using-context-data))。

## 定义数据的直接过滤器 {#defining-a-direct-filter-on-data}

### 筛选数据 {#filtering-data}

使用 **[!UICONTROL Query]** 构建报表时，类型活动不是必需的。 可直接在构成报告的表格和图表中过滤数据。

这使您能够通过直接选择要在报表中显示的数据 **[!UICONTROL Page]** 报告的活动。

要执行此操作，请单击 **[!UICONTROL Filter data...]** 中的链接 **[!UICONTROL Data]** 选项卡：利用此链接，可访问表达式编辑器以定义对要分析的数据的查询。

![](assets/reporting_filter_data_from_page.png)

### 示例：在图表中使用过滤器 {#example--use-a-filter-in-a-chart}

在以下示例中，我们希望图表仅显示生活在法国以及年内购买产品的收件人用户档案。

要定义此筛选器，请将页面放入图表并对其进行编辑。 单击 **[!UICONTROL Filter data]** 链接并创建与要显示的数据匹配的过滤器。 有关在Adobe Campaign中构建查询的更多信息，请参阅 [本节](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

在这里，我们要按城市显示选定收件人的细分。

![](assets/reporting_graph_with_2vars.png)

渲染将如下所示：

![](assets/reporting_graph_with_2vars_preview.png)

### 示例：在透视表中使用筛选器 {#example--use-a-filter-in-a-pivot-table}

在本例中，使用筛选器可在数据透视表中只显示非巴黎客户，而无需预先使用其他查询。

应用以下步骤：

1. 将页面放入图表中并进行编辑。
1. 创建数据透视表。
1. 转到 **[!UICONTROL Data]** 选项卡，并选择要使用的多维数据集。
1. 单击 **[!UICONTROL Filter data...]** 链接并定义以下查询，以从公司列表中删除Adobe。

   ![](assets/s_ncs_advuser_report_display_03.png)

只有符合筛选条件的收件人才会出现在报告中。

![](assets/s_ncs_advuser_report_display_04.png)

## 使用上下文数据 {#using-context-data}

以a的形式表示数据 **[!UICONTROL table]** 或 **[!UICONTROL chart]**，则数据可能来自报表上下文。

在包含表或图表的页中， **[!UICONTROL Data]** 选项卡允许您选择数据源。

![](assets/s_ncs_advuser_report_datasource_3.png)

* 此 **[!UICONTROL New query]** 选项允许您构建查询以收集数据。 有关详细信息，请参见 [定义数据的直接过滤器](#defining-a-direct-filter-on-data).
* 此 **[!UICONTROL Context data]** 选项允许您使用输入数据：报表的上下文与包含图表或表的页面的集客过渡中包含的信息一致。 例如，此上下文可能包含通过 **[!UICONTROL Query]** 放在之前的活动 **[!UICONTROL Page]** 活动，您需要指定报告涉及的表和字段。

例如，在查询框中，为收件人生成以下查询：

![](assets/s_ncs_advuser_report_datasource_2.png)

然后，在您的报表中指明数据的来源，在本例中为： **[!UICONTROL Data from the context]**.

数据位置会自动推断。 如有必要，您可以强制使用数据路径。

![](assets/s_ncs_advuser_report_datasource_4.png)

当您选择统计信息将涉及的数据时，可用字段与在查询中指定的数据一致。

![](assets/s_ncs_advuser_report_datasource_1.png)
