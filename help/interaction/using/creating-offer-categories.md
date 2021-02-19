---
solution: Campaign Classic
product: campaign
title: 创建优惠类别
description: 创建优惠类别
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# 创建优惠类别{#creating-offer-categories}

创建优惠类别只能在&#x200B;**[!UICONTROL Design]**&#x200B;环境中进行。 当包含的已创建/修改的优惠获得批准时，这些应用程序会自动部署在&#x200B;**[!UICONTROL Live]**&#x200B;环境中（即已提供）。 默认情况下，**[!UICONTROL Design]**&#x200B;环境包含接收所有优惠的类别。 可以创建子类别以将层次结构添加到目录优惠。

对于每个类别，您可以定义资格日期，即类别中包含的优惠可能不再显示给其目标的期间。 如果希望优惠引擎将特定类别的优惠选为优先级，则可以通过向类别添加相乘权重来增加给定时段的权重，以便更好地显示产品。

要创建其他类别，请应用以下步骤：

1. 转到&#x200B;**[!UICONTROL Offer catalog]**&#x200B;文件夹。

   ![](assets/offer_cat_create_001.png)

1. 右键单击并从下拉列表中选择&#x200B;**[!UICONTROL Create a new "Offer category" folder]**。

   ![](assets/offer_cat_create_002.png)

1. 重新命名类别。 以后可以使用&#x200B;**[!UICONTROL General]**&#x200B;选项卡编辑标签。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重复这些步骤，以创建所需数量的类别。

   之后，您可以根据需要：

   * 从&#x200B;**[!UICONTROL Eligibility]**&#x200B;选项卡分配资格日期。

      ![](assets/offer_cat_create_004.png)

   * 使用&#x200B;**[!UICONTROL Themes]**&#x200B;字段输入可用于从此类别中选择优惠的关键字。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >调用优惠引擎时，只会选择主题或类别与参数匹配的目录部分。

   * 通过&#x200B;**[!UICONTROL Multiplier weight]**&#x200B;字段暂时“提升”给定时段类别的优惠权重。

      ![](assets/offer_cat_create_006.png)

您可以在合格规则中包含的优惠的仪表板上查阅类别。 要视图它们，请单击&#x200B;**[!UICONTROL Schedule and eligibility rules of the offer]**&#x200B;链接。

![](assets/offer_create_006.png)

