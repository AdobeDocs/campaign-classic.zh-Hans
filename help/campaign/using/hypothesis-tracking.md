---
product: campaign
title: 假设验证跟踪
description: 假设验证跟踪
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 1%

---

# 假设验证跟踪{#hypothesis-tracking}

假设验证计算结果可在Adobe Campaign平台的不同级别获得：通过假设和目标群体反应计算的指标可通过实际假设以及通过营销活动和投放提供的假设验证报告中可见。

## 假设结果{#hypothesis-results}

### 指标 {#indicators}

计算假设后，会自动更新多个测量指标。 这些参数位于假设的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中。

![](assets/response_hypothesis_delivery_example_010.png)

这些指标包括：

* **答复者联系人数**:符合该假设的联系个人数量。
* **联系的响应率**:答复者联系人数/投放期间联系的总人数。
* **答复者控制组联系人数**:与假设匹配的控制组数量。
* **控制组的响应率**:响应者控制组数量/传递控制组总数。
* **反应次数**:表中包含个人、假设和事务表之间关系的记录数。

有关完整的指标列表，请单击&#x200B;**[!UICONTROL Display the list]**&#x200B;链接：

![](assets/response_hypothesis_indicators_002.png)

指标提供了以下信息：

* **联系的总人口收入**:与接触的个人人数相比的总金额。
* **控制组的总收入**:控制组数量的总金额。
* **每个联系人的平均收入**:总金额/联系人。
* **控制组的平均收入**:总金额/控制组。
* **每个联系人的毛利总额**:联系的总利润。
* **控制组的毛利总额**:控制组的毛利总额。
* **每个联系人的平均毛利**:总利润/联系人。
* **控制组的平均边距**:总边距/控制组。
* **额外收入**:（联系人的平均收入 — 控制组的平均收入）*联系人数
* **附加边距**:（平均联系边距 — 控制组的平均边距）/联系次数
* **每个联系人的平均成本**:计算的交货成本/联系人数。
* **ROI**:交付的计算成本/每个联系人的毛利总额
* **有效ROI**:计算的交付成本/附加利润。
* **显着性**:包含值0到3，具体取决于促销活动显着性。

### 反应 {#reactions}

您可以通过&#x200B;**[!UICONTROL Reactions]**&#x200B;选项卡查看收件人对假设的反应。

1. 完成假设验证计算后，转到Adobe Campaign树的&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;节点。
1. 选择所需的假设验证并单击&#x200B;**[!UICONTROL Reactions]**&#x200B;选项卡，以查看营销活动后可能购买商品的收件人列表。

   ![](assets/response_hypothesis_reactions_001.png)

## 报告 {#reports}

**[!UICONTROL Hypothesis report]**&#x200B;允许您查看对营销活动和投放执行的假设的结果。 此报表包含由假设计算的指标（有关更多信息，请参阅[指标](#indicators)）。

* **在营销活动级别**:单击相 **[!UICONTROL Reports]** 关营销活动的链接，然后选择 **[!UICONTROL Hypothesis report]**。此报表包含营销活动投放列表以及针对每个投放计算的假设验证。

   ![](assets/response_hypothesis_campaign_report_001.png)

* **在投放级别**:要访问报告，请打开相关投放，单击选 **[!UICONTROL Reports]** 项卡 **[!UICONTROL Summary]** 中的，然后选择 **[!UICONTROL Hypothesis report]**。如果为同一投放计算了多个假设，则报告将包含所有假设。

   ![](assets/response_hypothesis_delivery_report_001.png)
