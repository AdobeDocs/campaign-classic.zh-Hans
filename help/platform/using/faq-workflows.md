---
title: 工作流常见问题解答
seo-title: 使用工作流自动完成流程并管理数据
description: Campaign Classic常见问题解答
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 78%

---


# 工作流常见问题解答 {#workflows-faq}

了解如何使用 Adobe Campaign 工作流编排各种流程和任务。

## What are the key steps to create a workflow? {#what-are-the-key-steps-to-create-a-workflow-}

[单击此处了解如何创建首个工作流](../../workflow/using/building-a-workflow.md)：了解概念与最佳实践，以便在 Campaign 中构建工作流。

## How can I import data in Campaign? {#how-can-i-import-data-in-campaign-}

在[此部分](../../workflow/using/importing-data.md)了解通过 Campaign 工作流导入数据的最佳实践。

## Can I monitor workflow execution? {#can-i-monitor-workflow-execution-}

在[本页面](../../workflow/using/starting-a-workflow.md)中了解如何监视 Campaign 工作流执行情况。

## How can I update Campaign data with a workflow? {#how-can-i-update-campaign-data-with-a-workflow-}

您可以对数据库中的数据执行大量更新、合并及插入操作。

[单击此处了解更多信息](../../workflow/using/update-data.md)。

## How can I leverage data management capabilities? {#how-can-i-leverage-data-management-capabilities-}

在 Adobe Campaign 中，您可利用更有效率、更灵活的工具，通过一组活动来解决复杂的定位问题。通过数据管理活动，您可以使用与合约、订阅、对投放的反应等相关信息，对与联系人的所有通信进行一致的管理。数据管理可让您在细分操作期间跟踪数据生命周期，特别是：

* 通过包括未在数据集市中建模的数据，简化及优化定位流程（创建新表：根据设定，对每个定位工作流进行本地扩展）。
* 保留和传送缓冲区计算内容，尤其是在目标建构阶段或进行数据库管理时。
* 访问外部数据库（可选）：在定位过程中考虑异构数据库。

[单击此处了解更多信息](../../workflow/using/targeting-data.md#data-management)，并且能够设计复杂的目标，使用与数据管理工作流活动相结合的数据。

## Can I automate personalized messages sending? {#can-i-automate-personalized-messages-sending-}

参阅[此用例](../../workflow/using/enriching-data.md)，根据客户的最高竞争分数，向客户发送个性化的邮件。

## How can I split an audience in subsets with a workflow? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

在[此部分](../../workflow/using/split.md)中了解如何将目标分割成多个子集。

## How can I update recipient data from an external file? {#how-can-i-update-recipient-data-from-an-external-file-}

您可以使用外部文本文件中的值来修改 Campaign 表中的某些字段。

[单击此处了解如何操作](../../platform/using/importing-data.md#example--enrich-the-values-with-those-of-an-external-file)。

## How can I identify and target new recipients? {#how-can-i-identify-and-target-new-recipients-}

[此用例](../../workflow/using/using-aggregates.md)可帮助您了解如何使用汇总功能自动确定数据库中最后添加的收件人，并向他们发送欢迎邮件。
