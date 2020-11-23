---
solution: Campaign Classic
product: campaign
title: 定义条件性内容
description: 定义条件性内容
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---


# 定义条件性内容{#defining-a-conditional-content}

您可以对特定报表项目或页面的显示进行条件设置。

要使特定项目成为条件项，请调整其可见性设置。 有关详细信息，请参 [阅Conditioning项目显示](#conditioning-item-display)。

要使一个或多个页面显示为条件页面，请使用类 **[!UICONTROL Test]** 型活动。 For more on this, refer to [Conditioning page display](#conditioning-page-display).

## 调理项显示器 {#conditioning-item-display}

要使报表的部分显示为条件，您需要定义其可见性条件：如果不满足这些条件，则不显示项目。

可见性条件取决于操作符状态，取决于在报告页面中选择或输入的项目。

本节提供了显示页面上项目的条件显示 [示例](../../web/using/form-rendering.md#defining-fields-conditional-display)。

在以下示例中，显示条件取决于语言：

![](assets/reporting_display_condition.png)

## 调整页面显示 {#conditioning-page-display}

在报表的图表中，活动 **[!UICONTROL Test]** 允许您根据一个或多个条件更改页面顺序。

本活动基于以下操作原则：

1. 将图 **[!UICONTROL Test]** 表放入并编辑它。
1. 单击按 **[!UICONTROL Add]** 钮以创建各种可能的情况。

   ![](assets/reporting_test_sample.png)

   对于每种情况，都会向过渡添加一个输出 **[!UICONTROL Test]** 活动。

   ![](assets/reporting_test_transitions.png)

1. 选择 **[!UICONTROL Enable default transition]** 要添加过渡，以防其中一个配置的条件不满足。

   如需详细信息，请参阅[此部分](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

可 **[!UICONTROL Test]** 以将活动放在图表的开始，以根据上下文或运算符用户档案（例如）对显示进行条件化。
