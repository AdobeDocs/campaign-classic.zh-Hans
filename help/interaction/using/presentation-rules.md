---
product: campaign
title: 呈现规则
description: 呈现规则
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 1%

---

# 呈现规则{#presentation-rules}



## 创建呈现规则 {#creating-a-presentation-rule}

在我们的数据库中，有数种针对欧洲、非洲、美国和加拿大的旅行方案。 我们希望发送赴加拿大旅行的聘用，但如果收件人拒绝此类聘用，我们不想再次发送此聘用

我们将配置规则，以便每个收件人仅提供一次加拿大之行，如果被拒绝，则不再提供加拿大之行。

1. 在Adobe Campaign树中，转到 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** 节点。
1. 新建 **[!UICONTROL Offer presentation]** 键入规则。

   ![](assets/offer_typology_example_001.png)

1. 根据需要更改其标签和描述。

   ![](assets/offer_typology_example_002.png)

1. 选择 **[!UICONTROL All channels]** 选项以将规则扩展到所有渠道。

   ![](assets/offer_typology_example_003.png)

1. 单击 **[!UICONTROL Edit expression]** 链接并选择 **[!UICONTROL Category]** 节点。

   ![](assets/offer_typology_example_004.png)

1. 选择与您的加拿大旅行优惠匹配的类别，然后单击 **[!UICONTROL OK]** 以关闭查询窗口。

   ![](assets/offer_typology_example_005.png)

1. 在 **[!UICONTROL Offer presentation]** 选项卡中，选择与环境中配置的维度相同的维度。

   ![](assets/offer_typology_example_006.png)

1. 指定应用规则的时段。

   ![](assets/offer_typology_example_007.png)

1. 将建议限制为一个，以便已拒绝加拿大旅行的收件人不会收到另一个类似的建议。

   ![](assets/offer_typology_example_008.png)

1. 选择 **[!UICONTROL Offers for the same category]** 筛选条件以从中排除所有选件 **加拿大** 类别。

   ![](assets/offer_typology_example_020.png)

1. 选择 **[!UICONTROL Rejected propositions]** 筛选以仅考虑收件人拒绝的建议。

   ![](assets/offer_typology_example_021.png)

1. 选择要应用此规则的收件人。

   在本例中，我们将选择 **经常出差** 收件人。

   ![](assets/offer_typology_example_009.png)

1. 引用优惠类型中的规则。

   ![](assets/offer_typology_example_013.png)

1. 转到优惠环境(**环境 — 收件人** 在本例中)和引用刚刚使用 **[!UICONTROL Eligibility]** 选项卡。

   ![](assets/offer_typology_example_014.png)

## 应用呈现规则 {#applying-the-presentation-rule}

以下是之前创建的分类规则的应用程序示例。

我们希望发送属于加拿大类别的首个优惠建议。 如果任何收件人拒绝了选件一次，则不会再向其提供该选件。

1. 在 **经常出差** 收件人文件夹，选择一个用户档案以检查其符合条件的优惠：单击 **[!UICONTROL Propositions]** 选项卡，然后 **[!UICONTROL Preview]** 选项卡。

   在我们的例子中， **蒂姆·拉姆齐** 符合资格获得属于以下计划一部分的优惠 **美洲** 类别。

   ![](assets/offer_typology_example_015.png)

1. 首先，创建面向您的客户的电子邮件投放 **经常出差** 具有选件的收件人。
1. 选择优惠引擎调用参数。

   在我们的示例中， **美国旅游** 已选择类别，其中包含 **加拿大** 和 **美国** 子类别。

   ![](assets/offer_typology_example_016.png)

1. 在消息正文中插入优惠并发送投放。 有关更多信息，请参阅 [关于出站渠道](../../interaction/using/about-outbound-channels.md).

   收件人已收到他们符合条件的优惠。

1. 收件人拒绝了加拿大的报价，如建议案历史所示。

   ![](assets/offer_typology_example_018.png)

1. 查看他们现在有资格享受的优惠。

   我们可以看到，没有选择给加拿大的报价。

   ![](assets/offer_typology_example_019.png)
