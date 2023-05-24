---
product: campaign
title: 创建假设验证
description: 了解如何在Campaign响应管理器中创建假设验证
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: e0b3bc9f-5e81-463f-a59e-cd972a47109b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 3%

---

# 创建假设验证{#creating-hypotheses}



创建/将假设链接到活动选件或投放有多种可能性：

* 通过 **[!UICONTROL Measurement hypotheses]** 文件夹，方法是基于现有模板创建新假设验证，并将其链接到现有投放。
* 通过 **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** 选项卡。
* 通过 **[!UICONTROL Measurement]** 从营销活动创建的投放选项。

只有在启动营销活动且收件人收到投放后，才能计算假设验证。 如果假设基于优惠建议，那么后者至少需要呈现，并且仍然活跃。 通过创建优惠和投放假设 **[!UICONTROL Measurement hypotheses]** 文件夹并且基于假设验证模板。 但是，可以在营销活动开始之前直接在投放或营销活动中引用假设。 在这种情况下，将根据执行设置，在启动营销活动后自动计算假设验证。 [了解详情](hypothesis-templates.md#hypothesis-template-execution-settings)

## 在投放时动态创建假设验证 {#creating-a-hypothesis-on-the-fly-on-a-delivery}

要在现有投放上创建假设验证，请应用以下流程：

>[!NOTE]
>
>此操作仅适用于待处理的投放。

1. 在Adobe Campaign树中，转到 **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. 单击 **[!UICONTROL New]** 按钮或右键单击假设的列表并选择 **[!UICONTROL New]** 下拉列表中。

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 在假设验证窗口中，选择之前创建的模板。 [了解详情](hypothesis-templates.md)

   ![](assets/response_hypothesis_instance_creation_003.png)

   在所选模型中定义的假设验证上下文将显示在窗口中。

   >[!NOTE]
   >
   >模板中定义且在此步骤不可见的设置也会保留在内存中，并重新分配到正在进行的假设验证。

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 选择要为其创建假设验证的投放。

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 您可以通过编辑 **[!UICONTROL General]**， **[!UICONTROL Transactions]** 和 **[!UICONTROL Scope]** 选项卡。 [了解详情](hypothesis-templates.md#creating-a-hypothesis-model)
1. 通过单击开始假设验证 **[!UICONTROL Start]**.

   将自动创建工作流以执行测量。 根据假设验证配置，会自动定义名称。

   >[!CAUTION]
   >
   >如果您已选中 **[!UICONTROL Keep execution workflow]** 盒子。\
   >如果运行假设验证时出错，则必须仅出于调试目的激活此选项。 自动生成的工作流将保存在中 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** 文件夹(在Adobe Campaign资源管理器中)。
   > 
   >此外，不得修改自动生成的工作流。 任何最终修改都不会在别处被纳入考量，以供日后计算。
   >
   >如果选中了此选项，则在执行工作流后将其删除。

   ![](assets/response_hypothesis_instance_creation_006.png)

   计算完成后，测量指标将自动更新。

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 如有必要，请更改设置并重新启动假设验证。

## 在活动投放中引用假设验证 {#referencing-a-hypothesis-in-a-campaign-delivery}

在营销活动开始之前，您可以在营销活动中引用假设验证。 在这种情况下，根据假设验证模板中定义的执行设置，发送投放后将自动启动假设验证。 要在投放中创建假设验证，请应用以下流程：

1. 根据您的需求，您可以创建一个或多个 **[!UICONTROL Delivery]** 键入模板，如中所述 [本节](hypothesis-templates.md#creating-a-hypothesis-model)
1. 创建营销活动和定位工作流。
1. 在投放窗口中，单击 **[!UICONTROL Delivery measurement]** 图标。
1. 选择假设验证模板（模型中配置的查询显示在假设验证窗口中）。

   一旦营销活动完成，系统会根据模型中配置的日期，自动计算假设验证。 [了解详情](hypothesis-templates.md#hypothesis-template-execution-settings)

   ![](assets/response_hypothesis_instance_creation_008.png)

## 向营销活动的投放添加默认假设验证 {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

您可以在活动级别直接引用假设验证。 在这种情况下，假设验证将自动链接到营销活动中创建的所有投放。 操作步骤：

1. 转到 **[!UICONTROL Edit]** 选项卡中的选定内容进行标识。
1. 在测量部分中，单击 **[!UICONTROL Default hypotheses]** 选项卡。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 单击 **[!UICONTROL Add]** 并选择假设验证模板。

   ![](assets/response_hypothesis_instance_creation_011.png)

   现在，默认情况下，营销活动的每个新投放都将引用基于此模板的假设。

   ![](assets/response_hypothesis_instance_creation_012.png)

假设验证结果可以在 **[!UICONTROL General]** 和 **[!UICONTROL Reactions]** 假设验证的选项卡。 [了解详情](hypothesis-tracking.md)

有关更多信息，您还可以参阅 [此示例](#example--creating-a-hypothesis-linked-to-a-delivery).

## 对优惠创建假设验证 {#creating-a-hypothesis-on-an-offer}

在优惠建议上创建假设与创建即时投放假设类似。 只要优惠处于活动状态，就可以执行假设验证。 计算期间乃根据优惠建议日期而定。 当假设验证允许您将收件人链接到购买时，可能会被接受的优惠建议状态可以自动更改。 [了解详情](hypothesis-templates.md#transactions)

1. 创建一个或多个 **[!UICONTROL Offer]** 键入模型，如中所述 [本节](hypothesis-templates.md#creating-a-hypothesis-model).
1. 转到 **[!UICONTROL Campaign management > Measurement hypotheses]** 节点。
1. 创建 **[!UICONTROL Offers]** 通过选择之前创建的模型来键入假设验证。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中创建的查询将显示在窗口中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 选择要为其创建假设验证的选件。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 根据需要优化查询。
1. 单击 **[!UICONTROL Start]** 运行假设验证。
1. 假设验证结果可以在以下部分中查看： **[!UICONTROL General]** 和 **[!UICONTROL Reactions]** 选项卡。 [了解详情](hypothesis-tracking.md)

   有关对优惠所做的假设，请参阅 **[!UICONTROL Measurement]** 选项卡。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果 **[!UICONTROL Update offer proposition status]** 选项已在假设验证模板中启用，优惠建议的状态会自动更改，从而提供对营销活动影响的反馈(有关更多信息，请参阅 [交易](hypothesis-templates.md#transactions))。

## 示例：创建与投放关联的假设验证 {#example--creating-a-hypothesis-linked-to-a-delivery}

在本例中，我们要创建一个与投放关联的假设验证。 此假设将基于之前创建的模型。 [了解详情](hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)

然后，我们将优化从模型继承的查询，以对购买表的特定文章进行假设。

1. 创建活动和投放。 [了解详情](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)

   在我们的示例中，我们将使用直邮类型投放。

1. 配置种子地址：之前创建的假设验证模板配置为在反应结果中考虑控制组。

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >有关更多信息，请参见[此章节](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

1. 打开 **[!UICONTROL Direct mail delivery]** 并单击 **[!UICONTROL Delivery measurement]** 图标，然后单击 **[!UICONTROL Add]**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 从下拉列表中选择之前创建的假设验证模板。

   ![](assets/response_hypothesis_delivery_example_004.png)

   将显示在模型中创建的查询。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 单击 **[!UICONTROL Edit query...]** 并通过输入假设验证将涉及的产品来优化查询。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以在中检查假设验证是否与交付相关联 **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** 选项卡中的选定内容进行标识。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 启动定位工作流并运行必要的检查，直到营销活动完成。 [了解详情](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign树中，转到 **[!UICONTROL Campaign management > Measurement hypotheses]** 节点以检查由假设验证计算的指标。

   ![](assets/response_hypothesis_delivery_example_010.png)
