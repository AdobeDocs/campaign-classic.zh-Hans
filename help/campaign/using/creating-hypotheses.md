---
title: 创建假设
seo-title: 创建假设
description: 创建假设
seo-description: null
page-status-flag: never-activated
uuid: 48b74772-473f-4fbc-a228-ce8e35a7b9ba
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 0f73de0e-e589-4e39-9895-209dad75db75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 创建假设{#creating-hypotheses}

创建／链接营销活动选件或投放的假设有多种可能：

* 通过文 **[!UICONTROL Measurement hypotheses]** 件夹，基于现有模板创建新假设并将其链接到现有交付。
* 通过营销 **[!UICONTROL Edit]** 活动 **[!UICONTROL Measurement]** 中的>选项卡。
* 通过从 **[!UICONTROL Measurement]** 营销活动创建的分发选项。

只有在营销活动启动且收件人已收到分发后，才能计算假设。 如果假设是基于一个报价提议，那么后者至少需要提出，并且仍然有效。 提供和交付假设是通过文件夹创 **[!UICONTROL Measurement hypotheses]** 建的并且基于假设模板。 但是，在营销活动开始之前，可以直接在分发或营销活动中引用假设。 在这种情况下，一旦营销活动启动，将根据执行设置自动计算假设(有关详细信息，请参阅假设模 [板执行设置](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings))。

## 在交货时即刻创建假设 {#creating-a-hypothesis-on-the-fly-on-a-delivery}

要在现有交货上创建假设，请应用以下流程：

>[!NOTE]
>
>此操作仅对待定提交可用。

1. 在Adobe Campaign树中，转到 **[!UICONTROL Campaign management > Measurement hypotheses]**。
1. 单击 **[!UICONTROL New]** 按钮或右键单击假设列表，然后在下拉 **[!UICONTROL New]** 列表中进行选择。

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 在假设窗口中，选择以前创建的模板(请参阅假 [设模板](../../campaign/using/hypothesis-templates.md))。

   ![](assets/response_hypothesis_instance_creation_003.png)

   在所选模型中定义的假设上下文显示在窗口中。

   >[!NOTE]
   >
   >在模板中定义且在此步骤中不可见的设置也保留在内存中，并重新分配到进行中的假设。

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 选择要为其创建假设的交付。

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 您可以通过编辑选项卡和选项卡来 **[!UICONTROL General]**&#x200B;个性化 **[!UICONTROL Transactions]** 您的 **[!UICONTROL Scope]** 假设。 有关此方面的详细信息，请参 [阅创建假设模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 通过单击开始假设 **[!UICONTROL Start]**。

   将自动创建工作流以执行测量。 名称会根据假设配置自动定义。

   >[!CAUTION]
   >
   >如果选中了该框，则可以访问 **[!UICONTROL Keep execution workflow]** 它。\
   >仅当运行假设时出错时，才能出于调试目的激活此选项。 自动生成的工作流会保存在Adobe Campaign资 **[!UICONTROL Administration]** 源管理器的> **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** 文件夹中。
   > 
   >此外，不得修改自动生成的工作流。 在以后的计算中，任何最终的修改都不会计入其他地方。
   >
   >如果已选中此选项，请在执行该工作流后将其删除。

   ![](assets/response_hypothesis_instance_creation_006.png)

   计算完成后，测量指示器会自动更新。

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 如有必要，请更改设置并重新开始假设。

## 在营销活动投递中引用假设 {#referencing-a-hypothesis-in-a-campaign-delivery}

您可以在营销活动开始之前参考假设。 在这种情况下，假设将在发送传送后基于假设模板中定义的执行设置自动启动。 要在交货中创建假设，请应用以下流程：

1. 根据您的需要，您可以创建一个或多个类 **[!UICONTROL Delivery]** 型模板，如创建假 [说模型中所述](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. 创建营销活动和定位工作流。
1. 在传送窗口中，单击图 **[!UICONTROL Delivery measurement]** 标。
1. 选择假设模板（在模型中配置的查询显示在假设窗口中）。

   营销活动完成后，将根据模型中配置的日期自动计算假设(请参阅假设模 [板执行设置](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings))。

   ![](assets/response_hypothesis_instance_creation_008.png)

## 将默认假设添加到营销活动的分发 {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

您可以直接在营销活动级别引用假设。 在这种情况下，假设将自动链接到营销活动中创建的所有提交。 操作步骤：

1. 转到营销 **[!UICONTROL Edit]** 活动的选项卡。
1. 在测量部分，单击选 **[!UICONTROL Default hypotheses]** 项卡。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 单击 **[!UICONTROL Add]** 并选择假设模板。

   ![](assets/response_hypothesis_instance_creation_011.png)

   现在，基于此模板的假设将在营销活动的每个新分发中默认引用。

   ![](assets/response_hypothesis_instance_creation_012.png)

假设结果可在假设的标签和 **[!UICONTROL General]** 标签 **[!UICONTROL Reactions]** 中查看(参 [阅假设跟踪](../../campaign/using/hypothesis-tracking.md))

有关详细信息，您还可以参阅示 [例：创建与交付相关的假设](#example--creating-a-hypothesis-linked-to-a-delivery)。

## 为选件创建假设 {#creating-a-hypothesis-on-an-offer}

在促销建议中创建假设与创建即时投放假设类似。 只要报价有效，就可以执行该假设。 计算期间基于优惠建议日期。 当假设允许您将收件人关联到购买时，可能会被接受的优惠提案的状态可以自动更改(有关详细信息，请参阅“交 [易](../../campaign/using/hypothesis-templates.md#transactions)”)。

1. 创建一个或多个 **[!UICONTROL Offer]** 类型模型，如创 [建假设模型中所述](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 转到节 **[!UICONTROL Campaign management > Measurement hypotheses]** 点。
1. 通过选 **[!UICONTROL Offers]** 择先前创建的模型创建类型假设。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中创建的查询将显示在窗口中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 选择要为其创建假设的选件。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 根据需要调整查询。
1. 单击 **[!UICONTROL Start]** 以运行假设。
1. 假设结果可在其选项卡和选项卡中查 **[!UICONTROL General]** 看( **[!UICONTROL Reactions]** 请参阅假设 [跟踪](../../campaign/using/hypothesis-tracking.md))。

   在选件中引用了关于选件的假 **[!UICONTROL Measurement]** 设。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果假 **[!UICONTROL Update offer proposition status]** 说模板中启用了该选项，则会自动更改选件主张的状态，从而提供有关营销活动影响的反馈(有关详细信息，请参阅 [事务](../../campaign/using/hypothesis-templates.md#transactions))。

## 示例：创建与交付相关的假设 {#example--creating-a-hypothesis-linked-to-a-delivery}

在本例中，我们要创建一个链接到交付的假设。 此假设将基于先前创建的模型(请参阅 [示例：在分发上创建假设模板](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery))。 然后，我们将细化从模型继承的查询，以对购买表的特定文章做出假设。

1. 创建营销活动和分发(有关详细信息，请参阅创 [建营销活动](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   在我们的示例中，我们将使用直邮类型交付。

1. 配置种子地址：先前创建的假设模板被配置成在反应结果中考虑控制组。

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >有关详细信息，请参 [阅定义控制组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

1. 打开图 **[!UICONTROL Direct mail delivery]** 标，单 **[!UICONTROL Delivery measurement]** 击图标，然后单击 **[!UICONTROL Add]**。

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 从下拉列表中选择以前创建的假设模板。

   ![](assets/response_hypothesis_delivery_example_004.png)

   此时将显示在模型中创建的查询。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 单击 **[!UICONTROL Edit query...]** 并优化查询，方法是输入假设将涉及的产品。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以检查假设是否已链接到营销活动的 **[!UICONTROL Edit]** >选项 **[!UICONTROL Measurement]** 卡中的分发。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 启动定位工作流并运行必要的检查，直到营销活动完成(有关详细信息，请参阅 [启动分发](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery))。

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign树中，转到节点以 **[!UICONTROL Campaign management > Measurement hypotheses]** 检查由假设计算的指示符。

   ![](assets/response_hypothesis_delivery_example_010.png)

