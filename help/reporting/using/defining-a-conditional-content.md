---
product: campaign
title: 定义条件内容
description: 定义条件内容
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Reporting, Monitoring
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 8%

---

# 定义条件内容{#defining-a-conditional-content}



您可以对特定报表项或页面的显示进行限制。

要使特定项目具有条件，请调整其可见性设置。 有关详细信息，请参见 [条件项显示](#conditioning-item-display).

要使一个或多个页面的显示符合条件，请使用 **[!UICONTROL Test]** 键入activity。 有关详细信息，请参见 [条件页面显示](#conditioning-page-display).

## 条件项显示 {#conditioning-item-display}

要使显示的部分报告具有条件，您需要定义其可见性条件：如果不满足这些条件，将不会显示项目。

可见性条件可能取决于操作员状态、在报告页面中选择或输入的项目。

有关显示页面上项目的条件显示的示例，请参见 [本节](../../web/using/form-rendering.md#defining-fields-conditional-display).

在以下示例中，显示条件取决于语言：

![](assets/reporting_display_condition.png)

## 条件页面显示 {#conditioning-page-display}

在报表的图表中， **[!UICONTROL Test]** 通过活动，可根据一个或多个条件更改页面顺序。

本练习基于以下工作原理：

1. 放置 **[!UICONTROL Test]** 在图表中对其进行编辑。
1. 单击 **[!UICONTROL Add]** 按钮创建各种可能的情况。

   ![](assets/reporting_test_sample.png)

   对于每种情况，输出转换将添加到 **[!UICONTROL Test]** 活动。

   ![](assets/reporting_test_transitions.png)

1. 选择 **[!UICONTROL Enable default transition]** 以添加过渡，以防不满足其中一个配置的条件。

   如需详细信息，请参阅[此小节](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

A **[!UICONTROL Test]** 活动可以放置在图表的开头，以根据上下文或操作员个人资料等条件限定显示。
