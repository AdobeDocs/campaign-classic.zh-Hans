---
product: campaign
title: 定义条件内容
description: 定义条件内容
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---

# 定义条件内容{#defining-a-conditional-content}



您可以对特定报表项目或页面的显示进行条件设置。

要使特定项目成为条件项目，请调整其可见性设置。 有关更多信息，请参阅 [条件项显示](#conditioning-item-display).

要以条件方式显示一个或多个页面，请使用 **[!UICONTROL Test]** 键入活动。 有关更多信息，请参阅 [条件页面显示](#conditioning-page-display).

## 条件项显示 {#conditioning-item-display}

要以条件方式显示部分报表，您需要定义其可见性条件：如果不满足这些条件，则不会显示项目。

可见性条件可能取决于运算符状态，取决于在报表页面中选择或输入的项目。

中提供了一些示例，用于显示页面上项目的条件显示 [此部分](../../web/using/form-rendering.md#defining-fields-conditional-display).

在以下示例中，显示条件取决于语言：

![](assets/reporting_display_condition.png)

## 条件页面显示 {#conditioning-page-display}

在报表的图表中， **[!UICONTROL Test]** 活动，可根据一个或多个条件更改页面顺序。

本活动基于以下工作原则：

1. 放置 **[!UICONTROL Test]** 并对其进行编辑。
1. 单击 **[!UICONTROL Add]** 按钮以创建各种可能的情况。

   ![](assets/reporting_test_sample.png)

   对于每种情况，都会向 **[!UICONTROL Test]** 活动。

   ![](assets/reporting_test_transitions.png)

1. 选择 **[!UICONTROL Enable default transition]** 要添加过渡，请在不满足其中一个已配置条件时执行。

   如需详细信息，请参阅[此部分](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

A **[!UICONTROL Test]** 活动可置于图表的开头，以根据上下文或运算符配置文件等条件显示。
