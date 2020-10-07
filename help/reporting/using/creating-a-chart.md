---
title: 创建图表
seo-title: 创建图表
description: 创建图表
seo-description: null
page-status-flag: never-activated
uuid: 516ec707-207e-4320-8d70-fd410425bd4b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 70e4e63d-354d-4912-b75a-dba38e1c0b03
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 3%

---


# 创建图表{#creating-a-chart}

还可以收集数据库中的数据并在图表中显示。 Adobe Campaign提供一组图形表示。 其配置详见下文。

图表通过右键单击菜单或工具栏直接插入到报表页面。

## 创建步骤 {#creation-steps}

要在报表中创建图表，请应用以下步骤：

1. 编辑要显示图表的页面，并在工具栏上选择图表类型。

   ![](assets/s_advuser_report_page_activity_04.png)

1. 输入名称和题注。 如有必要，您可以使用下拉列表更改题注的位置。

   ![](assets/s_ncs_advuser_report_wizard_018.png)

1. 单击选 **[!UICONTROL Data]** 项卡以定义数据源和要计算的系列。

   要在图表中显示的统计信息可以基于查询或上下文数据(即当前页面的入站过渡提供的数据)来计算(有关详细信息，请参阅使 [用上下文数据](../../reporting/using/using-the-context.md#using-context-data))。

   * 单击链 **[!UICONTROL Filter data...]** 接以定义数据库中数据的筛选条件。

      ![](assets/reporting_graph_add_filter.png)

   * 要使用上下文数据，请选择此选项并单击 **[!UICONTROL Advanced settings...]** 链接。 然后选择统计数据所关注的数据。

      ![](assets/reporting_graph_from_context.png)

      然后，您将能够访问上下文数据以定义要在图表中显示的值：

      ![](assets/reporting_graph_select-from_context.png)

## 图表类型和变体 {#chart-types-and-variants}

Adobe Campaign优惠各种类型的图形表示。 详见下文。

将图表类型插入页面时，将选择该图表类型。

![](assets/s_advuser_report_page_activity_04.png)

也可以通过图表中 **[!UICONTROL Chart type]** 选项卡的 **[!UICONTROL General]** 部分更改它。

![](assets/reporting_change_graph_type.png)

变体取决于所选的图表类型。 它们通过链接进 **[!UICONTROL Variants...]** 行选择。

### 细分：饼图 {#breakdown--pie-charts}

通过这种图形表示形式，可显示测量元素的概述。

饼图仅允许您分析一个变量。

![](assets/reporting_graph_type_sector_1.png)

该链 **[!UICONTROL Variants]** 接可让您个性化图表的整体呈现。

![](assets/reporting_graph_type_sector_2.png)

饼图允许您在相应的字段中输入内半径值。

例如：

0.00跟踪整个圆圈。

![](assets/s_ncs_advuser_report_sector_exple1.png)

0.40跟踪半径为40%的圆。

![](assets/s_ncs_advuser_report_sector_exple2.png)

1.00仅跟踪圆的外部。

![](assets/s_ncs_advuser_report_sector_exple3.png)

### 演变：曲线和区域 {#evolution--curves-and-areas}

通过这种图形表示形式，您可以及时了解一个或多个度量的演变。

![](assets/reporting_graph_type_curve.png)

### 比较：直方图 {#comparison--histograms}

直方图允许您比较一个或多个变量的值。

对于这些类型的图表，窗口中提供以下选 **[!UICONTROL Variants]** 项：

![](assets/reporting_select_graph_var.png)

选中选 **[!UICONTROL Display caption]** 项以显示图表中的题注并选择其位置：

![](assets/reporting_select_graph_legend.png)

在适当时，您可以将值堆叠在一起。

![](assets/reporting_graph_type_histo.png)

如有必要，您可以颠倒值显示顺序。 To do this, select the **[!UICONTROL Reverse stacking]** option.

### 转换：漏斗 {#conversion--funnel}

通过这种图表可以跟踪测量元素的对话率。

### 进度：仪表 {#progress--gauge}

此类型的图表允许您显示与定义的目标相比值的进度。 在以下示例中，黑色拨号显示成功发送(76)的投放数，该数量超出100个投放的目标。 该仪表分为三个范围，这些范围与特定状态相对应。

![](assets/reporting_graph_type_gauge.png)

配置图表时会定义这些元素。

![](assets/reporting_graph_type_gauge1.png)

* 该 **[!UICONTROL Value]** 字段由图表中的黑色拨号表示。 它表示要计算其进度的元素。 必须已保存要表示的值才能使用。
* 字 **[!UICONTROL Goal]** 段表示要达到的最大值。
* 使用字 **[!UICONTROL Other mark]** 段，您可以向图表添加第二个指示符。
* 字 **[!UICONTROL Display range]** 段允许您指定计算报表的值。
* 该字 **[!UICONTROL Value ranges]** 段允许您将状态（无、坏、可接受、好）归为一组值，以更好地说明进度。

在部 **[!UICONTROL Display settings]** 分中， **[!UICONTROL Change appearance...]** 您可以配置图表的显示方式。

![](assets/reporting_graph_type_gauge2.png)

通过 **[!UICONTROL Display the value below the gauge]** 此选项，可在图表下方显示值进度。

该 **[!UICONTROL Aperture ratio]** 字段必须介于0和1之间，它允许您以或多或少完整的圆形编辑报表的光圈。 在上面的示例中，值0.50对应一个半圆。

该字 **[!UICONTROL Width]** 段允许您编辑图表大小。

## 与图表交互 {#interaction-with-the-chart}

用户单击图表时，您可以定义操作。 打开窗 **[!UICONTROL Interaction events]** 口并选择要执行的操作。

本节详细介绍了可能的交互类型 [及其配置](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

![](assets/s_ncs_advuser_report_wizard_017.png)

## 计算统计 {#calculating-statistics}

通过图表可显示有关所收集数据的统计信息。

这些统计信息是通过选 **[!UICONTROL Series parameters]** 项卡的部分定 **[!UICONTROL Data]** 义的。

要创建新统计信息，请单击图 **[!UICONTROL Add]** 标并配置相应的窗口。 可用的计算类型详见下文。

![](assets/reporting_add_statistics.png)

如需详细信息，请参阅[此部分](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation)。
