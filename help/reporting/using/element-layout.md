---
solution: Campaign Classic
product: campaign
title: 元素布局
description: 元素布局
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---


# 元素布局{#element-layout}

除了下面详述的各种图表外： [图表类型和变体](../../reporting/using/creating-a-chart.md#chart-types-and-variants)，您可以调整显示并向报表页面添加元素。

您可以使用容器:这些组件允许您链接页面的多个元素，并在列和／或单元格中配置其布局。 本节详细介绍了如何使 [用它们](../../web/using/defining-web-forms-layout.md#creating-containers)。

您可以在树的根位置配置报表布局，并为每个容器使其过载。 页面按列排序。 容器也按列排序。 只有静态和图形项被分类为单元格。

## 定义每个页面的选项 {#defining-the-options-for-each-page}

您可以使用报表每个页面上的选项。

通过 **[!UICONTROL General]** 该选项卡可更改页面标题，以及配置图例位置和在报表页面之间浏览。

![](assets/s_ncs_advuser_report_wizard_022.png)

通过 **[!UICONTROL Title]** 该字段，您可以个性化报表页面标题中的标签。 窗口的标题可通过报告 **[!UICONTROL Properties]** 的窗口配置。 有关此内容的详细信息， [请参阅添加页眉和页脚](#adding-a-header-and-a-footer)。

通过 **[!UICONTROL Display settings]** 这些选项，您可以选择报表页面中控件标题的位置以及定义页面上的列数。 有关页面布局的详细信息，请参 **阅此部分** 的“项 [目布局”部分](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page)。

在部分中选择各种选 **[!UICONTROL Browse]** 项，以授权从一个报表页面浏览到另一个报表页面。 如果选 **[!UICONTROL Disable next page]** 择或 **[!UICONTROL Disable previous page]** 选项，则报表 **[!UICONTROL Next]** 页面中 **[!UICONTROL Previous]** 和按钮将消失。

## 添加页眉和页脚 {#adding-a-header-and-a-footer}

在报表属性窗口中，您还可以定义布局元素，例如：窗口的标题、页眉和页脚的HTML内容。

要访问属性窗口，请单 **[!UICONTROL Properties]** 击报表的按钮。

![](assets/reporting_properties.png)

该选 **[!UICONTROL Page]** 项卡使您能够个性化您的显示屏。

![](assets/s_ncs_advuser_report_properties_04.png)

此选项卡中配置的内容将显示在所有报告页面上。

子选 **[!UICONTROL Texts]** 项卡允许您定义变量内容：如果报告设计为用于多种语言，则在翻译周期中将考虑这一因素。

这允许您创建文本片段列表并将它们链接到标识符：

![](assets/s_ncs_advuser_report_properties_04a.png)

然后，将这些标识符插入报告的HTML内容：

![](assets/s_ncs_advuser_report_properties_04b.png)

在显示报告时，系统会自动将其替换为相应的内容。

与HTML文本一样，此操作模式使您能够集中报告中使用的文本并管理其翻译。 在此选项卡中创建的文本由Adobe Campaign集成翻译工具自动收集。
