---
product: campaign
title: 元素布局
description: 元素布局
feature: Reporting
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 1%

---

# 元素布局{#element-layout}

![](../../assets/common.svg)

除了详细描述的各种图表外 [此处](../../reporting/using/creating-a-chart.md#chart-types-and-variants)，您可以调整显示内容并向报表页面添加元素。

您可以使用容器：这些选项允许您链接页面的多个元素，并在列和/或单元格中配置其布局。 有关如何使用这些源代码的详情，请参阅 [此部分](../../web/using/defining-web-forms-layout.md#creating-containers).

您可以在树的根位置配置报表布局，并为每个容器过载报表布局。 页面按列进行排序。 容器也按列进行排序。 只有静态项目和图形项目会按单元格进行排序。

## 为每个页面定义选项 {#defining-the-options-for-each-page}

您可以使用报表每个页面上的选项。

的 **[!UICONTROL General]** 选项卡，可更改页面标题，以及配置图例位置和在报表页面之间浏览。

![](assets/s_ncs_advuser_report_wizard_022.png)

的 **[!UICONTROL Title]** 字段，可将报表页面标题中的标签个性化。 窗口的标题可以通过 **[!UICONTROL Properties]** 窗口。 有关更多信息，请参阅 [添加页眉和页脚](#adding-a-header-and-a-footer).

的 **[!UICONTROL Display settings]** 选项允许您选择报表页面中控件标题的位置并定义页面上的列数。 有关页面布局的更多信息，请参阅 **项目布局** 部分 [此部分](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

在 **[!UICONTROL Browse]** 部分来授权从一个报表页面浏览到另一个报表页面。 如果 **[!UICONTROL Disable next page]** 或 **[!UICONTROL Disable previous page]** 选项， **[!UICONTROL Next]** 和 **[!UICONTROL Previous]** 按钮从报表页面中消失。

## 添加页眉和页脚 {#adding-a-header-and-a-footer}

利用报表属性窗口还可定义布局元素，例如：窗口的标题、页眉和页脚的HTML内容。

要访问属性窗口，请单击 **[!UICONTROL Properties]** 按钮。

![](assets/reporting_properties.png)

的 **[!UICONTROL Page]** 选项卡，可个性化显示。

![](assets/s_ncs_advuser_report_properties_04.png)

此选项卡中配置的内容将在所有报表页面上可见。

的 **[!UICONTROL Texts]** 子选项卡，用于定义变量内容：如果报告设计用于多种语言，则在翻译周期中将考虑这一点。

这允许您创建文本片段列表，并将它们链接到标识符：

![](assets/s_ncs_advuser_report_properties_04a.png)

然后，将这些标识符插入报表的HTML内容：

![](assets/s_ncs_advuser_report_properties_04b.png)

在显示报表时，系统会自动将其替换为相应的内容。

与HTML文本类似，此操作模式允许您将报表中使用的文本集中并管理其翻译。 在此选项卡中创建的文本由Adobe Campaign集成翻译工具自动收集。
