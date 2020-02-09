---
title: 定义条件内容
seo-title: 定义条件内容
description: 定义条件内容
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 定义条件内容{#defining-a-conditional-content}

您可以设置特定报告项目或页面显示条件。

要使特定项目成为条件项，请调整其可见性设置。 有关详细信息，请参阅 [Conditioning（调整）项显示](#conditioning-item-display)。

要使一个或多个页面的显示成为条件，请使用类 **[!UICONTROL Test]** 型活动。 For more on this, refer to [Conditioning page display](#conditioning-page-display).

## 调节物品显示器 {#conditioning-item-display}

要使报表的部分显示为条件，您需要定义其可见性条件：如果未满足这些要求，则不显示这些项目。

可见性条件可能取决于操作符状态，取决于在报告页面中选择或输入的项目。

本节提供了显示页面上项目的条件显示 [示例](../../web/using/form-rendering.md#defining-fields-conditional-display)。

在以下示例中，显示条件取决于语言：

![](assets/reporting_display_condition.png)

## 调整页面显示 {#conditioning-page-display}

在报表的图表中，通过活 **[!UICONTROL Test]** 动，可根据一个或多个条件更改页面顺序。

本活动基于以下操作原则：

1. 将图表 **[!UICONTROL Test]** 放入图表中并进行编辑。
1. 单击该 **[!UICONTROL Add]** 按钮可创建各种可能的情况。

   ![](assets/reporting_test_sample.png)

   对于每种情况，都会向活动添加一个输出过 **[!UICONTROL Test]** 渡。

   ![](assets/reporting_test_transitions.png)

1. 选择 **[!UICONTROL Enable default transition]** 要添加过渡的选项，以防其中一个配置的条件不满足。

   如需详细信息，请参阅[此部分](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

可 **[!UICONTROL Test]** 以将活动放置在图表的开头，以根据上下文或操作符配置文件（例如）对显示进行条件调整。
