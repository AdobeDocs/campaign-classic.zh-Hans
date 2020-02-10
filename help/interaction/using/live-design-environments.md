---
title: 实时／设计环境
seo-title: 实时／设计环境
description: 实时／设计环境
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 实时／设计环境{#live-design-environments}

## 工作原理 {#operating-principle}

交互操作有两种类型的选件环境：

* **[!UICONTROL Design]** 包含正在编辑并可以更改的选件的选件环境。 这些优惠尚未通过审批周期，也未交付给联系人。
* **[!UICONTROL Live]** 在向联系人展示已批准的选件时包含这些选件的选件环境。 此环境中的选件是只读的。

![](assets/offer_environments_overview_001.png)

每个 **[!UICONTROL Design]** 环境都与一个环境相 **[!UICONTROL Live]** 关联。 当选件完成时，其内容和资格规则将受到批准周期的约束。 完成此循环后，相关的优惠会自动部署到该环 **[!UICONTROL Live]** 境。 从此开始，它将可供交付。

默认情况下，交互包含一 **[!UICONTROL Design]** 个环境和一 **[!UICONTROL Live]** 个链接到该环境。 这两个环境都预配置为针对现成的收件人表。

>[!NOTE]
>
>要定位另一个表（匿名选件的访客表或特定收件人表），您需要使用目标映射向导来创建环境。 有关详细信息，请参阅 [创建选件环境](#creating-an-offer-environment)。

![](assets/offer_environments_overview_002.png)

选件经理和交付经理可以访问不同的环境视图。 交付经理只能查看选件 **[!UICONTROL Live]** 环境并使用选件来交付它们。 选件管理者可以查看和更 **[!UICONTROL Design]** 改环境并查看环 **[!UICONTROL Live]** 境。 For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).

## 创建选件环境 {#creating-an-offer-environment}

默认情况下，交互附带一个预配置的环境，用于定位收件人表（已识别的选件）。 如果您希望以其他表（匿名选件的访客表或特定收件人表）为目标，则需要应用以下配置：

1. 将光标放在 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** >节 **[!UICONTROL Delivery mappings]** 点上。 右键单击要使用的交付映射(如果&#x200B;**[!UICONTROL Visitors]** 要使用匿名选件)，然后选择 **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**。

   ![](assets/offer_env_anonymous_001.png)

1. 单 **[!UICONTROL Next]** 击以继续进入向导中的下一个屏幕，选中该框并 **[!UICONTROL Generate a storage schema for propositions]** 单击 **[!UICONTROL Save]**。

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果该框已选中，请取消选中它，然后重新选中它。

1. Adobe Campaign使用先前启用的目&#x200B;**[!UICONTROL Design]** 标映射中 **[!UICONTROL Live]** 的定位信息创建两个环境（和）。 该环境预配置了定位信息。

   如果已激活映 **[!UICONTROL Visitor]** 射，该框 **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 将自动选中该环境的选项 **[!UICONTROL General]** 卡。

   此选项允许您激活特定于匿名交互的函数，尤其是在配置环境提供空间时。 您还可以配置选项，以便从“已识别”环境切换到“匿名”环境。

   例如，您可以将收件人环境优惠空间（已识别的联系人）与与访客环境（未识别的联系人）匹配的优惠空间链接。 这样，根据是否识别联系人，将向联系人提供不同的优惠。 有关此内容的详细信息，请参阅 [创建选件空间](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>有关入站渠道上的匿名交互的详细信息，请参阅匿名 [交互](../../interaction/using/anonymous-interactions.md)。

