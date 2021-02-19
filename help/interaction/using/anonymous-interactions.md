---
solution: Campaign Classic
product: campaign
title: 匿名互动
description: 匿名互动
audience: interaction
content-type: reference
topic-tags: unitary-interactions
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---


# 匿名互动{#anonymous-interactions}

![](assets/do-not-localize/how-to-video.png) 观看此 [](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) 视频，了解如何将优惠交付给已识别和匿名目标。

## 定位和存储匿名交互的环境{#targeting-and-storing-an-environment-for-anonymous-interactions}

默认情况下，“交互”附带预配置的环境以目标收件人表(已标识的优惠)。 如果要目标另一个表(用于匿名优惠的访客表或特定收件人表)，则需要使用目标映射向导来创建环境。 有关详细信息，请参阅[创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

当您通过映射创建向导创建匿名环境时，**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;框会自动选中环境的&#x200B;**[!UICONTROL General]**&#x200B;选项卡。

**[!UICONTROL Targeting dimension]**&#x200B;会自动完成。 默认情况下，它链接到访客表。

出现&#x200B;**[!UICONTROL Visitor folder]**&#x200B;字段。 会自动完成链接至&#x200B;**[!UICONTROL Visitors]**&#x200B;文件夹的操作。 此字段允许您选择存储访客用户档案的位置。

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>如果要过滤几种类型的访客(例如，对于为一个或多个品牌显示的匿名优惠)，您需要为每个品牌创建一个环境，并为每个环境创建一个&#x200B;**[!UICONTROL Visitors]**&#x200B;类型文件夹。

## 优惠目录匿名交互{#offer-catalog-for-anonymous-interactions}

与出站交互一样，入站交互组织在由类别和优惠组成的优惠目录中。

要创建类别和空格，请应用与标识访客相同的流程(请参阅[创建优惠类别](../../interaction/using/creating-offer-categories.md)和[创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment))。

## 匿名访客{#anonymous-visitors}

匿名访客在连接时可能会提交到Cookie标识过程。 这种隐式识别是基于访客的浏览器历史记录。

在此步骤中，将比较由Cookies恢复的数据与数据库中的数据。 在某些情况下，访客是被认可的（然后隐含地被认出），在其他情况下，他是不被认可的（因此保持匿名）。

要运行此分析，请选中&#x200B;**[!UICONTROL Implicitly identify the individual based on their browser history]**&#x200B;选项作为优惠空间。

![](assets/identification_anonymous_visitors.png)

## 正在处理未识别的匿名访客{#processing-unidentified-anonymous-visitors}

分析后，如果未识别匿名访客，则可以将其数据存储在给定空间中。 这将允许您建议专门针对此类访客的优惠，与指定类型规则匹配。

如果没有允许您标识联系人的元素，或者如果您不希望向可以隐式标识的联系人建议已标识的优惠，则可以选择对匿名环境进行回退。

要执行此操作，请检查&#x200B;**[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**，然后在指定环境时，在&#x200B;**[!UICONTROL Linked anonymous space]**&#x200B;中指定专用于这些未识别访客的优惠空间。

![](assets/anonymous_to_anonymous_environment.png)

