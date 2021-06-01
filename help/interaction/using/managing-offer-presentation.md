---
product: campaign
title: 管理优惠演示
description: 管理优惠演示
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: 6158ffaa-cb08-4f77-82b8-b3e5e1bf7fd7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---

# 管理优惠演示{#managing-offer-presentation}

## 演示规则概述{#presentation-rules-overview}

通过交互，您可以使用演示规则控制优惠建议的流程。 这些特定于交互的规则是分类规则。 它们允许您根据已向收件人提出的建议的历史记录排除优惠。 环境中会引用这些参数

## 创建和引用选件演示规则{#creating-and-referencing-an-offer-presentation-rule}

1. 转到&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]**&#x200B;节点。
1. 创建分类规则并选择&#x200B;**[!UICONTROL Offer presentation]**&#x200B;类型。

   ![](assets/offer_typology_001.png)

1. 指定应用规则的渠道。

   ![](assets/offer_typology_002.png)

1. 配置规则的应用程序条件。 有关更多信息，请参阅[演示规则设置](#presentation-rule-settings)。
1. 转到&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]**&#x200B;节点，并创建将对所有&#x200B;**[!UICONTROL Offer presentation]**&#x200B;类型规则进行分组的分类。

   ![](assets/offer_typology_003.png)

1. 创建分类后，将光标放在分类规则上，并在刚刚创建的分类中对其进行分组。

   ![](assets/offer_typology_004.png)

1. 在选件环境中，使用下拉列表引用分类。

   ![](assets/offer_typology_005.png)

## 演示规则设置{#presentation-rule-settings}

### 应用程序标准{#application-criteria-}

**[!UICONTROL General]**&#x200B;选项卡中可用的应用程序标准允许您指定将应用演示规则的选件。 为此，您需要创建一个查询并选择相关的选件，如下所述。

1. 在分类规则中，单击&#x200B;**[!UICONTROL Edit the rule application conditions...]**&#x200B;链接以创建查询。

   ![](assets/offer_typology_006.png)

1. 在查询窗口中，您可以对要向其应用分类规则的选件应用过滤器。

   例如，您可以选择选件类别。

   ![](assets/offer_typology_008.png)

### 选件维度{#offer-dimensions}

在&#x200B;**[!UICONTROL Offer presentation]**&#x200B;选项卡中，必须为表示规则指定与环境中配置的维度相同的维度。

**[!UICONTROL Targeting dimension]**&#x200B;与收件人表一致(默认情况下为：nms:recipients)，将接收优惠建议。 **[!UICONTROL Storage dimension]**&#x200B;与包含与定向维度链接的命题历史记录的表（默认情况下：nms:campationRcp）一致。

![](assets/offer_typology_009.png)

>[!NOTE]
>
>您还可以使用非标准表。 如果要使用特定定向维度，则需要使用目标映射创建表以及专用环境。 有关更多信息，请参阅[创建选件环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

### 句点 {#period}

这是一个从选件演示日期开始的滑动周期。 它为优惠建议的有效性设置了时限。 该规则不适用于在此期间之后提出的建议。

期间从建议日期前的&#x200B;**n**&#x200B;天开始，并在之后的&#x200B;**n**&#x200B;天结束，其中&#x200B;**n**&#x200B;对应于在&#x200B;**[!UICONTROL Period considered]**&#x200B;字段中输入的数字：

* 对于集客空间，建议日期是选件演示日期。
* 对于出站空间，建议日期是投放联系日期（例如，在定位工作流中输入的投放日期）。

使用箭头更改天数或直接输入句点（例如“2d 6h”）。

![](assets/offer_typology_010.png)

### 命题数{#number-of-propositions}

可以设置在排除相关选件之前可以提出的建议的最大数量。

使用箭头更改优惠建议的数量。

![](assets/offer_typology_011.png)

## 定义主张和收件人{#defining-propositions-and-recipients}

通过&#x200B;**[!UICONTROL Propositions to count]**&#x200B;部分，您可以指定收件人和建议，如果建议历史记录中出现特定次数的建议，则这些建议会导致排除在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中定义的选件。

### 筛选建议{#filtering-propositions}

您可以根据渠道、相关选件或先前已分配命题的状态来选择筛选标准以排除命题。

![](assets/offer_typology_014.png)

这些标准表示表示规则最常用的应用。 要使用其他条件，您可以使用&#x200B;**[!UICONTROL Limit propositions...]**&#x200B;链接创建查询。 有关更多信息，请参阅[创建关于命题的查询](#creating-a-query-on-propositions)一节。

* **在渠道上筛选**

   **[!UICONTROL On the same channel only]** :允许您在选项卡中指定的渠道中排除优惠 **[!UICONTROL General]** 建议。

   例如，在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中为规则指定的渠道是电子邮件。 如果规则所适用的选件到目前为止仅在Web渠道上提供，则交互引擎可以在电子邮件投放中显示这些选件。 但是，在通过电子邮件呈现选件后，交互引擎将选择其他渠道来显示选件。

   >[!NOTE]
   >
   >我们讨论的是频道，而不是空间。 如果规则必须排除Web渠道上的选件，则如果之前已经提供该选件，则该选件将不会显示在网站上的两个空格（例如，在横幅和页面正文中）中。
   >
   >对于涉及选件演示的工作流，仅当在&#x200B;**[!UICONTROL All channels]**&#x200B;上配置规则时，才会正确考虑这些规则。

* **筛选选件**

   此过滤器允许您将选件建议计数到特定的选件集。

   **[!UICONTROL All offers]** :默认值。选件不会应用任何过滤器。

   **[!UICONTROL Offer being presented]** :如果选件已经显示， **[!UICONTROL General]** 则会排除在选项卡中指定的选件。

   **[!UICONTROL Offers from the same category]** :如果已经显示同一类别中的选件，则会排除该选件。

   **[!UICONTROL The offers which the rule applies to]** :在选项卡中定义多个选 **[!UICONTROL General]** 件后，将考虑此选件集中的每个选件建议，并在达到建议阈值时排除所有选件。

   例如，选件2、3和5在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中定义。 建议的最大数设置为2。 如果每个选件2和5都显示一次，则计数的建议数将为2。 因此，将永远不会提供选件3。

* **建议状态筛选**

   此过滤器允许您为建议历史中要考虑的选件建议选择最频繁的状态。

   **[!UICONTROL Regardless of the proposition status]** :默认值。没有对命题状态应用任何过滤器。

   **[!UICONTROL Accepted or rejected propositions]** :允许您排除之前呈现且已被接受或拒绝的选件。

   **[!UICONTROL Accepted propositions]** :允许您排除之前已接受的选件。

   **[!UICONTROL Rejected propositions]** :允许您排除之前呈现且已被拒绝的选件。

### 定义收件人{#defining-recipients}

要指定收件人，请单击&#x200B;**[!UICONTROL Edit the query from the targeting dimension...]**&#x200B;链接，然后选择规则所关注的收件人。

![](assets/offer_typology_012.png)

### 创建关于命题{#creating-a-query-on-propositions}的查询

要指定要通过查询计数的命题，请单击&#x200B;**[!UICONTROL Limit propositions...]**&#x200B;链接并指定要考虑的标准。

在以下示例中，两个演示之后要计数的命题是&#x200B;**特殊选件**&#x200B;类别中的&#x200B;**呼叫中心**&#x200B;空间的命题，权重低于&#x200B;**20**。

![](assets/offer_typology_013.png)
