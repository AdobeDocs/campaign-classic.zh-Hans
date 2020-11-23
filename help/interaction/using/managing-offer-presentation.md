---
solution: Campaign Classic
product: campaign
title: 管理优惠演示
description: 管理优惠演示
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---


# 管理优惠演示{#managing-offer-presentation}

## 推荐规则概述 {#presentation-rules-overview}

通过交互，您可以使用优惠建议控制推荐规则流。 这些规则是特定于交互的类型规则。 它们允许您根据已经向优惠提出的建议的历史来排除收件人。 它们在环境中被引用

## 创建和引用优惠推荐规则 {#creating-and-referencing-an-offer-presentation-rule}

1. 转到> **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** 节 **[!UICONTROL Typology rules]** 点。
1. 创建类型规则并选择 **[!UICONTROL Offer presentation]** 类型。

   ![](assets/offer_typology_001.png)

1. 指定应用规则的渠道。

   ![](assets/offer_typology_002.png)

1. 配置规则的应用程序条件。 有关此内容的详细信息，请参阅 [推荐规则设置](#presentation-rule-settings)。
1. 转到> **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** node并创 **[!UICONTROL Typologies]** 建将所有类型规则分组 **[!UICONTROL Offer presentation]** 的类型学。

   ![](assets/offer_typology_003.png)

1. 创建字体后，将光标放在类型规则上，并将它们分组到您刚刚创建的字体中。

   ![](assets/offer_typology_004.png)

1. 在优惠环境中，使用下拉式列表引用类型学。

   ![](assets/offer_typology_005.png)

## 推荐规则设置 {#presentation-rule-settings}

### 应用程序条件 {#application-criteria-}

选项卡中提供的应 **[!UICONTROL General]** 用程序条件允许您指定推荐规则将应用到的优惠。 为此，您需要创建查询并选择相关优惠，如下所述。

1. 在您的类型规则中，单 **[!UICONTROL Edit the rule application conditions...]** 击链接以创建查询。

   ![](assets/offer_typology_006.png)

1. 在“查询”窗口中，您可以对要应用类型规则的优惠应用过滤器。

   例如，您可以选择优惠类别。

   ![](assets/offer_typology_008.png)

### 优惠维 {#offer-dimensions}

在选 **[!UICONTROL Offer presentation]** 项卡中，必须为推荐规则指定与在环境中配置的维相同的维。

与 **[!UICONTROL Targeting dimension]** 收件人表重合(默认情况下：nms:收件人)，将接收优惠建议。 该 **[!UICONTROL Storage dimension]** 表与包含链接到定位维度的命题历史记录（默认情况下：nms:postitionRcp）的表重合。

![](assets/offer_typology_009.png)

>[!NOTE]
>
>您还可以使用非标准表。 如果要使用特定定位维度，您需要创建表以及使用目标映射的专用环境。 有关此内容的详细信息，请参 [阅创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

### 期间 {#period}

这是开始在优惠演示日期的滑动时段。 它为优惠建议的有效性设置时间限制。 该规则不适用于超过此期限的优惠建议。

期间开始 **在提议日** 期前的n天结束，在 **之后的** n天结束，其 **中n** 与在字段中输入的 **[!UICONTROL Period considered]** 数字相对应：

* 对于入站空间，提议日期是优惠演示日期。
* 对于出站空间，提案日期是投放联系日期(例如，在定位工作流中输入的投放日期)。

使用箭头更改天数或直接输入句点（例如“2d 6h”）。

![](assets/offer_typology_010.png)

### 命题数 {#number-of-propositions}

可以设置在排除相关优惠之前可以提出的最大数目。

使用箭头更改优惠建议数。

![](assets/offer_typology_011.png)

## 定义命题和收件人 {#defining-propositions-and-recipients}

在该 **[!UICONTROL Propositions to count]** 部分中，您可以指定收件人和主张，如果优惠在主张历史记录中出现一定次数，则这将导致排除在选项卡 **[!UICONTROL General]** 中定义的。

### 筛选建议 {#filtering-propositions}

您可以根据渠道、相关优惠或先前已分配命题的状态选择筛选条件来排除命题。

![](assets/offer_typology_014.png)

这些标准代表推荐规则最常用的应用。 要使用其他条件，您可以使用链接创建 **[!UICONTROL Limit propositions...]** 查询。 For more on this, refer to the [Creating a query on propositions](#creating-a-query-on-propositions) section.

* **筛选渠道**

   **[!UICONTROL On the same channel only]** :允许您排除优惠建议在选项卡中指定的渠道 **[!UICONTROL General]** 中。

   例如，为选项卡中的规则指定的渠道 **[!UICONTROL General]** 是电子邮件。 如果规则所适用的优惠目前仅在Web渠道上提供，则交互引擎可以在电子邮件投放中显示优惠。 但是，一旦通过电子邮件呈现优惠，交互引擎将选择其他渠道来呈现优惠。

   >[!NOTE]
   >
   >我们说的是渠道，而不是空间。 如果规则必须排除Web优惠上的渠道，则注定在网站上以两个空间（例如，在横幅和页面正文中）显示的优惠将不会显示在网站上（如果之前已经显示过）。
   >
   >对于涉及优惠演示的工作流，只有在对规则进行配置时，才能正确考虑这些规则 **[!UICONTROL All channels]**。

* **筛选优惠**

   通过此筛选器，可以将优惠建议数限制为特定优惠集。

   **[!UICONTROL All offers]** :默认值。 不会对优惠应用筛选器。

   **[!UICONTROL Offer being presented]** :如果选项卡中 **[!UICONTROL General]** 指定的优惠已经显示，则它将被排除。

   **[!UICONTROL Offers from the same category]** :如果已显示来自同一优惠的优惠，则排除类别。

   **[!UICONTROL The offers which the rule applies to]** :当在标签中定义了多个优惠 **[!UICONTROL General]** 时，将考虑这组优惠中的每个优惠建议，并在达到命题阈值时排除所有优惠。

   例如，优惠2、3和5在选项卡中定 **[!UICONTROL General]** 义。 最大命题数设置为2。 如果优惠2和5各呈现一次，则计数的建议数将为2。 因此，优惠3永远不会出现。

* **对命题状态进行筛选**

   此过滤器允许您选择最频繁的状态，以便优惠建议在命题历史记录中得到考虑。

   **[!UICONTROL Regardless of the proposition status]** :默认值。 没有对命题状态应用任何过滤器。

   **[!UICONTROL Accepted or rejected propositions]** :允许您排除之前已接受或拒绝的优惠。

   **[!UICONTROL Accepted propositions]** :允许您排除之前已接受的呈现优惠。

   **[!UICONTROL Rejected propositions]** :允许您排除之前呈现的已被拒绝的优惠。

### 定义收件人 {#defining-recipients}

要指定收件人，请单击链 **[!UICONTROL Edit the query from the targeting dimension...]** 接，然后选择规则所涉及的收件人。

![](assets/offer_typology_012.png)

### 创建查询 {#creating-a-query-on-propositions}

要指定要通过查询计数的建议，请单 **[!UICONTROL Limit propositions...]** 击链接并指定要考虑的条件。

在以下示例中，两个演示后要计数的建议是“特殊优惠 **”类别中的建议，** 对于呼叫中心空间， **其权重低于** 20 ****。

![](assets/offer_typology_013.png)

