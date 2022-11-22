---
product: campaign
title: 呈现规则
description: 呈现规则
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: 6eaf7490f1be913986af2924017d014d2ba54559
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 1%

---

# 呈现规则{#presentation-rules}

![](../../assets/common.svg)

## 创建演示规则 {#creating-a-presentation-rule}

在我们的数据库中，有几份前往欧洲、非洲、美国和加拿大的旅行优惠。 我们希望发送前往加拿大的优惠，但如果接受者拒绝此类优惠，我们不希望再将其发送给他们

我们将配置我们的规则，以便每个收件人仅提供一次加拿大之旅，如果被拒绝，则不再提供。

1. 在Adobe Campaign树中，转到 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** 节点。
1. 新建 **[!UICONTROL Offer presentation]** 类型规则。

   ![](assets/offer_typology_example_001.png)

1. 如有必要，请更改其标签和说明。

   ![](assets/offer_typology_example_002.png)

1. 选择 **[!UICONTROL All channels]** 选项以将规则扩展到所有渠道。

   ![](assets/offer_typology_example_003.png)

1. 单击 **[!UICONTROL Edit expression]** 链接，然后选择 **[!UICONTROL Category]** 节点。

   ![](assets/offer_typology_example_004.png)

1. 选择与您的加拿大差旅选件匹配的类别，然后单击 **[!UICONTROL OK]** 以关闭查询窗口。

   ![](assets/offer_typology_example_005.png)

1. 在 **[!UICONTROL Offer presentation]** 选项卡，选择与环境中配置的维度相同的维度。

   ![](assets/offer_typology_example_006.png)

1. 指定应用规则的时段。

   ![](assets/offer_typology_example_007.png)

1. 将建议限制为一个，以便已经拒绝前往加拿大的收件人不会再收到类似的建议。

   ![](assets/offer_typology_example_008.png)

1. 选择 **[!UICONTROL Offers for the same category]** 过滤器，从 **加拿大** 类别。

   ![](assets/offer_typology_example_020.png)

1. 选择 **[!UICONTROL Rejected propositions]** 过滤以仅考虑收件人拒绝的建议。

   ![](assets/offer_typology_example_021.png)

1. 选择将应用此规则的收件人。

   在本例中，我们将选择 **常客** 收件人。

   ![](assets/offer_typology_example_009.png)

1. 在选件分类中引用规则。

   ![](assets/offer_typology_example_013.png)

1. 转到选件环境(**环境 — 收件人** 在本例中)，并引用使用 **[!UICONTROL Eligibility]** 选项卡。

   ![](assets/offer_typology_example_014.png)

## 应用演示规则 {#applying-the-presentation-rule}

以下是之前创建的分类规则的应用程序示例。

我们想发送属于加拿大类别的第一个优惠建议。 如果任何收件人拒绝该选件一次，则不会再向他们提供该选件。

1. 在 **常客** 收件人文件夹中，选择一个配置文件以检查其符合条件的选件：单击 **[!UICONTROL Propositions]** 选项卡，然后 **[!UICONTROL Preview]** 选项卡。

   在我们的示例中， **蒂姆·拉姆齐** 有资格获得属于 **美洲** 类别。

   ![](assets/offer_typology_example_015.png)

1. 首先，创建以您的 **常客** 具有选件的收件人。
1. 选择选件引擎调用参数。

   在本例中， **美国旅行** 类别，其中包含 **加拿大** 和 **美国** 子类别。

   ![](assets/offer_typology_example_016.png)

1. 将选件插入消息正文并发送投放。 有关更多信息，请参阅 [关于出站渠道](../../interaction/using/about-outbound-channels.md).

   收件人收到了他们有资格获得的选件。

1. 收件人拒绝了加拿大选件，如建议历史中所示。

   ![](assets/offer_typology_example_018.png)

1. 检查他们现在符合条件的选件。

   我们可以看到没有选择加拿大的优惠。

   ![](assets/offer_typology_example_019.png)
