---
product: campaign
title: 匿名互动
description: 匿名互动
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# 匿名互动{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png) 观看此内容 [视频](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) 大致了解如何将优惠提供给已识别和匿名目标。

## 为匿名交互定位和存储环境 {#targeting-and-storing-an-environment-for-anonymous-interactions}

默认情况下，交互附带预配置的环境，以定向收件人表（已识别的选件）。 如果要定位其他表（匿名选件的访客表或特定的收件人表），则需要使用目标映射向导创建环境。 有关此内容的更多信息，请参阅 [创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

通过映射创建向导创建匿名环境时， **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 框会在环境的 **[!UICONTROL General]** 选项卡。

此 **[!UICONTROL Targeting dimension]** 将自动完成。 默认情况下，该链接会链接到访客表。

此 **[!UICONTROL Visitor folder]** 字段。 自动完成以链接到 **[!UICONTROL Visitors]** 文件夹。 此字段允许您选择存储访客配置文件的位置。

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>如果要筛选多种类型的访客，例如，为一个或多个品牌提供的匿名优惠，则需要为每个品牌创建一个环境，并且 **[!UICONTROL Visitors]** 为每个环境键入文件夹。

## 匿名交互的优惠目录 {#offer-catalog-for-anonymous-interactions}

与叫客交互一样，入站交互也是在由类别和优惠组成的优惠目录中组织的。

要创建类别和空间，请应用与已识别访客相同的流程(请参阅 [创建优惠类别](../../interaction/using/creating-offer-categories.md) 和 [创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment))。

## 匿名访客 {#anonymous-visitors}

匿名访客在连接时可能会提交到Cookie识别流程。 此隐式识别基于访客的浏览器历史记录。

在此步骤中，将Cookie恢复的数据与数据库中的数据进行比较。 在一些情况下，访客会被识别（然后被隐式识别），而在其他情况下，访客不会被识别（因此保持匿名）。

要运行此分析，对于选件空间，请选中 **[!UICONTROL Implicitly identify the individual based on their browser history]** 选项。

![](assets/identification_anonymous_visitors.png)

## 处理未识别的匿名访客 {#processing-unidentified-anonymous-visitors}

经过分析后，如果未识别匿名访客，则可以将他们的数据存储在给定的空间中。 这样，您就可以根据指定的分类规则，提出专门针对此类访客的优惠建议。

如果没有允许您识别联系人的元素，或者如果您不想向可以隐式识别的联系人建议已识别的选件，则可以选择对匿名环境执行回退。

要执行此操作，请查看 **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**，然后在中指定专门为这些未识别的访客提供的环境 **[!UICONTROL Linked anonymous space]** 指定优惠空间时。

![](assets/anonymous_to_anonymous_environment.png)
