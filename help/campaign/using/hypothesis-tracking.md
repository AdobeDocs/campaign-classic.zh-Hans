---
solution: Campaign Classic
product: campaign
title: 假设验证跟踪
description: 假设验证跟踪
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 1%

---


# 假设验证跟踪{#hypothesis-tracking}

假设验证计算结果可在Adobe Campaign平台的不同级别上获得：假设验证和目标群反应计算的指标可通过实际假设验证以及活动和投放提供的假设验证报告看到。

## 假设验证结果 {#hypothesis-results}

### 指标 {#indicators}

一旦计算了假设验证，就会自动更新多个度量指标。 这些选项卡位 **[!UICONTROL General]** 于假设验证的选项卡中。

![](assets/response_hypothesis_delivery_example_010.png)

这些指标是：

* **被申请人联系人数**:与假设验证匹配的联系人数。
* **联系的响应率**:答复者联系人数/投放内联系的总人数。
* **答复者对照组联系人数**:与对照组匹配的假设验证数。
* **对照组的响应率**:答复对照组数/投放对照组总数。
* **反应数**:表中记录数，它包含个人、假设验证和事务表之间的关系。

要获得完整的列表，请单击链 **[!UICONTROL Display the list]** 接：

![](assets/response_hypothesis_indicators_002.png)

指标提供了以下信息：

* **联系的人口总收入**:所联系个人总数。
* **对照组总收入**:对照组总数。
* **每个联系人的平均收入**:总金额／联系人数。
* **对照组平均收入**:总金额/对照组。
* **每个联系人的毛利总额**:联系的毛利总数。
* **对照组总利润**:对照组毛利总额。
* **每个联系人的平均边距**:总利润／联系人。
* **平均对照组率**:总边距/对照组。
* **额外收入**:(联系人的平均收入-对照组的平均收入)*联系人数
* **附加利润**:(平均联系对照组率——平均联系客户率)/联系人数
* **每个联系人的平均成本**:计算投放成本／联系人数。
* **ROI**:计算投放成本／每个联系人的毛利总额
* **有效投资回报**:计算投放成本／附加毛利。
* **重要性**:根据活动重要性，包含0到3的值。

### 反应 {#reactions}

您可以通过选项卡视图收件人对假设验证的 **[!UICONTROL Reactions]** 反应。

1. 假设验证计算完成后，转 **[!UICONTROL Campaign management > Measurement hypotheses]** 到Adobe Campaign树的节点。
1. 选择所需的假设验证并单击选 **[!UICONTROL Reactions]** 项卡，以视图可能在营销活动后购买某些产品的收件人的列表。

   ![](assets/response_hypothesis_reactions_001.png)

## 报告 {#reports}

您 **[!UICONTROL Hypothesis report]** 可以视图对活动和投放执行的假设验证的结果。 此报告包含由假设验证计算的指标(有关详细信息，请参阅 [指标](#indicators))。

* **在活动级**:单击相 **[!UICONTROL Reports]** 关活动的链接，然后选择 **[!UICONTROL Hypothesis report]**。 此报告包含活动投放的列表以及为每个投放计算的假设验证。

   ![](assets/response_hypothesis_campaign_report_001.png)

* **在投放级**:要访问报告，请打开相关投放，单击 **[!UICONTROL Reports]** 选项卡 **[!UICONTROL Summary]** 中的，然后选择 **[!UICONTROL Hypothesis report]**。 如果为同一假设验证计算了多个投放，则报表将包含所有假设验证。

   ![](assets/response_hypothesis_delivery_report_001.png)
