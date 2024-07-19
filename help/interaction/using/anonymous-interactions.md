---
product: campaign
title: 匿名互动
description: 匿名互动
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# 匿名互动{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png)观看此[视频](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com)，大致了解如何将优惠提供给已识别和匿名目标。

## 为匿名交互定位和存储环境 {#targeting-and-storing-an-environment-for-anonymous-interactions}

默认情况下，交互附带预配置的环境，以定向收件人表（已识别的选件）。 如果要定位其他表（匿名选件的访客表或特定的收件人表），则需要使用目标映射向导创建环境。 有关此内容的详细信息，请参阅[创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

通过映射创建向导创建匿名环境时，会自动在环境的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中选中&#x200B;**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;框。

**[!UICONTROL Targeting dimension]**&#x200B;自动完成。 默认情况下，该链接会链接到访客表。

出现&#x200B;**[!UICONTROL Visitor folder]**&#x200B;字段。 自动完成以链接到&#x200B;**[!UICONTROL Visitors]**&#x200B;文件夹。 此字段允许您选择存储访客配置文件的位置。

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>如果要过滤多种类型的访客，例如为一个或多个品牌提供的匿名优惠，则需要为每个品牌创建一个环境，并为每个环境创建一个&#x200B;**[!UICONTROL Visitors]**&#x200B;类型文件夹。

## 匿名交互的优惠目录 {#offer-catalog-for-anonymous-interactions}

与叫客交互一样，入站交互也会在优惠目录中组织，该优惠目录由类别和优惠组成。

要创建类别和空间，请应用与已识别访客相同的流程（请参阅[创建优惠类别](../../interaction/using/creating-offer-categories.md)和[创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)）。

## 匿名访客 {#anonymous-visitors}

匿名访客在连接时可能会提交到Cookie识别流程。 此隐式识别基于访客的浏览器历史记录。

在此步骤中，将比较由Cookie恢复的数据与数据库中的数据。 在一些情况下，访客会被识别（然后被隐式识别），而在其他情况下，访客不会被识别（因此保持匿名）。

要运行此分析，请为优惠空间选中&#x200B;**[!UICONTROL Implicitly identify the individual based on their browser history]**&#x200B;选项。

![](assets/identification_anonymous_visitors.png)

## 处理未识别的匿名访客 {#processing-unidentified-anonymous-visitors}

经过分析后，如果匿名访客未识别，则可以将他们的数据存储在给定空间中。 这样，您就可以根据指定的分类规则，提出专门针对此类访客的优惠建议。

如果没有允许您识别联系人的元素，或者如果您不想向可以隐式识别的联系人建议已识别的优惠，则可以选择对匿名环境进行替代。

为此，请选中&#x200B;**[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**，然后在指定选件空间时在&#x200B;**[!UICONTROL Linked anonymous space]**&#x200B;中指定专用于这些未识别访客的环境。

![](assets/anonymous_to_anonymous_environment.png)
