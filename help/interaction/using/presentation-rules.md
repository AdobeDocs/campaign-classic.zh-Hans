---
product: campaign
title: 呈现规则
description: 呈现规则
feature: Interaction, Offers
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 1%

---

# 呈现规则{#presentation-rules}



## 创建推荐规则 {#creating-a-presentation-rule}

在我们的数据库中，有数种针对欧洲、非洲、美国和加拿大的旅行优惠。 我们希望发送赴加拿大旅行的聘用，但如果收件人拒绝此类聘用，我们便不希望再次向其发送

我们将配置规则，以便每个收件人仅提供一次加拿大之行，如果被拒绝，则不再提供加拿大之行。

1. 在Adobe Campaign树中，转到&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]**&#x200B;节点。
1. 创建新的&#x200B;**[!UICONTROL Offer presentation]**&#x200B;类型规则。

   ![](assets/offer_typology_example_001.png)

1. 根据需要更改其标签及其描述。

   ![](assets/offer_typology_example_002.png)

1. 选择&#x200B;**[!UICONTROL All channels]**&#x200B;选项以将规则扩展到所有渠道。

   ![](assets/offer_typology_example_003.png)

1. 单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;链接并选择&#x200B;**[!UICONTROL Category]**&#x200B;节点作为表达式。

   ![](assets/offer_typology_example_004.png)

1. 选择与您的加拿大旅行优惠匹配的类别，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;以关闭查询窗口。

   ![](assets/offer_typology_example_005.png)

1. 在&#x200B;**[!UICONTROL Offer presentation]**&#x200B;选项卡中，选择与环境中配置的维度相同的维度。

   ![](assets/offer_typology_example_006.png)

1. 指定应用规则的时段。

   ![](assets/offer_typology_example_007.png)

1. 将建议限制为一个，以便已拒绝加拿大旅行的收件人不会收到另一个类似的建议。

   ![](assets/offer_typology_example_008.png)

1. 选择&#x200B;**[!UICONTROL Offers for the same category]**&#x200B;筛选器以排除&#x200B;**加拿大**&#x200B;类别中的所有选件。

   ![](assets/offer_typology_example_020.png)

1. 选择&#x200B;**[!UICONTROL Rejected propositions]**&#x200B;筛选器以仅考虑收件人拒绝的建议。

   ![](assets/offer_typology_example_021.png)

1. 选择要应用此规则的收件人。

   在本例中，我们将选择&#x200B;**频繁出差者**&#x200B;收件人。

   ![](assets/offer_typology_example_009.png)

1. 在优惠类型中引用规则。

   ![](assets/offer_typology_example_013.png)

1. 转到优惠环境（**环境 — 此示例中为Recipient**）并引用刚刚使用&#x200B;**[!UICONTROL Eligibility]**&#x200B;选项卡中的下拉列表创建的新分类。

   ![](assets/offer_typology_example_014.png)

## 应用呈现规则 {#applying-the-presentation-rule}

以下是之前创建的分类规则的应用程序示例。

我们希望发送属于加拿大类别的第一个优惠建议。 如果任何收件人拒绝了选件一次，则不会再次向其提供该选件。

1. 在&#x200B;**常客**&#x200B;收件人文件夹中，选择一个用户档案以检查其符合条件的优惠：单击&#x200B;**[!UICONTROL Propositions]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡。

   在我们的示例中，**Tim Ramsey**&#x200B;有资格获得属于&#x200B;**美洲**&#x200B;类别的优惠。

   ![](assets/offer_typology_example_015.png)

1. 首先，创建电子邮件投放，将选件定位到&#x200B;**频繁出差者**&#x200B;的收件人。
1. 选择优惠引擎调用参数。

   在我们的示例中，选择了&#x200B;**Travel in America**&#x200B;类别，该类别包含&#x200B;**Canada**&#x200B;和&#x200B;**United States**&#x200B;子类别。

   ![](assets/offer_typology_example_016.png)

1. 在消息正文中插入优惠并发送投放。 有关详情，请参阅[关于出站频道](../../interaction/using/about-outbound-channels.md)。

   收件人已收到他们符合条件的优惠。

1. 收件人拒绝了加拿大的报价，如建议历史记录中所示。

   ![](assets/offer_typology_example_018.png)

1. 检查他们现在有资格享受的优惠。

   我们可以看到，没有选择加拿大的优惠。

   ![](assets/offer_typology_example_019.png)
