---
product: campaign
title: 定义正确的受众
description: 了解选择受众时的最佳实践
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Audiences
role: User
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 4%

---

# 定义正确的受众 {#define-the-right-audience}

目标群体是关键：仔细构建列表，在常用的电子邮件客户端和移动设备上测试电子邮件，并确保电子邮件列表是最新的（不含未知或过时的地址）。 您还可以发送校样来帮助设置完整的验证周期。

了解有关目标群体的更多信息 [在此部分中](steps-defining-the-target-population.md)

## 定位正确的受众 {#target-the-right-audience}

准备好内容后，您需要仔细定义接收消息的人员。

为了成功交付，您需要将最相关的个性化内容发送给正确的收件人。 Adobe Campaign使您能够构建最准确的目标：您可以根据收件人的年龄、本地化、购买内容、是否在上一次投放中单击链接等选择收件人。 通过Adobe Campaign，您还可以定义测试用户档案、控制组和种子地址，以确保您的目标正确。

## 目标映射 {#target-mappings}

在Campaign Classic中，默认投放模板目标 **收件人**. Adobe Campaign为您的投放提供了其他目标映射，您可以根据需要更改这些映射。

例如，您可以向通过社交网络收集用户档案的访客或订阅了信息服务的访客投放。

这些映射将呈现 [在此部分中](selecting-a-target-mapping.md).

您还可以创建和使用自定义的目标映射。 如需详细信息，请参阅[此小节](../../configuration/using/target-mapping.md)。

## 外部收件人 {#external-recipients}

您可以向存储在外部文件中而不是数据库中保存的收件人投放。 了解详情 [在此部分中](steps-defining-the-target-population.md#selecting-external-recipients).

## 发送给订阅者 {#send-to-subscribers}

要向新闻稿的订阅者发送消息，可以直接将订阅者定位到相应的信息服务。 了解详情 [在此部分中](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## 测试收件人和种子地址 {#test-recipients-seed-addresses}

要测试您的投放，请在发送到主目标之前使用验证。

确保选择适当的校样收件人，因为他们验证消息的表单和内容。 介绍了定义校样收件人的步骤 [在此部分中](steps-defining-the-target-population.md#selecting-the-proof-target).

种子地址用于定向不符合所定义目标标准的收件人，以便在发送到主目标之前测试投放。 它们会呈现 [在此部分中](about-seed-addresses.md).

## 删除重复地址 {#deduplicate-addresses}

请务必避免电子邮件地址重复，因为这可能会对目标产生影响：

* 分割目标时，同一消息可能会发送多次。

* 如果收件人在收到消息后取消订阅，则其重复的用户档案仍会收到未来的消息。

对地址进行重复数据删除可保护您的发送信誉并确保良好的隔离管理。

**相关主题：**

* [重复数据删除活动](../../workflow/using/deduplication.md).
* [用例：使用外部重复数据删除活动的合并功能](../../workflow/using/deduplication-merge.md)

## 为电子邮件地址编制索引 {#index-addresses}

为了优化应用程序中使用的SQL查询的性能，可以从数据架构的主元素声明索引。

介绍了向电子邮件地址添加索引的步骤 [在此部分中](../../configuration/using/database-mapping.md#indexed-fields).
