---
solution: Campaign Classic
product: campaign
title: 创建假设验证
description: 了解如何在活动响应管理器中创建假设验证
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---


# 创建假设验证{#creating-hypotheses}

创建假设验证/将活动链接到优惠或投放有多种可能：

* 通过&#x200B;**[!UICONTROL Measurement hypotheses]**&#x200B;文件夹，基于现有模板创建新假设验证并将其链接到现有投放。
* 通过活动中的&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Measurement]**&#x200B;选项卡。
* 通过从投放创建的活动的&#x200B;**[!UICONTROL Measurement]**&#x200B;选项。

假设验证只有在营销活动启动且收件人收到投放后才能计算。 如果假设验证基于优惠建议，则至少需要显示该，并且仍然处于活动状态。 优惠和投放假设验证通过&#x200B;**[!UICONTROL Measurement hypotheses]**&#x200B;文件夹创建，并基于假设验证模板。 但是，可以直接在投放中引用假设验证，或在活动开始之前引用活动。 在这种情况下，将根据执行设置(有关详细信息，请参阅[假设验证模板执行设置](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings))，在启动营销活动后自动计算假设验证。

## 在投放{#creating-a-hypothesis-on-the-fly-on-a-delivery}上快速创建假设验证

要在现有假设验证上创建投放，请应用以下流程：

>[!NOTE]
>
>此操作仅可用于挂起的投放。

1. 在Adobe Campaign树中，转到&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**。
1. 单击&#x200B;**[!UICONTROL New]**&#x200B;按钮或右键单击假设验证列表，然后在下拉列表中选择&#x200B;**[!UICONTROL New]**。

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 在“假设验证”窗口中，选择先前创建的模板(请参阅[假设验证模板](../../campaign/using/hypothesis-templates.md))。

   ![](assets/response_hypothesis_instance_creation_003.png)

   在选定模型中定义的假设验证上下文将显示在窗口中。

   >[!NOTE]
   >
   >在模板中定义且在此步骤中不可见的设置也会保留在内存中，并重新分配给正在进行的假设验证。

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 选择要为其创建投放的假设验证。

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 您可以通过编辑&#x200B;**[!UICONTROL General]**、**[!UICONTROL Transactions]**&#x200B;和&#x200B;**[!UICONTROL Scope]**&#x200B;选项卡来个性化您的假设验证。 有关详细信息，请参阅[创建假设验证模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 通过单击&#x200B;**[!UICONTROL Start]**&#x200B;开始假设验证。

   将自动创建工作流以执行测量。 名称会根据假设验证配置自动定义。

   >[!CAUTION]
   >
   >如果选中了&#x200B;**[!UICONTROL Keep execution workflow]**&#x200B;框，则可以访问此选项。\
   >仅当运行假设验证时出错时，必须出于调试目的激活此选项。 自动生成的工作流将保存在Adobe Campaign资源管理器的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]**&#x200B;文件夹中。
   > 
   >此外，不得修改自动生成的工作流。 在以后的计算中，任何最终的修改都不会考虑在其他地方。
   >
   >如果已选中此选项，请在执行该工作流后将其删除。

   ![](assets/response_hypothesis_instance_creation_006.png)

   计算完成后，测量指示器会自动更新。

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 如有必要，请更改设置并重新开始假设验证。

## 在活动投放{#referencing-a-hypothesis-in-a-campaign-delivery}中引用假设验证

您可以在营销活动中引用假设验证，然后再启动。 在这种情况下，根据假设验证模板中定义的执行设置，投放在发送后将自动启动。 要在投放中创建假设验证，请应用以下过程：

1. 根据您的需要，可以创建一个或多个&#x200B;**[!UICONTROL Delivery]**&#x200B;类型模板，如[本节](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)中所述
1. 创建营销活动和定位工作流。
1. 在投放窗口中，单击&#x200B;**[!UICONTROL Delivery measurement]**&#x200B;图标。
1. 选择假设验证模板(在模型中配置的查询显示在假设验证窗口中)。

   假设验证将根据模型中配置的日期(请参阅[假设验证模板执行设置](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings))在活动完成后自动计算。

   ![](assets/response_hypothesis_instance_creation_008.png)

