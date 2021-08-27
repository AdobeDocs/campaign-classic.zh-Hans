---
product: campaign
title: 实时/设计环境
description: 实时/设计环境
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# 实时/设计环境{#live-design-environments}

![](../../assets/v7-only.svg)

## 操作原则 {#operating-principle}

交互可与两种类型的选件环境进行操作：

* **[!UICONTROL Design]** 包含正在编辑且可更改的选件的选件环境。这些选件尚未通过批准周期，也未交付给联系人。
* **[!UICONTROL Live]** 在向联系人显示已批准选件时包含这些选件的选件环境。此环境中的选件为只读选件。

![](assets/offer_environments_overview_001.png)

每个&#x200B;**[!UICONTROL Design]**&#x200B;环境均链接到&#x200B;**[!UICONTROL Live]**&#x200B;环境。 选件完成后，其内容和资格规则将受到批准周期的约束。 完成此周期后，相关选件会自动部署到&#x200B;**[!UICONTROL Live]**&#x200B;环境。 从此刻起，它将可供投放。

默认情况下，交互会附带一个&#x200B;**[!UICONTROL Design]**&#x200B;环境和一个与之链接的&#x200B;**[!UICONTROL Live]**&#x200B;环境。 这两个环境都已预配置为定向即装即用的收件人表。

>[!NOTE]
>
>要定位另一个表（匿名选件的访客表或特定的收件人表），您需要使用目标映射向导来创建环境。 有关更多信息，请参阅[创建选件环境](#creating-an-offer-environment)。

![](assets/offer_environments_overview_002.png)

选件管理器和交付管理器可以访问环境的不同视图。 投放管理器只能查看&#x200B;**[!UICONTROL Live]**&#x200B;选件环境并使用选件进行投放。 选件管理器可以查看和更改&#x200B;**[!UICONTROL Design]**&#x200B;环境，并查看&#x200B;**[!UICONTROL Live]**&#x200B;环境。 有关更多信息，请参阅[运算符配置文件](../../interaction/using/operator-profiles.md)。

## 创建优惠环境 {#creating-an-offer-environment}

默认情况下，交互会附带一个预配置的环境，以定位收件人表（已识别的选件）。 如果您希望定位其他表（匿名选件的访客表或特定收件人表），则需要应用以下配置：

1. 将光标放在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**&#x200B;节点上。 右键单击要使用的投放映射（如果要使用匿名选件，请单击&#x200B;**[!UICONTROL Visitors]**），然后选择&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**。

   ![](assets/offer_env_anonymous_001.png)

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;以继续进入向导的下一个屏幕，选中&#x200B;**[!UICONTROL Generate a storage schema for propositions]**&#x200B;框，然后单击&#x200B;**[!UICONTROL Save]**。

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果复选框已选中，请取消选中该框，然后重新选中该框。

1. Adobe Campaign使用先前启用的目标映射中的定位信息创建两个环境（**[!UICONTROL Design]**&#x200B;和&#x200B;**[!UICONTROL Live]**）。 环境已预配置了定位信息。

   如果已激活&#x200B;**[!UICONTROL Visitor]**&#x200B;映射，则在环境的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中会自动选中&#x200B;**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;框。

   利用此选项，可激活特定于匿名交互的函数，尤其是在配置环境选件空间时。 您还可以配置选项，以便从“已识别”环境切换到“匿名”环境。

   例如，您可以将收件人环境选件空间（已识别的联系人）与与访客环境（未识别的联系人）匹配的选件空间链接起来。 这样，联系人就可以获得不同的选件，具体取决于他们是否被识别。 有关更多信息，请参阅[创建选件空间](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>有关入站渠道上匿名交互的更多信息，请参阅[匿名交互](../../interaction/using/anonymous-interactions.md)。
