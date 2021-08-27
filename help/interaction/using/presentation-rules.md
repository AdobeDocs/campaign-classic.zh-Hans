---
product: campaign
title: 呈现规则
description: 呈现规则
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 1%

---

# 呈现规则{#presentation-rules}

![](../../assets/v7-only.svg)

## 创建演示规则 {#creating-a-presentation-rule}

在我们的数据库中，有几份前往欧洲、非洲、美国和加拿大的旅行优惠。 我们希望发送前往加拿大的优惠，但如果接受者拒绝此类优惠，我们不希望再将其发送给他们

我们将配置我们的规则，以便每个收件人仅提供一次加拿大之旅，如果被拒绝，则不再提供。

1. 在Adobe Campaign树中，转到&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]**&#x200B;节点。
1. 创建新的&#x200B;**[!UICONTROL Offer presentation]**&#x200B;类型规则。

   ![](assets/offer_typology_example_001.png)

1. 如有必要，请更改其标签和说明。

   ![](assets/offer_typology_example_002.png)

1. 选择&#x200B;**[!UICONTROL All channels]**&#x200B;选项以将规则扩展到所有渠道。

   ![](assets/offer_typology_example_003.png)

1. 单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;链接，然后选择&#x200B;**[!UICONTROL Category]**&#x200B;节点作为表达式。

   ![](assets/offer_typology_example_004.png)

1. 选择与您的加拿大差旅选件匹配的类别，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;以关闭查询窗口。

   ![](assets/offer_typology_example_005.png)

1. 在&#x200B;**[!UICONTROL Offer presentation]**&#x200B;选项卡中，选择与环境中配置的维度相同的维度。

   ![](assets/offer_typology_example_006.png)

1. 指定应用规则的时段。

   ![](assets/offer_typology_example_007.png)

1. 将建议限制为一个，以便已经拒绝前往加拿大的收件人不会再收到类似的建议。

   ![](assets/offer_typology_example_008.png)

1. 选择&#x200B;**[!UICONTROL Offers for the same category]**&#x200B;筛选器可从&#x200B;**Canada**&#x200B;类别中排除所有选件。

   ![](assets/offer_typology_example_020.png)

1. 选择&#x200B;**[!UICONTROL Rejected propositions]**&#x200B;过滤器，以便仅考虑收件人拒绝的主张。

   ![](assets/offer_typology_example_021.png)

1. 选择将应用此规则的收件人。

   在本例中，我们将选择&#x200B;**频繁出差者**&#x200B;收件人。

   ![](assets/offer_typology_example_009.png)

1. 在选件分类中引用规则。

   ![](assets/offer_typology_example_013.png)

1. 转到选件环境（在本例中为&#x200B;**Environment - Recipient**），并引用使用&#x200B;**[!UICONTROL Eligibility]**&#x200B;选项卡中的下拉列表刚刚创建的新分类。

   ![](assets/offer_typology_example_014.png)

## 应用演示规则 {#applying-the-presentation-rule}

以下是之前创建的分类规则的应用程序示例。

我们想发送属于加拿大类别的第一个优惠建议。 如果任何收件人拒绝该选件一次，则不会再向他们提供该选件。

1. 在&#x200B;**Frevent travers**&#x200B;收件人文件夹中，选择其中一个用户档案，以检查他们有资格使用的选件：单击&#x200B;**[!UICONTROL Propositions]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡。

   在我们的示例中，**Tim Ramsey**&#x200B;符合&#x200B;**Americas**&#x200B;类别中的选件条件。

   ![](assets/offer_typology_example_015.png)

1. 首先，创建一封电子邮件投放，该邮件投放的目标是提供优惠的&#x200B;**常客**&#x200B;收件人。
1. 选择选件引擎调用参数。

   在我们的示例中，选择了&#x200B;**Travel in America**&#x200B;类别，该类别包含&#x200B;**Canada**&#x200B;和&#x200B;**United States**&#x200B;子类别。

   ![](assets/offer_typology_example_016.png)

1. 将选件插入消息正文并发送投放。 有关更多信息，请参阅[关于出站渠道](../../interaction/using/about-outbound-channels.md)。

   收件人收到了他们有资格获得的选件。

1. 收件人拒绝了加拿大选件，如建议历史中所示。

   ![](assets/offer_typology_example_018.png)

1. 检查他们现在符合条件的选件。

   我们可以看到没有选择加拿大的优惠。

   ![](assets/offer_typology_example_019.png)

**相关主题**

* [跨渠道管理优惠并控制冗余](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Manageoffersandcontrolredundancyacrosschannels)
