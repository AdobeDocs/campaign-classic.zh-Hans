---
solution: Campaign Classic
product: campaign
title: 创建假设验证
description: 创建假设验证
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1061'
ht-degree: 0%

---


# 创建假设验证{#creating-hypotheses}

创建假设验证/将活动关联到优惠或投放有多种可能：

* 通过文 **[!UICONTROL Measurement hypotheses]** 件夹，根据现有模板创建新假设验证并将其链接到现有投放。
* 通过活动 **[!UICONTROL Edit]** 中的 **[!UICONTROL Measurement]** >选项卡。
* 通过 **[!UICONTROL Measurement]** 从投放创建的活动选项。

假设验证只有在营销活动启动且收件人收到投放后才能计算。 如果假设验证基于优惠建议，则至少需要显示该，并且仍然有效。 优惠和投放假设验证通过文件夹 **[!UICONTROL Measurement hypotheses]** 创建，并基于假设验证模板。 但是，可以直接在假设验证中引用投放或活动开始之前的活动。 在这种情况下，假设验证将根据执行设置(有关详细信息，请参阅假设验证模板执行设置)在启动营销活动后 [自动计算](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)。

## 在假设验证上快速创建投放 {#creating-a-hypothesis-on-the-fly-on-a-delivery}

要在现有假设验证上创建投放，请应用以下流程：

>[!NOTE]
>
>此操作仅可用于待处理投放。

1. 在Adobe Campaign树中，转到 **[!UICONTROL Campaign management > Measurement hypotheses]**。
1. 单击 **[!UICONTROL New]** 按钮或右键单击假设验证列表，然 **[!UICONTROL New]** 后在下拉列表中选择。

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 在“假设验证”窗口中，选择以前创建的模板(请参阅 [假设验证模板](../../campaign/using/hypothesis-templates.md))。

   ![](assets/response_hypothesis_instance_creation_003.png)

   在选定模型中定义的假设验证上下文将显示在窗口中。

   >[!NOTE]
   >
   >在模板中定义且在此步骤中不可见的设置也保留在内存中，并重新分配给进行中的假设验证。

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 选择要为其创建投放的假设验证。

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 您可以通过编辑和选项卡来 **[!UICONTROL General]**&#x200B;个性化 **[!UICONTROL Transactions]** 您的 **[!UICONTROL Scope]** 假设验证。 有关此的详细信息，请参 [阅创建假设验证模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 开始假设验证，方法是单 **[!UICONTROL Start]**&#x200B;击。

   将自动创建工作流以执行测量。 名称会根据假设验证配置自动定义。

   >[!CAUTION]
   >
   >如果选中了复选框，则可以访 **[!UICONTROL Keep execution workflow]** 问它。\
   >仅当运行假设验证时出错时，才能为调试目的激活此选项。 自动生成的工作流会保存在 **[!UICONTROL Administration]** Adobe Campaign资 **[!UICONTROL Production]** 源管理器 **[!UICONTROL Objects created automatically]** 的 **[!UICONTROL Campaign workflows]** > >文件夹中。
   > 
   >此外，不得修改自动生成的工作流。 在以后的计算中，任何最终的修改都不会考虑在其他地方。
   >
   >如果已选中此选项，请在执行该工作流后将其删除。

   ![](assets/response_hypothesis_instance_creation_006.png)

   计算完成后，测量指标将自动更新。

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 如有必要，请更改设置并重新开始假设验证。

## 在假设验证投放中引用活动 {#referencing-a-hypothesis-in-a-campaign-delivery}

您可以在营销假设验证启动之前引用活动。 在这种情况下，根据假设验证模板中定义的执行设置，在发送投放后，假设验证将自动启动。 要在假设验证中创建投放，请应用以下流程：

