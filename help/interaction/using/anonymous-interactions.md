---
title: 匿名互动
seo-title: 匿名互动
description: 匿名互动
seo-description: null
page-status-flag: never-activated
uuid: 6e28e8a4-8d2f-4747-8dd0-680fbf02b25d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 3fd7a1ef-b0e2-4a7e-9e36-044d997db785
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8e37be4f764feadb49c70a9d598f8f3b8f864380

---


# 匿名互动{#anonymous-interactions}

观看此 [视频](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) ，了解如何向已识别和匿名目标提供优惠。

## 定位和存储匿名交互环境 {#targeting-and-storing-an-environment-for-anonymous-interactions}

默认情况下，交互附带一个预配置的环境，用于定位收件人表（已识别的选件）。 如果要将另一个表（匿名选件的访客表或特定收件人表）定位，则需要使用目标映射向导来创建环境。 有关此内容的详细信息，请参 [阅创建选件环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

当您通过映射创建向导创建匿名环境时，该 **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 框会自动选中该环境的选项卡中的 **[!UICONTROL General]** 框。

此操 **[!UICONTROL Targeting dimension]** 作将自动完成。 默认情况下，它链接到访客表。

此时将 **[!UICONTROL Visitor folder]** 显示该字段。 自动完成链接到文件夹的 **[!UICONTROL Visitors]** 操作。 通过此字段，您可以选择存储访客资料的位置。

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>如果要过滤几种类型的访客，例如，对于为一个或多个品牌提供的匿名选件，您需要为每个品牌创建一个环境，并为每个环境创建一个 **[!UICONTROL Visitors]** 类型文件夹。

## 提供用于匿名交互的目录 {#offer-catalog-for-anonymous-interactions}

与出站交互一样，入站交互在由类别和选件组成的选件目录中进行组织。

要创建类别和空间，请应用与标识访客相同的流程(请参阅创建 [选件类别](../../interaction/using/creating-offer-categories.md)[和创建选件环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment))。

## 匿名访客 {#anonymous-visitors}

匿名访客在进行连接时可能会被提交到cookie识别流程。 这种隐含的识别基于访客的浏览器历史记录。

在此步骤中，将比较由cookies恢复的数据与数据库中的数据。 在某些情况下，访客会被识别（然后隐含地被识别），而在其他情况下，访客不会被识别（因此保持匿名）。

要运行此分析，请选中选件空间的选 **[!UICONTROL Implicitly identify the individual based on their browser history]** 项。

![](assets/identification_anonymous_visitors.png)

## 处理身份不明的匿名访客 {#processing-unidentified-anonymous-visitors}

分析后，如果未识别匿名访客，则可以将其数据存储在给定空间中。 这样，您就可以推荐专门针对此类访客的优惠信息，这与指定的排版规则相匹配。

如果没有允许您识别联系人的元素，或者您不希望向可以隐式识别的联系人推荐已识别的选件，则可以选择对匿名环境进行备份。

要执行此操作，请选 **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**&#x200B;中，然后在指定选件空间时指定这些身份不明的访 **[!UICONTROL Linked anonymous space]** 客专用的环境。

![](assets/anonymous_to_anonymous_environment.png)

