---
product: campaign
title: 定义正确的受众
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---

# 定义正确的受众 {#define-the-right-audience}

目标群体是关键：仔细构建列表，在流行的电子邮件客户端和移动设备上测试电子邮件，并确保电子邮件列表是最新的（地址不未知或过时）。 您还可以发送校样，以帮助设置完整的验证周期。

在此部分](../../delivery/using/steps-defining-the-target-population.md)中了解有关目标群体[的更多信息

## 定位正确的受众{#target-the-right-audience}

当您的内容准备就绪后，您需要仔细定义接收消息的人员。

为了使交付成功，您需要将最相关的个性化内容发送给适当的收件人。 Adobe Campaign使您能够构建最准确的目标：您可以根据收件人的年龄、本地化、购买的内容、他们单击了先前投放中的链接等内容来选择收件人。 通过Adobe Campaign，您还可以定义测试用户档案、控制组和种子地址，以确保目标正确。

## 目标映射{#target-mappings}

在Campaign Classic中，默认投放模板以&#x200B;**收件人**&#x200B;为目标。 Adobe Campaign为您的投放提供了其他目标映射，您可以根据自己的需求进行更改。

例如，您可以将用户档案通过社交网络收集的访客或订阅了信息服务的访客交付给。

此部分](../../delivery/using/selecting-a-target-mapping.md)中提供了这些映射。[

您还可以创建和使用自定义目标映射。 如需详细信息，请参阅[此部分](../../configuration/using/target-mapping.md)。

## 外部收件人{#external-recipients}

您可以将内容发送给存储在外部文件中而不是保存在数据库中的收件人。 在此部分](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)中了解更多[信息。

## 发送给订阅者{#send-to-subscribers}

要向新闻稿的订阅者发送消息，您可以直接将订阅者定位到相应的信息服务。 在此部分](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service)中了解更多[信息。


## 测试收件人和种子地址{#test-recipients-seed-addresses}

要测试投放，请在发送到主目标之前使用校样。

请确保选择适当的校样收件人，因为他们会验证消息的表单和内容。 [本节](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)介绍了定义校样收件人的步骤。

种子地址用于定位不符合所定义目标标准的收件人，以便在发送到主目标之前测试投放。 此部分](../../delivery/using/about-seed-addresses.md)中提供了这些参数。[

## 删除重复的地址{#deduplicate-addresses}

请务必避免使用重复的电子邮件地址，因为这可能会对您的目标产生影响：

* 在拆分目标时，可以多次发送同一消息。

* 如果收件人在收到消息后取消订阅，则其重复的用户档案仍将收到将来的消息。

删除地址重复项可保护您的发送信誉，并确保良好的隔离管理。

**相关主题：**

* [重复数据删除活动](../../workflow/using/deduplication.md)。
* [用例：使用重复数据删除活动的合并功能](../../workflow/using/deduplication-merge.md)

## 索引电子邮件地址{#index-addresses}

要优化应用程序中使用的SQL查询的性能，可以从数据模式的主元素中声明索引。

此部分](../../configuration/using/database-mapping.md#indexed-fields)中介绍了向电子邮件地址添加索引的步骤。[
