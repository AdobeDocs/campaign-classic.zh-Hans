---
product: campaign
title: 创建优惠类别
description: 创建优惠类别
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---

# 创建优惠类别{#creating-offer-categories}

选件类别的创建只能在&#x200B;**[!UICONTROL Design]**&#x200B;环境中进行。 当包含的已创建/修改选件获得批准时，这些选件会在&#x200B;**[!UICONTROL Live]**&#x200B;环境中自动部署（即可用）。 默认情况下，**[!UICONTROL Design]**&#x200B;环境包含用于接收所有选件的类别。 可以创建子类别以将层次结构添加到目录选件中。

对于每个类别，您可以定义资格日期，即类别中包含的选件可能不再呈现给其目标的时间段。 如果您希望选件引擎将特定类别中的选件作为优先级来选择，以便更好地显示产品，例如，您可以通过向类别中添加乘数来增加其给定期间的权重。

要创建其他类别，请应用以下步骤：

1. 转到&#x200B;**[!UICONTROL Offer catalog]**&#x200B;文件夹。

   ![](assets/offer_cat_create_001.png)

1. 右键单击并从下拉列表中选择&#x200B;**[!UICONTROL Create a new "Offer category" folder]**。

   ![](assets/offer_cat_create_002.png)

1. 重新命名类别。 您稍后可以使用&#x200B;**[!UICONTROL General]**&#x200B;选项卡编辑标签。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重复这些步骤以创建所需数量的类别。

   之后，您可以根据需要：

   * 从&#x200B;**[!UICONTROL Eligibility]**&#x200B;选项卡分配资格日期。

      ![](assets/offer_cat_create_004.png)

   * 使用&#x200B;**[!UICONTROL Themes]**&#x200B;字段输入可用于从此类别中选择选件的关键字。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >调用选件引擎时，只会选择目录中主题或类别与参数匹配的部分。

   * 通过&#x200B;**[!UICONTROL Multiplier weight]**&#x200B;字段暂时“提升”给定时段内类别的选件权重。

      ![](assets/offer_cat_create_006.png)

资格规则的回顾可在类别中包含的选件的仪表板中找到。 要查看它们，请单击&#x200B;**[!UICONTROL Schedule and eligibility rules of the offer]**&#x200B;链接。

![](assets/offer_create_006.png)
