---
product: campaign
title: 创建优惠类别
description: 创建优惠类别
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 创建优惠类别{#creating-offer-categories}



优惠类别的创建只能在&#x200B;**[!UICONTROL Design]**&#x200B;环境中进行。 当创建/修改的选件获得批准时，这些选件将自动部署在&#x200B;**[!UICONTROL Live]**&#x200B;环境中（即可用）。 默认情况下，**[!UICONTROL Design]**&#x200B;环境包含接收所有选件的类别。 可以创建子类别以将层次结构添加到目录选件。

对于每个类别，您可以定义资格日期，即在超过该日期后，类别中包含的优惠将不再呈现给其目标。 如果您希望优惠引擎选择特定类别的优惠作为优先级，以便更好地展示产品，例如，您可以通过为类别添加相乘权重来增加给定时段的权重。

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

   此后，您可以根据需要执行以下操作：

   * 从&#x200B;**[!UICONTROL Eligibility]**&#x200B;选项卡分配资格日期。

     ![](assets/offer_cat_create_004.png)

   * 使用&#x200B;**[!UICONTROL Themes]**&#x200B;字段输入可用于从该类别中选择优惠的关键字。

     ![](assets/offer_cat_create_005.png)

     >[!NOTE]
     >
     >在调用优惠引擎时，仅选择目录中与主题或类别匹配参数的部分。

   * 通过&#x200B;**[!UICONTROL Multiplier weight]**&#x200B;字段在给定时间段内临时“提升”类别的选件权重。

     ![](assets/offer_cat_create_006.png)

类别中包含的优惠信息板上提供了资格规则的回顾。 要查看其内容，请单击&#x200B;**[!UICONTROL Schedule and eligibility rules of the offer]**&#x200B;链接。

![](assets/offer_create_006.png)
