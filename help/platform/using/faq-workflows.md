---
product: campaign
title: 工作流常见问题解答
description: Campaign Classic 常见问题解答
feature: Troubleshooting, Workflows
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7d1bb3c6-d056-4212-9500-75459a0046fa
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 63%

---

# 工作流常见问题解答 {#workflows-faq}



了解如何使用 Adobe Campaign 工作流编排各种流程和任务。

## 创建工作流的主要步骤是什么？ {#what-are-the-key-steps-to-create-a-workflow-}

请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=zh-Hans){target="_blank"}以了解如何创建您的第一个工作流：了解概念与最佳实践，以便在Campaign中构建工作流。

## 如何在 Campaign 中导入数据？ {#how-can-i-import-data-in-campaign-}

在[此部分](../../platform/using/import-export-best-practices.md)中了解导入数据的最佳实践。

## 是否能监测工作流的执行？ {#can-i-monitor-workflow-execution-}

请参阅[Campaign v8文档]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution)以了解如何监测Campaign工作流的执行情况
.html){target="_blank"}。

## 如何使用工作流更新 Campaign 数据？ {#how-can-i-update-campaign-data-with-a-workflow-}

您可以对数据库中的数据执行大量更新、合并及插入操作。

请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html){target="_blank"}以了解详情。

## 如何利用数据管理功能？ {#how-can-i-leverage-data-management-capabilities-}

在 Adobe Campaign 中，您可利用更有效率、更灵活的工具，通过一组活动来解决复杂的定位问题。通过数据管理活动，您可以使用与合约、订阅、对投放的反应等相关信息，对与联系人的所有通信进行一致的管理。数据管理可让您在细分操作期间跟踪数据生命周期，特别是：

* 通过包括未在数据集市中建模的数据，简化及优化定位流程（创建新表：根据设定，对每个定位工作流进行本地扩展）。
* 保留和传送缓冲区计算内容，尤其是在目标建构阶段或进行数据库管理时。
* 访问外部数据库（可选）：在定位过程中考虑异构数据库。

请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}，了解如何设计复杂的目标以及处理结合数据管理工作流活动的数据。

## 我能自动发送个性化的邮件吗？ {#can-i-automate-personalized-messages-sending-}

查看[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/enrich-data.html?lang=zh-Hans){target="_blank"}，了解如何根据客户的最高竞争得分，向客户发送个性化的邮件。

## 如何使用工作流将受众分割到子集中？ {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}以了解如何将目标分割成多个子集。

## 如何通过外部文件更新收件人数据？ {#how-can-i-update-recipient-data-from-an-external-file-}

您可以使用外部文本文件中的值来修改 Campaign 表中的某些字段。

[单击此处了解如何操作](../../platform/using/import-operations-samples.md#example--enrich-the-values-with-those-of-an-external-file)。

## 如何识别和定位新的收件人？ {#how-can-i-identify-and-target-new-recipients-}

查看[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/using-aggregates.html){target="_blank"}，了解如何使用聚合自动识别数据库中最后添加的收件人，并向他们发送欢迎邮件。
