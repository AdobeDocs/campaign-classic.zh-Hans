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

您可以设置特定报表项目或页面显示的条件。

要使特定项目成为条件项，请调整其可见性设置。 有关详细信息，请参阅[Conditioning item display](#conditioning-item-display)。

要使一个或多个页面的显示成为条件，请使用&#x200B;**[!UICONTROL Test]**&#x200B;类型活动。 有关详细信息，请参阅[Conditioning page display](#conditioning-page-display)。

## 调节项显示器{#conditioning-item-display}

要使报表的部分显示为条件，您需要定义其可见性条件：如果未满足这些条件，则不显示项目。

可见性条件取决于操作符状态，取决于在报表页面中选择或输入的项目。

[本节](../../web/using/form-rendering.md#defining-fields-conditional-display)提供了显示页面上项目的条件显示的示例。

在以下示例中，显示条件取决于语言：

![](assets/reporting_display_condition.png)

## 调整页面显示{#conditioning-page-display}

在报表的图表中，**[!UICONTROL Test]**&#x200B;活动允许您根据一个或多个条件更改页面顺序。

此活动基于以下操作原则：

1. 将&#x200B;**[!UICONTROL Test]**&#x200B;放在图表中并编辑它。
1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮可创建各种可能的情况。

   ![](assets/reporting_test_sample.png)

   对于每种情况，都会向&#x200B;**[!UICONTROL Test]**&#x200B;过渡添加输出活动。

   ![](assets/reporting_test_transitions.png)

1. 选择&#x200B;**[!UICONTROL Enable default transition]**&#x200B;以添加过渡，以防其中一个配置的条件不满足。

   如需详细信息，请参阅[此部分](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

**[!UICONTROL Test]**&#x200B;活动可放置在图表的开始，以根据上下文或运算符用户档案（例如）对显示进行条件设置。
