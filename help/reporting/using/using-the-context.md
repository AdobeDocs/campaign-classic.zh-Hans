---
solution: Campaign Classic
product: campaign
title: 使用上下文
description: 使用上下文
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 3%

---


# 使用上下文{#using-the-context}

当您希望以&#x200B;**[!UICONTROL tables]**&#x200B;或&#x200B;**[!UICONTROL charts]**&#x200B;的形式表示数据时，可以从以下两个来源获取数据：新查询（请参阅[定义数据](#defining-a-direct-filter-on-data)的直接过滤器）或报表上下文（请参阅[使用上下文数据](#using-context-data)）。

## 定义数据{#defining-a-direct-filter-on-data}的直接过滤器

### 筛选数据 {#filtering-data}

构建报告时，不必使用&#x200B;**[!UICONTROL Query]**&#x200B;类型活动。 数据可以直接在构成报告的表和图表中过滤。

这使您能够通过报表的&#x200B;**[!UICONTROL Page]**&#x200B;活动直接选择要在报表中显示的数据。

为此，请单击&#x200B;**[!UICONTROL Data]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Filter data...]**&#x200B;链接：此链接允许您访问表达式编辑器，以定义要分析的查询。

![](assets/reporting_filter_data_from_page.png)

### 示例：在图表{#example--use-a-filter-in-a-chart}中使用过滤器

在以下示例中，我们希望图表仅显示居住在法国的收件人用户档案以及年内购买的客户。

要定义此过滤器，请将页面放在图表中并进行编辑。 单击&#x200B;**[!UICONTROL Filter data]**&#x200B;链接并创建与要显示的数据匹配的筛选器。 有关在Adobe Campaign中构建查询的详细信息，请参阅[此部分](../../platform/using/about-queries-in-campaign.md)。

![](assets/s_ncs_advuser_report_wizard_029.png)

在此，我们要按选定收件人的城市显示细分。

![](assets/reporting_graph_with_2vars.png)

渲染将如下所示：

![](assets/reporting_graph_with_2vars_preview.png)

### 示例：在透视表{#example--use-a-filter-in-a-pivot-table}中使用过滤器

在此示例中，过滤器允许您在枢纽表中仅显示非巴黎客户，而无需事先使用其他查询。

应用以下步骤：

1. 将页面放在图表中并进行编辑。
1. 创建透视表。
1. 转至&#x200B;**[!UICONTROL Data]**&#x200B;选项卡并选择要使用的多维数据集。
1. 单击&#x200B;**[!UICONTROL Filter data...]**&#x200B;链接并定义以下查询，以从公司列表中删除Adobe。

   ![](assets/s_ncs_advuser_report_display_03.png)

报告中只显示符合筛选条件的收件人。

![](assets/s_ncs_advuser_report_display_04.png)

## 使用上下文数据{#using-context-data}

要以&#x200B;**[!UICONTROL table]**&#x200B;或&#x200B;**[!UICONTROL chart]**&#x200B;的形式表示数据，数据可以来自报告上下文。

在包含表或图表的页面中，**[!UICONTROL Data]**&#x200B;选项卡允许您选择数据源。

![](assets/s_ncs_advuser_report_datasource_3.png)

* 使用&#x200B;**[!UICONTROL New query]**&#x200B;选项可以构建查询来收集数据。 有关详细信息，请参阅[定义数据的直接过滤器](#defining-a-direct-filter-on-data)。
* 使用&#x200B;**[!UICONTROL Context data]**&#x200B;选项可以使用输入数据：报表的上下文与包含图表或表的页面的入站过渡中包含的信息一致。 例如，此上下文可能包含通过放置在&#x200B;**[!UICONTROL Page]**&#x200B;活动之前的&#x200B;**[!UICONTROL Query]**&#x200B;活动收集的数据，您需要为其指定报表所关注的表和字段。

例如，在查询框中，为收件人构建以下查询:

![](assets/s_ncs_advuser_report_datasource_2.png)

然后在报告中指明数据的来源，在这种情况下：**[!UICONTROL Data from the context]**。

数据位置会自动推断。 如有必要，您可以强制使用数据路径。

![](assets/s_ncs_advuser_report_datasource_4.png)

当您选择统计信息将涉及的数据时，可用字段与查询中指定的数据一致。

![](assets/s_ncs_advuser_report_datasource_1.png)

