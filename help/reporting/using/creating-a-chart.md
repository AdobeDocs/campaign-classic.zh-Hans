---
product: campaign
title: 创建图表
description: 创建图表
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: d32b614f-82c1-4363-816c-4ebedaa5cfe9
source-git-commit: 7fa8cea04fb4e25187c48ad19330815e9b522b37
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 3%

---

# 创建图表{#creating-a-chart}

![](../../assets/common.svg)

数据库中的数据也可以在图表中收集和显示。 Adobe Campaign提供一组图形表示。 其配置详见下文。

通过右键单击菜单或工具栏将图表直接插入报表页面。

## 创建步骤 {#creation-steps}

要在报表中创建图表，请应用以下步骤：

1. 编辑要在其中显示图表的页面，然后在工具栏中选择图表类型。

   ![](assets/s_advuser_report_page_activity_04.png)

1. 输入名称和标题。 如有必要，您可以使用下拉列表更改标题的位置。

   ![](assets/s_ncs_advuser_report_wizard_018.png)

1. 单击&#x200B;**[!UICONTROL Data]**&#x200B;选项卡以定义要计算的数据源和系列。

   要在图表中显示的统计信息可以基于查询或上下文数据计算，即由当前页面的集客过渡提供的数据（有关更多信息，请参阅[使用上下文数据](../../reporting/using/using-the-context.md#using-context-data)）。

   * 单击&#x200B;**[!UICONTROL Filter data...]**&#x200B;链接，为数据库中的数据定义筛选条件。

      ![](assets/reporting_graph_add_filter.png)

   * 要使用上下文数据，请从&#x200B;**[!UICONTROL Source]**&#x200B;下拉菜单中选择&#x200B;**[!UICONTROL Context data]**，然后单击&#x200B;**[!UICONTROL Advanced settings...]**&#x200B;链接。 然后，选择统计信息将涉及的数据。

      ![](assets/reporting_graph_from_context.png)

      然后，您将能够访问上下文数据以定义要在图表中显示的值：

      ![](assets/reporting_graph_select-from_context.png)

## 图表类型和变体 {#chart-types-and-variants}

Adobe Campaign提供各种类型的图形表示形式。 下文详述了这些规则。

将图表类型插入到页面中时，将选择该图表类型。

![](assets/s_advuser_report_page_activity_04.png)

也可以通过图表中&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL Chart type]**&#x200B;部分更改。

![](assets/reporting_change_graph_type.png)

变体取决于所选的图表类型。 它们通过&#x200B;**[!UICONTROL Variants...]**&#x200B;链接进行选择。

### 划分：饼图 {#breakdown--pie-charts}

此类型的图形表示允许您显示测量元素的概述。

饼图仅允许您分析一个变量。

![](assets/reporting_graph_type_sector_1.png)

**[!UICONTROL Variants]**&#x200B;链接允许您个性化图表的整体呈现。

![](assets/reporting_graph_type_sector_2.png)

饼图允许您在相应的字段中输入内半径的值。

例如：

0.00跟踪整个圆。

![](assets/s_ncs_advuser_report_sector_exple1.png)

0.40跟踪半径为40%的圆。

![](assets/s_ncs_advuser_report_sector_exple2.png)

1.00仅跟踪圆圈外部。

![](assets/s_ncs_advuser_report_sector_exple3.png)

### 进化：曲线和区域 {#evolution--curves-and-areas}

此类型的图形表示可让您及时了解一个或多个测量的演变。

![](assets/reporting_graph_type_curve.png)

### 比较：直方图 {#comparison--histograms}

直方图允许您比较一个或多个变量的值。

对于这些类型的图表，**[!UICONTROL Variants]**&#x200B;窗口中提供了以下选项：

![](assets/reporting_select_graph_var.png)

选中&#x200B;**[!UICONTROL Display caption]**&#x200B;选项以显示图表标题并选择其位置：

![](assets/reporting_select_graph_legend.png)

在适当时，您可以将值堆叠在一起。

![](assets/reporting_graph_type_histo.png)

如有必要，您可以反转值显示序列。 要执行此操作，请选择&#x200B;**[!UICONTROL Reverse stacking]**&#x200B;选项。

### 转化：漏斗 {#conversion--funnel}

此类型的图表允许您跟踪测量元素的对话率。

## 与图表交互 {#interaction-with-the-chart}

您可以定义用户单击图表时的操作。 打开&#x200B;**[!UICONTROL Interaction events]**&#x200B;窗口，然后选择要执行的操作。

[此部分](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)中详细描述了可能的交互类型及其配置。

![](assets/s_ncs_advuser_report_wizard_017.png)

## 计算统计信息 {#calculating-statistics}

通过图表可显示有关收集数据的统计信息。

这些统计信息通过&#x200B;**[!UICONTROL Data]**&#x200B;选项卡的&#x200B;**[!UICONTROL Series parameters]**&#x200B;部分定义。

要创建新统计信息，请单击&#x200B;**[!UICONTROL Add]**&#x200B;图标并配置相应的窗口。 可用的计算类型详见下文。

![](assets/reporting_add_statistics.png)

如需详细信息，请参阅[此部分](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation)。
