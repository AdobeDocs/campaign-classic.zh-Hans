---
product: campaign
title: 创建优惠类别
description: 创建优惠类别
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---

# 创建优惠类别{#creating-offer-categories}

![](../../assets/v7-only.svg)

选件类别的创建只能在 **[!UICONTROL Design]** 环境。 它们会自动部署在 **[!UICONTROL Live]** 环境（即，提供）。 默认情况下， **[!UICONTROL Design]** 环境包含用于接收所有选件的类别。 可以创建子类别以将层次结构添加到目录选件中。

对于每个类别，您可以定义资格日期，即类别中包含的选件可能不再呈现给其目标的时间段。 如果您希望选件引擎将特定类别中的选件作为优先级来选择，以便更好地显示产品，例如，您可以通过向类别中添加乘数来增加其给定期间的权重。

要创建其他类别，请应用以下步骤：

1. 转到 **[!UICONTROL Offer catalog]** 文件夹。

   ![](assets/offer_cat_create_001.png)

1. 右键单击并选择 **[!UICONTROL Create a new "Offer category" folder]** 从下拉列表中。

   ![](assets/offer_cat_create_002.png)

1. 重新命名类别。 您稍后可以使用 **[!UICONTROL General]** 选项卡。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重复这些步骤以创建所需数量的类别。

   之后，您可以根据需要：

   * 分配 **[!UICONTROL Eligibility]** 选项卡。

      ![](assets/offer_cat_create_004.png)

   * 使用 **[!UICONTROL Themes]** 字段。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >调用选件引擎时，只会选择目录中主题或类别与参数匹配的部分。

   * 通过 **[!UICONTROL Multiplier weight]** 字段。

      ![](assets/offer_cat_create_006.png)

资格规则的回顾可在类别中包含的选件的仪表板中找到。 要查看这些区段，请单击 **[!UICONTROL Schedule and eligibility rules of the offer]** 链接。

![](assets/offer_create_006.png)
