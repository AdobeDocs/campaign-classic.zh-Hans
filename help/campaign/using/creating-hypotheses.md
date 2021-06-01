---
product: campaign
title: 创建假设验证
description: 了解如何在Campaign响应管理器中创建假设验证
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: e0b3bc9f-5e81-463f-a59e-cd972a47109b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---

# 创建假设验证{#creating-hypotheses}

创建假设/将假设链接到营销活动选件或投放有多种可能性：

* 通过&#x200B;**[!UICONTROL Measurement hypotheses]**&#x200B;文件夹，根据现有模板创建新假设并将其链接到现有投放。
* 通过营销活动中的&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Measurement]**&#x200B;选项卡。
* 通过从营销策划创建的投放的&#x200B;**[!UICONTROL Measurement]**&#x200B;选项。

仅当营销活动启动且收件人收到投放后，才能计算假设验证。 如果假设是基于一个优惠建议的，那么后者至少需要被提出，并且仍然是主动的。 选件和投放假设是通过&#x200B;**[!UICONTROL Measurement hypotheses]**&#x200B;文件夹创建的，并基于假设验证模板。 但是，在营销活动开始之前，可以直接在投放或营销活动中引用假设验证。 在这种情况下，一旦根据执行设置启动营销活动，就会自动计算假设（有关更多信息，请参阅[假设验证模板执行设置](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)）。

## 在投放中即时创建假设{#creating-a-hypothesis-on-the-fly-on-a-delivery}

要对现有投放创建假设验证，请应用以下流程：

>[!NOTE]
>
>此操作仅适用于待处理投放。

1. 在Adobe Campaign树中，转到&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**。
1. 单击&#x200B;**[!UICONTROL New]**&#x200B;按钮或右键单击假设列表并在下拉列表中选择&#x200B;**[!UICONTROL New]**。

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 在假设验证窗口中，选择之前创建的模板（请参阅[假设验证模板](../../campaign/using/hypothesis-templates.md)）。

   ![](assets/response_hypothesis_instance_creation_003.png)

   在所选模型中定义的假设上下文将显示在窗口中。

   >[!NOTE]
   >
   >在模板中定义且在此步骤中不可见的设置也会保留在内存中，并重新分配到正在进行的假设。

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 选择要为其创建假设验证的投放。

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 您可以通过编辑&#x200B;**[!UICONTROL General]**、**[!UICONTROL Transactions]**&#x200B;和&#x200B;**[!UICONTROL Scope]**&#x200B;选项卡，将您的假设个性化。 有关更多信息，请参阅[创建假设模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 通过单击&#x200B;**[!UICONTROL Start]**&#x200B;启动该假设验证。

   将自动创建工作流以执行测量。 名称会根据假设验证配置自动定义。

   >[!CAUTION]
   >
   >如果已选中&#x200B;**[!UICONTROL Keep execution workflow]**&#x200B;框，则可以访问此复选框。\
   >出于调试目的，如果运行假设时出错，必须仅激活此选项。 自动生成的工作流将保存在Adobe Campaign资源管理器的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]**&#x200B;文件夹中。
   > 
   >此外，不得修改自动生成的工作流。 在其他地方，任何最终修改都不会被考虑，以备日后计算。
   >
   >如果已选中此选项，请在执行该工作流后将其删除。

   ![](assets/response_hypothesis_instance_creation_006.png)

   计算完成后，测量指标会自动更新。

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 如有必要，请更改设置并重新启动假设验证。

## 在促销活动投放{#referencing-a-hypothesis-in-a-campaign-delivery}中引用假设验证

您可以在营销活动启动前引用该假设。 在这种情况下，假设验证将根据假设验证模板中定义的执行设置，在发送投放后自动启动。 要在投放中创建假设，请应用以下流程：

1. 根据您的需要，可以创建一个或多个&#x200B;**[!UICONTROL Delivery]**&#x200B;类型模板，如[此部分](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)中所述
1. 创建营销活动和定位工作流。
1. 在投放窗口中，单击&#x200B;**[!UICONTROL Delivery measurement]**&#x200B;图标。
1. 选择假设验证模板（在模型中配置的查询显示在假设验证窗口中）。

   营销活动完成后，将根据模型中配置的日期自动计算假设（请参阅[假设模板执行设置](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)）。

   ![](assets/response_hypothesis_instance_creation_008.png)

