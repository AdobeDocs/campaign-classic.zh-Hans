---
product: campaign
title: 跟踪假设验证
description: 了解如何在Campaign响应管理器中跟踪假设验证
feature: Campaigns, Monitoring, Reporting
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 1%

---

# 假设验证跟踪{#hypothesis-tracking}



假设计算的结果可在Adobe Campaign平台的各个级别上获得：通过假设计算出的指标和目标群体反应可通过实际假设以及营销活动和投放提供的假设报告中查看。

## 假设验证结果 {#hypothesis-results}

### 指标 {#indicators}

计算假设验证后，会自动更新多个衡量指标。 这些功能在以下位置提供： **[!UICONTROL General]** 假设验证的选项卡。

![](assets/response_hypothesis_delivery_example_010.png)

这些指标包括：

* **响应联系人的数量**：与假设验证匹配的已联系个人的数量。
* **联系响应率**：响应联系人数/投放期间联系的总人数。
* **响应控制组联系人数目**：与假设验证匹配的控制组数量。
* **对照组的响应率**：响应控制组数量/投放控制组总数。
* **反应数**：表中包含个人、假设验证和事务表之间关系的记录数。

有关指示器的完整列表，请单击 **[!UICONTROL Display the list]** 链接：

![](assets/response_hypothesis_indicators_002.png)

指标提供以下信息：

* **已联系人口的总收入**：总数超过联系的个人数量。
* **对照组的总收入**：对照组的总金额。
* **每次联系的平均收入**：总额/已联系。
* **对照组的平均收入**：总金额/对照组。
* **每次联系的总利润**：已联系的总利润。
* **对照组的总利润**：相对于对照组的总利润。
* **每次联系的平均利润**：总利润/已联系。
* **对照组的平均利润**：总利润/对照组。
* **其他收入**：（接触的平均收入 — 对照组的平均收入）&#42;联系数
* **附加利润**：（联系的平均利润 — 对照组的平均利润）/联系数
* **每次联系的平均成本**：计算的投放成本/联系人数。
* **ROI**：计算的投放成本/每次联系的总利润
* **有效ROI**：计算的投放成本/其他利润。
* **重要性**：包含值0到3，具体取决于促销活动重要性。

### 反应 {#reactions}

您可以通过查看收件人对于假设的反应 **[!UICONTROL Reactions]** 选项卡。

1. 假设验证计算完成后，转到 **[!UICONTROL Campaign management > Measurement hypotheses]** Adobe Campaign树的节点。
1. 选择所需的假设验证，然后单击 **[!UICONTROL Reactions]** 选项卡，以查看营销活动后可能购买产品的收件人列表。

   ![](assets/response_hypothesis_reactions_001.png)

## 报告 {#reports}

此 **[!UICONTROL Hypothesis report]** 您可以查看对营销活动和投放执行的假设的结果。 此报表包含由假设验证计算的指标(有关更多信息，请参阅 [指示器](#indicators))。

* **在营销活动级别**：单击 **[!UICONTROL Reports]** 相关营销策划的链接，然后选择 **[!UICONTROL Hypothesis report]**. 此报表包含活动投放的列表以及为每个投放计算的假设。

  ![](assets/response_hypothesis_campaign_report_001.png)

* **在投放级别**：要访问报表，请打开相关的投放，单击 **[!UICONTROL Reports]** 在 **[!UICONTROL Summary]** 选项卡，然后选择 **[!UICONTROL Hypothesis report]**. 如果为同一投放计算了多个假设，则报表将包含所有假设。

  ![](assets/response_hypothesis_delivery_report_001.png)
