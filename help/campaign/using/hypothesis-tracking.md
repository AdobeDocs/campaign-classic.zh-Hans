---
title: 假设跟踪
seo-title: 假设跟踪
description: 假设跟踪
seo-description: null
page-status-flag: never-activated
uuid: cb949a9d-8bbe-446b-b5b4-22234a91a68b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 4452bfc6-9ac4-4d81-a63c-879a163c13ee
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 假设跟踪{#hypothesis-tracking}

假设计算的结果可在Adobe Campaign平台的不同级别获得：通过假设和目标群体反应计算的指标通过实际假设以及通过活动和交付提供的假设报告中可见。

## 假设结果 {#hypothesis-results}

### 指标 {#indicators}

一旦计算了该假设，就会自动更新多个测量指标。 这些选项卡在假 **[!UICONTROL General]** 说标签中可用。

![](assets/response_hypothesis_delivery_example_010.png)

这些指标是：

* **被申请人联系人数**:与假设相符的接触个体的数量。
* **联系的响应率**:答复者联系人数／交付期间联系的总人数。
* **答复者控制组联系人数**:与假设匹配的控制组数。
* **控制组的响应率**:答复者控制组数量／交付控制组总数。
* **反应数**:表中记录的数量包括个人、假设和事务表之间的关系。

对于指示器的完整列表，单击链 **[!UICONTROL Display the list]** 接：

![](assets/response_hypothesis_indicators_002.png)

指示器提供以下信息：

* **联系人口总收入**:总数超过所联系的个人数。
* **控制组的总收益**:控制组数量的总额。
* **每个联系人的平均收入**:总数／联系人数。
* **控制组平均收入**:总金额／控制组。
* **每位联系人的总利润**:联系的毛利总额。
* **控制组的毛利总额**:控制组的毛利总额。
* **每个联系人的平均边距**:总边距／联系人。
* **控制组的平均边距**:总边距／控制组。
* **额外收入**:（已联系的平均收入——控制组的平均收入）*已联系的人数
* **附加边距**:（已联系的平均边距——控制组的平均边距）/已联系人数
* **每个联系人的平均成本**:计算的交付成本／联系人数。
* **ROI**:交付的计算成本／每个联系人的总利润
* **有效的投资回报**:计算的交付成本／附加利润。
* **重要性**:根据营销活动的重要性，包含0到3的值。

### 反应 {#reactions}

您可以通过选项卡查看收件人对假设的反 **[!UICONTROL Reactions]** 应。

1. 假设计算完成后，转到Adobe **[!UICONTROL Campaign management > Measurement hypotheses]** Campaign树的节点。
1. 选择所需假设并单击选 **[!UICONTROL Reactions]** 项卡，以查看可能在营销活动后购买内容的收件人列表。

   ![](assets/response_hypothesis_reactions_001.png)

## 报告 {#reports}

您可 **[!UICONTROL Hypothesis report]** 以查看对营销活动和交付执行的假设的结果。 此报告包含由假设计算的指标(有关详细信息，请参阅 [指标](#indicators))。

* **在营销活动级别**:单击相 **[!UICONTROL Reports]** 关营销活动的链接，然后选择 **[!UICONTROL Hypothesis report]**。 此报告包含营销活动提交的列表以及为每个交付计算的假设。

   ![](assets/response_hypothesis_campaign_report_001.png)

* **在交付级别**:要访问报告，请打开相关的提交，单击选 **[!UICONTROL Reports]** 项卡中 **[!UICONTROL Summary]** 的，然后选择 **[!UICONTROL Hypothesis report]**。 如果为同一交付计算了若干假设，报告将包含所有假设。

   ![](assets/response_hypothesis_delivery_report_001.png)