1. 根据您的需要，您可以创建一个或多个类 **[!UICONTROL Delivery]** 型模板，如创 [建假设验证模型中所述](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. 创建营销活动和定位工作流。
1. 在投放窗口中，单击图 **[!UICONTROL Delivery measurement]** 标。
1. 选择假设验证模板(在模型中配置的查询显示在假设验证窗口中)。

   假设验证将根据模型中配置的日期(请参阅假设验证模板执行设置)在活动完成 [后自动计算](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)。

   ![](assets/response_hypothesis_instance_creation_008.png)

## 将默认假设验证添加到活动的投放 {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

您可以直接在假设验证级别引用活动。 在这种情况下，假设验证将自动链接到在活动中创建的所有投放。 操作步骤：

1. 转到活动 **[!UICONTROL Edit]** 的选项卡。
1. 在测量部分，单击选 **[!UICONTROL Default hypotheses]** 项卡。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 单击 **[!UICONTROL Add]** 并选择假设验证模板。

   ![](assets/response_hypothesis_instance_creation_011.png)

   现在，基于此模板的假设验证将默认在活动的每个新投放中引用。

   ![](assets/response_hypothesis_instance_creation_012.png)

假设验证结果可在假设验证的 **[!UICONTROL General]** 和 **[!UICONTROL Reactions]** 选项卡中查看(请参 [阅假设验证跟踪](../../campaign/using/hypothesis-tracking.md))

有关详细信息，您还可以参阅 [示例：创建链接到假设验证的投放](#example--creating-a-hypothesis-linked-to-a-delivery)。

## 在假设验证上创建优惠 {#creating-a-hypothesis-on-an-offer}

在优惠建议上创建假设验证与在动态投放上创建假设验证相似。 只要假设验证处于活动状态，就可以执行优惠。 计算期间基于优惠建议日期。 当假设验证允许您将收件人关联到购买时，可能会接受的优惠建议的状态会自动更改(有关详细信息，请参阅“交易 [记录](../../campaign/using/hypothesis-templates.md#transactions)”)。

1. 创建一个或多个 **[!UICONTROL Offer]** 类型模型，如创 [建假设验证模型中所述](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. Go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node.
1. 通过选 **[!UICONTROL Offers]** 择先前创建的模型创建类型假设验证。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中创建的查询会出现在窗口中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 选择要为其创建优惠的假设验证。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 根据需要调整查询。
1. 单 **[!UICONTROL Start]** 击以运行假设验证。
1. 假设验证结果可在其选项卡和 **[!UICONTROL General]** 选项卡 **[!UICONTROL Reactions]** 中查看(请参 [阅假设验证跟踪](../../campaign/using/hypothesis-tracking.md))。

   在优惠上创建的假设验证在选项卡中 **[!UICONTROL Measurement]** 引用。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果假设验证 **[!UICONTROL Update offer proposition status]** 模板中启用了该选项，则优惠建议的状态将自动更改，从而提供有关活动影响的反馈(有关详细信息，请参阅 [事务](../../campaign/using/hypothesis-templates.md#transactions))。

## 示例：创建链接到假设验证的投放 {#example--creating-a-hypothesis-linked-to-a-delivery}

在此示例中，我们要创建链接到假设验证的投放。 此假设验证将基于先前创建的模型(请参阅 [示例：在假设验证上创建投放模板](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery))。 然后，我们将优化从模型继承的查询，以对购买表的特定文章进行假设验证。

1. 创建活动和投放(有关详细信息，请参阅 [创建活动](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   在我们的示例中，我们将使用直接邮件类型投放。

1. 配置种子地址：之前创建的假设验证模板配置为在反应结果中考虑对照组。

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >有关详细信息，请参 [阅定义对照组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

1. 打开图 **[!UICONTROL Direct mail delivery]** 标，单 **[!UICONTROL Delivery measurement]** 击图标，然后单击 **[!UICONTROL Add]**。

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 从下拉式假设验证中选择之前创建的列表模板。

   ![](assets/response_hypothesis_delivery_example_004.png)

   将显示在模型中创建的查询。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 单 **[!UICONTROL Edit query...]** 击并细化查询，输入假设验证将关注的产品。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以检查假设验证是否已链接到活动的“>” **[!UICONTROL Edit]** 选 **[!UICONTROL Measurement]** 项卡中的投放。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 启动定位工作流并运行必要的检查，直到活动完成(有关详细信息，请参 [阅启动投放](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery))。

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign树中，转到节 **[!UICONTROL Campaign management > Measurement hypotheses]** 点以检查假设验证计算的指示符。

   ![](assets/response_hypothesis_delivery_example_010.png)

