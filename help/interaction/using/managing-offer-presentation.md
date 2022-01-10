---
product: campaign
title: 管理优惠演示
description: 管理优惠演示
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: 6158ffaa-cb08-4f77-82b8-b3e5e1bf7fd7
source-git-commit: d835da6c7b55d9bf70b6b5dc58880718e12211d5
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 0%

---

# 管理优惠演示{#managing-offer-presentation}

![](../../assets/common.svg)

## 演示规则概述 {#presentation-rules-overview}

通过交互，您可以使用演示规则控制优惠建议的流程。 这些特定于交互的规则是分类规则。 它们允许您根据已向收件人提出的建议的历史记录排除优惠。 环境中会引用这些参数

## 创建和引用优惠演示规则 {#creating-and-referencing-an-offer-presentation-rule}

1. 转到 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** 节点。
1. 创建分类规则并选择 **[!UICONTROL Offer presentation]** 类型。

   ![](assets/offer_typology_001.png)

1. 指定应用规则的渠道。

   ![](assets/offer_typology_002.png)

1. 配置规则的应用程序条件。 有关更多信息，请参阅 [演示规则设置](#presentation-rule-settings).
1. 转到 **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** 节点，并创建将所有 **[!UICONTROL Offer presentation]** 类型规则。

   ![](assets/offer_typology_003.png)

1. 创建分类后，将光标放在分类规则上，并在刚刚创建的分类中对其进行分组。

   ![](assets/offer_typology_004.png)

1. 在选件环境中，使用下拉列表引用分类。

   ![](assets/offer_typology_005.png)

## 演示规则设置 {#presentation-rule-settings}

### 应用程序标准 {#application-criteria-}

中可用的应用程序标准 **[!UICONTROL General]** 选项卡，您可以指定将应用演示规则的选件。 为此，您需要创建一个查询并选择相关的选件，如下所述。

1. 在分类规则中，单击 **[!UICONTROL Edit the rule application conditions...]** 链接以创建查询。

   ![](assets/offer_typology_006.png)

1. 在查询窗口中，您可以对要向其应用分类规则的选件应用过滤器。

   例如，您可以选择选件类别。

   ![](assets/offer_typology_008.png)

### 选件维度 {#offer-dimensions}

在 **[!UICONTROL Offer presentation]** 选项卡，则必须为表示规则指定与环境中配置的维度相同的维度。

的 **[!UICONTROL Targeting dimension]** 与收件人表格一致(默认情况下为：nms:recipients)，将接收优惠建议。 的 **[!UICONTROL Storage dimension]** 与包含链接到定向维度的命题历史记录的表（默认情况下）一致:nms:建议Rcp)。

![](assets/offer_typology_009.png)

>[!NOTE]
>
>您还可以使用非标准表。 如果要使用特定定向维度，则需要使用目标映射创建表以及专用环境。 有关更多信息，请参阅 [创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

### 句点 {#period}

这是一个从选件演示日期开始的滑动周期。 它为优惠建议的有效性设置了时限。 该规则不适用于在此期间之后提出的建议。

期间开始 **n** 提案日期和结束前的天数 **n** 天后，其中 **n** 对应于 **[!UICONTROL Period considered]** 字段：

* 对于集客空间，建议日期是选件演示日期。
* 对于出站空间，建议日期是投放联系日期（例如，在定位工作流中输入的投放日期）。

使用箭头更改天数或直接输入句点（例如“2d 6h”）。

![](assets/offer_typology_010.png)

### 建议数 {#number-of-propositions}

可以设置在排除相关选件之前可以提出的建议的最大数量。

使用箭头更改优惠建议的数量。

![](assets/offer_typology_011.png)

## 定义主张和收件人 {#defining-propositions-and-recipients}

的 **[!UICONTROL Propositions to count]** 部分中，您可以指定收件人和建议，这些建议将导致排除 **[!UICONTROL General]** 选项卡，以检查在建议历史记录中显示的次数。

### 筛选建议 {#filtering-propositions}

您可以根据渠道、相关选件或先前已分配命题的状态来选择筛选标准以排除命题。

![](assets/offer_typology_014.png)

这些标准表示表示规则最常用的应用。 要使用其他标准，您可以使用 **[!UICONTROL Limit propositions...]** 链接。 有关更多信息，请参阅 [创建关于命题的查询](#creating-a-query-on-propositions) 中。

* **在渠道上筛选**

   **[!UICONTROL On the same channel only]** :允许您排除 **[!UICONTROL General]** 选项卡。

   例如，为 **[!UICONTROL General]** 选项卡。 如果规则所适用的选件到目前为止仅在Web渠道上提供，则交互引擎可以在电子邮件投放中显示这些选件。 但是，在通过电子邮件呈现选件后，交互引擎将选择其他渠道来显示选件。

   >[!NOTE]
   >
   >我们讨论的是频道，而不是空间。 如果规则必须排除Web渠道上的选件，则如果之前已经提供该选件，则该选件将不会显示在网站上的两个空格（例如，在横幅和页面正文中）中。
   >
   >对于涉及选件演示的工作流，仅当在上配置了规则时，才会正确考虑这些规则 **[!UICONTROL All channels]**.

* **筛选选件**

   此过滤器允许您将选件建议计数到特定的选件集。

   **[!UICONTROL All offers]** :默认值。 选件不会应用任何过滤器。

   **[!UICONTROL Offer being presented]** :在 **[!UICONTROL General]** 选项卡（如果已显示）。

   **[!UICONTROL Offers from the same category]** :如果已经显示同一类别中的选件，则会排除该选件。

   **[!UICONTROL The offers which the rule applies to]** :在 **[!UICONTROL General]** 选项卡，则此选件集中的每个选件建议都会被考虑，并在达到建议阈值时以排除所有选件的结尾。

   例如，选件2、3和5在 **[!UICONTROL General]** 选项卡。 建议的最大数设置为2。 如果每个选件2和5都显示一次，则计数的建议数将为2。 因此，将永远不会提供选件3。

* **建议状态筛选**

   此过滤器允许您为建议历史中要考虑的选件建议选择最频繁的状态。

   **[!UICONTROL Regardless of the proposition status]** :默认值。 没有对命题状态应用任何过滤器。

   **[!UICONTROL Accepted or rejected propositions]** :允许您排除之前呈现且已被接受或拒绝的选件。

   **[!UICONTROL Accepted propositions]** :允许您排除之前已接受的选件。

   **[!UICONTROL Rejected propositions]** :允许您排除之前呈现且已被拒绝的选件。

### 定义收件人 {#defining-recipients}

要指定收件人，请单击 **[!UICONTROL Edit the query from the targeting dimension...]** 链接并选择规则所关注的收件人。

![](assets/offer_typology_012.png)

### 创建关于命题的查询 {#creating-a-query-on-propositions}

要指定要通过查询计数的命题，请单击 **[!UICONTROL Limit propositions...]** 链接，并指定要考虑的条件。

在以下示例中，两个演示之后要计数的命题是 **特别优惠** 类别， **呼叫中心** 空间，重量低于 **20**.

![](assets/offer_typology_013.png)
