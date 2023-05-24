---
product: campaign
title: 测试和发送常见问题解答
description: Campaign Classic 常见问题解答
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 98%

---

# 验证、发送和跟踪消息 {#validate-send-track}



## 测试和验证 {#test-and-validate-before-sending}

了解在发送邮件前，如何在 Adobe Campaign 中执行测试和验证步骤。

### 什么是投放分析? {#what-is-the-delivery-analysis-}

投放分析是指计算目标群体以及准备投放内容的阶段。完成该阶段后便可发送投放内容了。查阅日志可确保所有事项都正确无误。

[单击此处了解更多信息](../../delivery/using/steps-validating-the-delivery.md)。

### 为何要创建验证？ {#why-should-i-create-proofs-}

Adobe 强烈建议您先创建验证邮件，在将邮件发送到主目标前先行在审批组上测试投放。然后可以确认邮件内容、个性化和投放参数。

[单击此处了解更多信息](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 如何在 Adobe Campaign 中使用种子地址？ {#how-to-use-seed-addresses-in-adobe-campaign-}

种子地址用于定位不符合既定目标标准的收件人。这些收件人会被添加到目标中：可直接在投放或营销活动中导入或创建这些收件人。如果是直邮投放，则会在提取期间添加，在输出文档中进行混合。

这样做有以下好处：

* 使用收件人用户档案中的数据随机替代字段：例如，您可以在种子地址部分中仅输入电子邮件地址。
* 使用具有数据管理功能的工作流时，可在种子地址级别输入投放中已处理的其他数据，以强制使用该值：这可以作为随机值替代的另一做法。

[单击此处了解有关种子地址的更多信息](../../delivery/using/about-seed-addresses.md)。

### 如何设置发送邮件前的批准流程？ {#how-can-i-set-up-an-approval-process-before-sending-messages-}

为了检测邮件配置中可能出现的错误，Adobe 强烈建议您设置投放验证周期。尽可能频繁地向测试收件人发送验证内容，确保内容已获得批准。每次进行变更时都应发送验证内容，以批准内容。

[单击此处了解更多信息](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 什么是类型规则？ {#what-is-a-typology-rule-}

为了避免营销活动之间发生冲突，Adobe Campaign 可以应用特定的限制规则来测试各种活动组合。这可确保在遵守公司通信政策的同时，发送最符合客户需求及期望的邮件。

[单击此处了解更多信息](../../campaign-opt/using/about-campaign-typologies.md)。

## 发送您的邮件 {#send-your-messages}

了解如何使用 Adobe Campaign 在各个渠道中发送邮件。

### 如何分批次发送电子邮件？ {#how-can-i-send-emails-in-waves-}

向较大的群体发送投放内容前，您可以通过[配置批次](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)将邮件分为多个批次，从而平衡负载。

### 在 Campaign 中创建电子邮件有哪些重要步骤？ {#which-are-the-key-steps-to-create-an-email-in-campaign-}

创建并验证电子邮件投放内容后，您就可以发送它了。您可以决定立即将电子邮件发送给主要目标，还是计划好在以后进行投放。如有需要，也可以先估计目标群体规模。

[单击此处了解更多信息](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 如何计划一次投放？ {#how-to-schedule-a-delivery-}

您可以推迟邮件的投放，以便计划内容的投放或管理销售压力并避免过度营销。

[单击此处了解更多信息](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending)。

### 我可以将附件添加到电子邮件吗？ {#can-i-add-an-attachment-to-emails-}

使用 Campaign Classic，您可以在电子邮件中加入个性化的附件。

[单击此处了解有关电子邮件附件的更多信息](../../delivery/using/attaching-files.md)。

## 跟踪邮件并衡量其的影响 {#track-your-messages-and-measure-their-impact}

发送邮件后，了解如何通过 Adobe Campaign 跟踪和衡量邮件的影响。

### 如何在电子邮件投放中设置跟踪链接？ {#how-can-i-configure-tracked-links-in-an-email-delivery-}

对于每次投放，您可以跟踪邮件是否收到，以及邮件内容中插入的链接是否被点击。这样即可在目标投放行动实施后，跟踪收件人的行为。

对于每个邮件的 URL，您可以选择是否启动跟踪、变更链接标签、根据报告需求对链接进行分类等。

[单击此处了解有关](../../delivery/using/about-message-tracking.md)如何通过 Campaign Classic 跟踪邮件的更多信息。

### 我在哪里可以访问投放内容和跟踪日志？ {#where-can-i-access-delivery-and-tracking-logs-}

了解如何跟踪投放内容并了解收件人的行为 [从此页面](../../delivery/using/delivery-dashboard.md).

### 从何处获得投放报告？ {#where-can-i-get-delivery-reports-}

Adobe Campaign 随附了一组报告，用于监视投放并跟踪邮件。

[单击此处了解有关内置报告的更多信息](../../reporting/using/delivery-reports.md)。

### Adobe Campaign 如何确定和管理隔离地址？ {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign 管理了一个隔离地址列表。在投放分析时，默认情况下会将其地址已被隔离的收件人排除在外，不会将其设为目标。举例来说，信箱已满或地址不存在时，可以隔离某个电子邮件地址。

[单击此处了解有关隔离管理的更多信息](../../delivery/using/understanding-quarantine-management.md)。