## 为活动{#adding-a-default-hypothesis-to-deliveries-for-a-campaign}的投放添加默认假设验证

您可以直接在假设验证级别引用活动。 在这种情况下，假设验证将自动链接到在活动中创建的所有投放。 操作步骤：

1. 转到活动的&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。
1. 在测量部分，单击&#x200B;**[!UICONTROL Default hypotheses]**&#x200B;选项卡。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择假设验证模板。

   ![](assets/response_hypothesis_instance_creation_011.png)

   现在，基于此模板的假设验证将默认在活动的每个新投放中引用。

   ![](assets/response_hypothesis_instance_creation_012.png)

假设验证结果可在假设验证的&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Reactions]**&#x200B;选项卡中查看(请参阅[假设验证跟踪](../../campaign/using/hypothesis-tracking.md))

有关详细信息，还可以参阅[此示例](#example--creating-a-hypothesis-linked-to-a-delivery)。

## 在优惠{#creating-a-hypothesis-on-an-offer}上创建假设验证

在优惠建议上创建假设验证与在动态投放假设验证中创建类似。 只要假设验证处于活动状态，就可以执行优惠。 计算期间基于优惠建议。 当假设验证允许您将收件人链接到购买时，可能会被接受的优惠建议的状态会自动更改（有关详细信息，请参阅[Transactions](../../campaign/using/hypothesis-templates.md#transactions)）。

1. 创建一个或多个&#x200B;**[!UICONTROL Offer]**&#x200B;类型模型，如[本节](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)中所述。
1. 转到&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;节点。
1. 通过选择以前创建的模型创建&#x200B;**[!UICONTROL Offers]**&#x200B;类型假设验证。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中创建的查询将出现在窗口中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 选择要为其创建优惠的假设验证。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 根据需要优化查询。
1. 单击&#x200B;**[!UICONTROL Start]**&#x200B;以运行假设验证。
1. 假设验证结果可在其&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Reactions]**&#x200B;选项卡中查看(请参阅[假设验证跟踪](../../campaign/using/hypothesis-tracking.md))。

   在优惠上创建的假设验证在&#x200B;**[!UICONTROL Measurement]**&#x200B;选项卡中引用。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果在假设验证模板中启用了&#x200B;**[!UICONTROL Update offer proposition status]**&#x200B;选项，则优惠建议的状态会自动更改，从而提供有关活动影响的反馈（有关详细信息，请参阅[Transactions](../../campaign/using/hypothesis-templates.md#transactions)）。

## 示例：创建链接到投放{#example--creating-a-hypothesis-linked-to-a-delivery}的假设验证

在此示例中，我们要创建一个链接到投放的假设验证。 此假设验证将基于先前创建的模型（请参阅[此示例](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)）。 然后，我们将优化从模型继承的查询，以对购买表的特定文章进行假设验证。

1. 创建活动和投放(有关详细信息，请参阅[创建营销活动](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   在我们的示例中，我们将使用直接邮件类型投放。

1. 配置种子地址：之前创建的假设验证模板配置为在反应结果中考虑对照组。

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >有关详细信息，请参阅[定义对照组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

1. 打开&#x200B;**[!UICONTROL Direct mail delivery]**&#x200B;并单击&#x200B;**[!UICONTROL Delivery measurement]**&#x200B;图标，然后单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 从下拉式假设验证中选择之前创建的列表模板。

   ![](assets/response_hypothesis_delivery_example_004.png)

   将显示在模型中创建的查询。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 单击&#x200B;**[!UICONTROL Edit query...]**，然后输入查询将关注的产品来优化假设验证。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以检查假设验证是否已链接到活动的&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Measurement]**&#x200B;选项卡中的投放。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 启动定位工作流并运行必要的检查，直到活动完成（有关详细信息，请参阅[此部分](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)）。

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign树中，转到&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;节点以检查由假设验证计算的指示器。

   ![](assets/response_hypothesis_delivery_example_010.png)

