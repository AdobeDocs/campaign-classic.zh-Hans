---
product: campaign
title: 元素布局
description: 元素布局
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---

# 元素布局{#element-layout}

![](../../assets/common.svg)

除了此处详述的各种图表外：[图表类型和变体](../../reporting/using/creating-a-chart.md#chart-types-and-variants)，您可以调整显示并向报表页面添加元素。

您可以使用容器：这些选项允许您链接页面的多个元素，并在列和/或单元格中配置其布局。 [此部分](../../web/using/defining-web-forms-layout.md#creating-containers)中详细说明了如何使用它们。

您可以在树的根位置配置报表布局，并为每个容器过载报表布局。 页面按列进行排序。 容器也按列进行排序。 只有静态项目和图形项目会按单元格进行排序。

## 为每个页面定义选项 {#defining-the-options-for-each-page}

您可以使用报表每个页面上的选项。

**[!UICONTROL General]**&#x200B;选项卡允许您更改页面标题，以及配置图例位置和在报表页面之间浏览。

![](assets/s_ncs_advuser_report_wizard_022.png)

使用&#x200B;**[!UICONTROL Title]**&#x200B;字段可将报表页面标题中的标签个性化。 窗口的标题可通过报告的&#x200B;**[!UICONTROL Properties]**&#x200B;窗口进行配置。 有关更多信息，请参阅[添加页眉和页脚](#adding-a-header-and-a-footer)。

**[!UICONTROL Display settings]**&#x200B;选项允许您选择报表页面中控件标题的位置并定义页面上的列数。 有关页面布局的更多信息，请参阅[此部分](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page)的&#x200B;**项目布局**&#x200B;部分。

选择&#x200B;**[!UICONTROL Browse]**&#x200B;部分中的各种选项，以授权从一个报表页面浏览到另一个报表页面。 如果选择&#x200B;**[!UICONTROL Disable next page]**&#x200B;或&#x200B;**[!UICONTROL Disable previous page]**&#x200B;选项，则&#x200B;**[!UICONTROL Next]**&#x200B;和&#x200B;**[!UICONTROL Previous]**&#x200B;按钮将从报表页面中消失。

## 添加页眉和页脚 {#adding-a-header-and-a-footer}

利用报表属性窗口还可定义布局元素，例如：窗口的标题、页眉和页脚的HTML内容。

要访问属性窗口，请单击报表的&#x200B;**[!UICONTROL Properties]**&#x200B;按钮。

![](assets/reporting_properties.png)

使用&#x200B;**[!UICONTROL Page]**&#x200B;选项卡可以个性化显示。

![](assets/s_ncs_advuser_report_properties_04.png)

此选项卡中配置的内容将在所有报表页面上可见。

使用&#x200B;**[!UICONTROL Texts]**&#x200B;子选项卡可定义变量内容：如果报告设计用于多种语言，则在翻译周期中将考虑这一点。

这允许您创建文本片段列表，并将它们链接到标识符：

![](assets/s_ncs_advuser_report_properties_04a.png)

然后，将这些标识符插入报表的HTML内容：

![](assets/s_ncs_advuser_report_properties_04b.png)

在显示报表时，系统会自动将其替换为相应的内容。

与HTML文本一样，此操作模式允许您将报表中使用的文本集中起来并管理其翻译。 在此选项卡中创建的文本由Adobe Campaign集成翻译工具自动收集。
