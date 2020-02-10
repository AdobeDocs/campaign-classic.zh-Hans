---
title: 创建选件类别
seo-title: 创建选件类别
description: 创建选件类别
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 创建选件类别{#creating-offer-categories}

只能在环境中创建选件类 **[!UICONTROL Design]** 别。 当所包含的已创建／修 **[!UICONTROL Live]** 改选件获得批准时，这些选件将自动部署在环境中（即提供）。 默认情况下，该环 **[!UICONTROL Design]** 境包含一个类别，用于接收所有选件。 可以创建子类别，以向目录选件添加层次结构。

对于每个类别，您可以定义资格日期，即类别中包含的选件可能不再呈现给其目标的期限。 如果您希望某个特定类别的选件被选件引擎选为优先级，例如，为了更好地展示产品，您可以通过向该类别添加乘权来增加给定期间的权重。

要创建其他类别，请应用以下步骤：

1. 转到文件 **[!UICONTROL Offer catalog]** 夹。

   ![](assets/offer_cat_create_001.png)

1. 右键单击并 **[!UICONTROL Create a new "Offer category" folder]** 从下拉列表中选择。

   ![](assets/offer_cat_create_002.png)

1. 重新命名类别。 您以后可以使用选项卡编辑标 **[!UICONTROL General]** 签。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重复这些步骤以创建所需数量的类别。

   之后，您可以根据需要：

   * 从选项卡中分配资格 **[!UICONTROL Eligibility]** 日期。

      ![](assets/offer_cat_create_004.png)

   * 使用字段输入可用于从此类别中选择选件的关 **[!UICONTROL Themes]** 键字。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >调用选件引擎时，只会选择主题或类别与参数匹配的目录部分。

   * 您可以通过字段临时“提升”某个类别在给定时间段内的优惠权重。 **[!UICONTROL Multiplier weight]**

      ![](assets/offer_cat_create_006.png)

在类别中包含的选件的功能板上可查看资格规则的更新。 要查看它们，请单击链 **[!UICONTROL Schedule and eligibility rules of the offer]** 接。

![](assets/offer_create_006.png)

