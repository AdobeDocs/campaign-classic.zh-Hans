---
solution: Campaign Classic
product: campaign
title: 实时/设计环境
description: 实时/设计环境
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---


# 实时/设计环境{#live-design-environments}

## 工作原理 {#operating-principle}

交互操作有两种类型的优惠环境:

* **[!UICONTROL Design]** 优惠环境，包括正在编辑且可以更改的优惠。这些优惠尚未通过审批周期，也未送达联系人。
* **[!UICONTROL Live]** 优惠环境，在向联系人显示批准的优惠时，包括这些。此环境中的优惠为只读。

![](assets/offer_environments_overview_001.png)

每个&#x200B;**[!UICONTROL Design]**&#x200B;环境都链接到&#x200B;**[!UICONTROL Live]**&#x200B;环境。 优惠完成后，其内容和合格规则将受到批准周期的约束。 完成此周期后，相关优惠将自动部署到&#x200B;**[!UICONTROL Live]**&#x200B;环境。 从现在开始，它将可用于投放。

默认情况下，“交互”附带一个&#x200B;**[!UICONTROL Design]**&#x200B;环境和一个链接到它的&#x200B;**[!UICONTROL Live]**&#x200B;环境。 这两个环境都已预配置为目标现成的收件人表。

>[!NOTE]
>
>要目标其他表(用于匿名优惠的访客表或特定收件人表)，您需要使用目标映射向导来创建环境。 有关详细信息，请参阅[创建优惠环境](#creating-an-offer-environment)。

![](assets/offer_environments_overview_002.png)

优惠经理和投放经理可以访问环境的不同视图。 投放管理者只能视图&#x200B;**[!UICONTROL Live]**&#x200B;优惠环境，并使用优惠来提供。 优惠管理器可以视图和更改&#x200B;**[!UICONTROL Design]**&#x200B;环境，并视图&#x200B;**[!UICONTROL Live]**&#x200B;环境。 有关详细信息，请参阅[运算符用户档案](../../interaction/using/operator-profiles.md)。

## 创建优惠环境{#creating-an-offer-environment}

默认情况下，“交互”附带预配置的环境以目标收件人表(已标识的优惠)。 如果要目标另一个表(匿名优惠的访客表或特定收件人表)，您需要应用以下配置：

1. 将光标放在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**&#x200B;节点上。 右键单击要使用的投放映射(如果要使用匿名优惠，请&#x200B;**[!UICONTROL Visitors]**)，然后选择&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**。

   ![](assets/offer_env_anonymous_001.png)

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;进入向导的下一个屏幕，选中&#x200B;**[!UICONTROL Generate a storage schema for propositions]**&#x200B;框，然后单击&#x200B;**[!UICONTROL Save]**。

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果该框已选中，请取消选中它，然后重新选中它。

1. Adobe Campaign创建两个环境（**[!UICONTROL Design]**&#x200B;和&#x200B;**[!UICONTROL Live]**），其中包含先前启用的目标映射的定位信息。 环境预配置了定位信息。

   如果已激活&#x200B;**[!UICONTROL Visitor]**&#x200B;映射，则会在环境的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中自动选中&#x200B;**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;框。

   此选项允许您激活特定于匿名交互的函数，尤其是在配置环境优惠空间时。 您还可以配置选项，允许您从“已识别”环境切换到“匿名”环境。

   例如，您可以将收件人环境优惠空间（已标识联系人）与与访客环境（未标识联系人）匹配的优惠空间链接。 这样，根据是否识别了联系人，将向联系人提供不同的优惠。 有关详细信息，请参阅[创建优惠空间](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>有关入站渠道上的匿名交互的详细信息，请参阅[匿名交互](../../interaction/using/anonymous-interactions.md)。

