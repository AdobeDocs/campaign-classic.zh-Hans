---
title: 实时/设计环境
seo-title: 实时/设计环境
description: 实时/设计环境
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---


# 实时/设计环境{#live-design-environments}

## 工作原理 {#operating-principle}

交互操作有两种类型的优惠环境:

* **[!UICONTROL Design]** 优惠环境，包括正在编辑的优惠，可以更改。 这些优惠尚未通过审批周期，也未送达联系人。
* **[!UICONTROL Live]** 优惠环境，在向联系人展示时包括已批准的优惠。 此环境中的优惠是只读的。

![](assets/offer_environments_overview_001.png)

每个 **[!UICONTROL Design]** 环境都链接到 **[!UICONTROL Live]** 环境。 优惠完成后，其内容和合格规则将受到批准周期的约束。 完成此循环后，相关优惠将自动部署到该 **[!UICONTROL Live]** 环境。 从此刻起，它将可用于投放。

默认情况下，“交互”附带 **[!UICONTROL Design]** 一个环境和 **[!UICONTROL Live]** 一个链接到它的环境。 两个环境都预配置为目标现成的收件人表。

>[!NOTE]
>
>要目标其他表(匿名优惠的访客表或特定收件人表)，您需要使用目标映射向导来创建环境。 有关此内容的详细信息，请参 [阅创建优惠环境](#creating-an-offer-environment)。

![](assets/offer_environments_overview_002.png)

优惠经理和投放经理有权访问环境的不同视图。 投放经理只能视图 **[!UICONTROL Live]** 优惠环境并使用优惠来提供。 优惠管理者可以视图和更改 **[!UICONTROL Design]** 环境并视图 **[!UICONTROL Live]** 环境。 For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).

## 创建优惠环境 {#creating-an-offer-environment}

默认情况下，“交互”附带预配置的环境来目标收件人表(标识的优惠)。 如果要目标另一个表(匿名优惠的访客表或特定收件人表)，您需要应用以下配置：

1. 将光标放在 **[!UICONTROL Administration]** > > **[!UICONTROL Campaign management]** 节 **[!UICONTROL Delivery mappings]** 点上。 右键单击要使用的投放映射(如&#x200B;**[!UICONTROL Visitors]** 果要使用匿名优惠)，然后选择 **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**。

   ![](assets/offer_env_anonymous_001.png)

1. 单 **[!UICONTROL Next]** 击以继续进入向导的下一个屏幕，选中该 **[!UICONTROL Generate a storage schema for propositions]** 框并单击 **[!UICONTROL Save]**。

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果该框已选中，请取消选中它，然后重新选中它。

1. Adobe Campaign创建两个环境(**[!UICONTROL Design]** 和 **[!UICONTROL Live]** )，其中包含先前启用的目标映射的定位信息。 环境预配置了定位信息。

   如果已激活 **[!UICONTROL Visitor]** 映射， **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 则环境选项卡中会自动选中该 **[!UICONTROL General]** 框。

   通过此选项，可激活特定于匿名交互的函数，尤其是在配置环境优惠空间时。 您还可以配置选项，允许您从“已识别”环境切换为“匿名”环境。

   例如，您可以将收件人环境优惠空间（已标识联系人）与与访客环境（未标识的联系人）匹配的优惠空间链接。 这样，根据是否识别了联系人，将向联系人提供不同的优惠。 有关此内容的详细信息，请参阅 [创建优惠空间](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>有关入站渠道上的匿名交互的更多信息，请参阅 [匿名交互](../../interaction/using/anonymous-interactions.md)。