## 向促销活动{#adding-a-default-hypothesis-to-deliveries-for-a-campaign}的投放添加默认假设验证

您可以直接引用营销活动级别的假设验证。 在这种情况下，假设将自动链接到营销活动中创建的所有投放。 操作步骤：

1. 转到营销活动的&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。
1. 在测量部分，单击&#x200B;**[!UICONTROL Default hypotheses]**&#x200B;选项卡。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择一个假设验证模板。

   ![](assets/response_hypothesis_instance_creation_011.png)

   现在，基于此模板的假设验证将在营销活动的每个新投放中默认引用。

   ![](assets/response_hypothesis_instance_creation_012.png)

可以在假设验证的&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Reactions]**&#x200B;选项卡中查看假设验证结果（请参阅[假设验证跟踪](../../campaign/using/hypothesis-tracking.md)）

有关更多信息，还可以参阅[此示例](#example--creating-a-hypothesis-linked-to-a-delivery)。

## 创建选件{#creating-a-hypothesis-on-an-offer}的假设验证

就优惠建议创建假设与即时投放假说类似。 只要选件处于活动状态，就可以执行该假设。 计算期间基于优惠建议日期。 当假设允许您将收件人关联到购买时，可能会被接受的选件建议的状态将自动更改（有关更多信息，请参阅[Transactions](../../campaign/using/hypothesis-templates.md#transactions)）。

1. 创建一个或多个&#x200B;**[!UICONTROL Offer]**&#x200B;类型模型，如[此部分](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)中所述。
1. 转到&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;节点。
1. 通过选择之前创建的模型来创建&#x200B;**[!UICONTROL Offers]**&#x200B;类型假设。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中创建的查询将出现在窗口中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 选择要为其创建假设的选件。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 根据需要优化查询。
1. 单击&#x200B;**[!UICONTROL Start]**&#x200B;以运行假设验证。
1. 可以在其&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Reactions]**&#x200B;选项卡中查看假设验证结果（请参阅[假设验证跟踪](../../campaign/using/hypothesis-tracking.md)）。

   在&#x200B;**[!UICONTROL Measurement]**&#x200B;选项卡中会引用对选件所做的假设。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果在假设验证模板中启用了&#x200B;**[!UICONTROL Update offer proposition status]**&#x200B;选项，则会自动更改选件主张的状态，从而提供有关促销活动影响的反馈（有关更多信息，请参阅[交易](../../campaign/using/hypothesis-templates.md#transactions)）。

## 示例：创建链接到投放{#example--creating-a-hypothesis-linked-to-a-delivery}的假设验证

在本例中，我们要创建链接到投放的假设验证。 此假设将基于之前创建的模型（请参阅[此示例](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)）。 然后，我们将优化从模型继承的查询，以对购买表的特定文章进行假设验证。

1. 创建营销活动和投放（有关更多信息，请参阅[创建营销活动](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)）。

   在本例中，我们将使用直邮类型投放。

1. 配置种子地址：之前创建的假设验证模板配置为在反应结果中考虑控制组。

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >有关更多信息，请参阅[定义控制组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

1. 打开&#x200B;**[!UICONTROL Direct mail delivery]**&#x200B;并单击&#x200B;**[!UICONTROL Delivery measurement]**&#x200B;图标，然后单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 从下拉列表中选择之前创建的假设验证模板。

   ![](assets/response_hypothesis_delivery_example_004.png)

   随即会显示在模型中创建的查询。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 单击&#x200B;**[!UICONTROL Edit query...]**，然后输入假设验证将涉及的产品以优化查询。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以检查该假设是否已链接到营销活动&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Measurement]**&#x200B;选项卡中的投放。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 启动定位工作流并运行必要的检查，直到营销活动完成（有关更多信息，请参阅[此部分](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)）。

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign树中，转到&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;节点以检查由假设计算的指标。

   ![](assets/response_hypothesis_delivery_example_010.png)
