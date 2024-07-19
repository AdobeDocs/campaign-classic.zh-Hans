---
product: campaign
title: 定义条件内容
description: 定义条件内容
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Reporting, Monitoring
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 7%

---

# 定义条件内容{#defining-a-conditional-content}



您可以对特定报表项或页面的显示进行限制。

要使特定项目具有条件，请调整其可见性设置。 有关详细信息，请参阅[条件项显示](#conditioning-item-display)。

若要使一个或多个页面的显示具有条件，请使用&#x200B;**[!UICONTROL Test]**&#x200B;类型活动。 有关详细信息，请参阅[条件页面显示](#conditioning-page-display)。

## 条件项显示 {#conditioning-item-display}

要使显示的部分报告具有条件，您需要定义其可见性条件：如果不满足这些条件，将不会显示项目。

可见性条件可能取决于操作员状态、在报告页面中选择或输入的项目。

[此部分](../../web/using/form-rendering.md#defining-fields-conditional-display)中提供了显示页面上项目的条件显示的示例。

在以下示例中，显示条件取决于语言：

![](assets/reporting_display_condition.png)

## 条件页面显示 {#conditioning-page-display}

在报表的图表中，**[!UICONTROL Test]**&#x200B;活动允许您根据一个或多个条件更改页面顺序。

本练习基于以下工作原理：

1. 将&#x200B;**[!UICONTROL Test]**&#x200B;放入图表并进行编辑。
1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以创建各种可能的情况。

   ![](assets/reporting_test_sample.png)

   对于每种情况，都会向&#x200B;**[!UICONTROL Test]**&#x200B;活动添加输出转换。

   ![](assets/reporting_test_transitions.png)

1. 选择&#x200B;**[!UICONTROL Enable default transition]**&#x200B;以添加过渡，以防不满足其中一个配置的条件。

   如需详细信息，请参阅[此小节](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

可以将&#x200B;**[!UICONTROL Test]**&#x200B;活动放在图表的开头处，以根据实例的上下文或操作员配置文件对显示进行条件。
