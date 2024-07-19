---
product: campaign
title: 实时/设计环境
description: 实时/设计环境
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# 实时/设计环境{#live-design-environments}



## 操作原则 {#operating-principle}

交互操作有两种类型的选件环境：

* **[!UICONTROL Design]**&#x200B;选件环境，其中包含正在编辑且可更改的选件。 这些选件尚未经过批准周期，不会发送给联系人。
* **[!UICONTROL Live]**&#x200B;优惠环境包含向联系人呈现的已批准优惠。 此环境中的选件处于只读状态。

![](assets/offer_environments_overview_001.png)

每个&#x200B;**[!UICONTROL Design]**&#x200B;环境都链接到&#x200B;**[!UICONTROL Live]**&#x200B;环境。 选件完成后，其内容和资格规则需要经过批准周期。 此周期完成后，相关选件将自动部署到&#x200B;**[!UICONTROL Live]**&#x200B;环境。 从现在开始，它将可供交付。

默认情况下，交互包含一个&#x200B;**[!UICONTROL Design]**&#x200B;环境和一个与之关联的&#x200B;**[!UICONTROL Live]**&#x200B;环境。 这两个环境都已预配置为定位内置的收件人表。

>[!NOTE]
>
>要定位其他表（匿名选件的访客表或特定的收件人表），您需要使用目标映射向导创建环境。 有关详细信息，请参阅[创建优惠环境](#creating-an-offer-environment)。

![](assets/offer_environments_overview_002.png)

优惠经理和投放经理可以访问环境的不同视图。 投放经理只能查看&#x200B;**[!UICONTROL Live]**&#x200B;优惠环境并使用优惠进行投放。 选件经理可以查看和更改&#x200B;**[!UICONTROL Design]**&#x200B;环境以及查看&#x200B;**[!UICONTROL Live]**&#x200B;环境。 有关详细信息，请参阅[操作员配置文件](../../interaction/using/operator-profiles.md)。

## 创建优惠环境 {#creating-an-offer-environment}

默认情况下，交互附带预配置的环境，以定向收件人表（已识别的选件）。 如果要定位另一个表（匿名选件的访客表或特定的收件人表），则需要应用以下配置：

1. 将光标置于&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**&#x200B;节点上。 右键单击要使用的投放映射（如果要使用匿名优惠，则为&#x200B;**[!UICONTROL Visitors]**），然后选择&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**。

   ![](assets/offer_env_anonymous_001.png)

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;以进入向导中的下一个屏幕，选中&#x200B;**[!UICONTROL Generate a storage schema for propositions]**&#x200B;框并单击&#x200B;**[!UICONTROL Save]**。

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果该框已被选中，请取消选中，然后重新选中。

1. Adobe Campaign使用以前启用的目标映射中的定位信息创建两个环境（**[!UICONTROL Design]**&#x200B;和&#x200B;**[!UICONTROL Live]** ）。 环境已预先配置了定位信息。

   如果已激活&#x200B;**[!UICONTROL Visitor]**&#x200B;映射，则会在环境的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中自动选中&#x200B;**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;框。

   此选项允许您激活特定于匿名交互的功能，尤其是在配置环境优惠空间时。 您还可以配置相应的选项，以便从“已识别”环境切换到“匿名”环境。

   例如，您可以将收件人环境选件空间（已识别的联系人）链接到与访客环境（未识别的联系人）匹配的选件空间。 这样，根据此联系人是否识别，将向联系人提供不同的选件。 有关详细信息，请参阅[创建优惠空间](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>有关入站渠道上的匿名交互的详细信息，请参阅[匿名交互](../../interaction/using/anonymous-interactions.md)。
