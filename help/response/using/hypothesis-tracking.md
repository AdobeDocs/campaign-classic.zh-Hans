---
product: campaign
title: 跟踪假设验证
description: 了解如何在Campaign响应管理器中跟踪假设验证
feature: Campaigns, Monitoring, Reporting
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 1%

---

# 假设验证跟踪{#hypothesis-tracking}



假设计算的结果可在Adobe Campaign平台的各个级别上获得：通过假设计算出的指标和目标群体反应可通过实际假设以及营销活动和投放提供的假设报告中查看。

## 假设验证结果 {#hypothesis-results}

### 指标 {#indicators}

计算假设验证后，会自动更新多个衡量指标。 这些在假设验证的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中可用。

![](assets/response_hypothesis_delivery_example_010.png)

这些指标包括：

* **响应联系人数**：与假设验证匹配的已联系个人数。
* **已联系的响应率**：传递期间已联系的响应联系人数/总联系人数。
* **响应控制组联系人数**：与假设验证匹配的控制组数。
* **控制组的响应率**：响应控制组的数量/传递控制组的总数。
* **反应数**：表中包含个人、假设验证和事务表之间关系的记录数。

有关指示器的完整列表，请单击&#x200B;**[!UICONTROL Display the list]**&#x200B;链接：

![](assets/response_hypothesis_indicators_002.png)

指标提供以下信息：

* **已联系群体的总收入**：总金额超过已联系的个人数量。
* **对照组的总收入**：总金额超过对照组的数量。
* **每个联系人的平均收入**：总金额/联系人。
* **对照组的平均收入**：总金额/对照组。
* **每个联系人的总利润**：总利润超过联系人的利润。
* **对照组的总利润**：对照组的总利润。
* **每个联系人的平均利润**：总利润/已联系。
* **控制组的平均利润**：总利润/控制组。
* **附加收入**： （被联系人的平均收入 — 对照组的平均收入）&#42;被联系的人数
* **附加利润**： （联系的平均利润 — 控制组的平均利润）/联系数
* **每个联系人的平均成本**：计算的传递成本/联系人数目。
* **ROI**：计算的投放成本/每次联系的总利润
* **有效ROI**：计算的投放成本/附加利润。
* **重要性**：包含值0到3，具体取决于促销活动重要性。

### 反应 {#reactions}

您可以通过&#x200B;**[!UICONTROL Reactions]**&#x200B;选项卡查看收件人对假设的反应。

1. 假设验证计算完成后，转到Adobe Campaign树的&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;节点。
1. 选择所需的假设验证，然后单击&#x200B;**[!UICONTROL Reactions]**&#x200B;选项卡以查看营销活动后可能购买产品的收件人列表。

   ![](assets/response_hypothesis_reactions_001.png)

## 报告 {#reports}

**[!UICONTROL Hypothesis report]**&#x200B;允许您查看对营销活动和投放执行的假设的结果。 此报表包含由假设验证计算的指标（有关更多信息，请参阅[指标](#indicators)）。

* **在营销活动级别**：单击相关营销活动的&#x200B;**[!UICONTROL Reports]**&#x200B;链接并选择&#x200B;**[!UICONTROL Hypothesis report]**。 此报表包含活动投放的列表以及为每个投放计算的假设。

  ![](assets/response_hypothesis_campaign_report_001.png)

* **在投放级别**：要访问报告，请打开相关的投放，单击&#x200B;**[!UICONTROL Summary]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Reports]**&#x200B;并选择&#x200B;**[!UICONTROL Hypothesis report]**。 如果为同一投放计算了多个假设，则报表将包含所有假设。

  ![](assets/response_hypothesis_delivery_report_001.png)
