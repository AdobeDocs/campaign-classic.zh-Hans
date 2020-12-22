---
solution: Campaign Classic
product: campaign
title: 定义正确的受众
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: fe7ff64d24113e026a47aa1c9f08daacce2b383e
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---


# 定义正确的受众 {#define-the-right-audience}

目标人口是关键：仔细构建列表，在流行的电子邮件客户端和移动设备上测试电子邮件，并确保电子邮件列表始终处于最新状态（没有未知或过时的地址）。 您还可以发送帮助设置完整验证周期的验证。

在本节](../../delivery/using/steps-defining-the-target-population.md)中进一步了解目标群体[

## 目标右受众{#target-the-right-audience}

当您的内容准备就绪后，您需要仔细定义将收到您的消息的人。

为了使投放成功，您希望将最相关的个性化内容发送给正确的收件人。 Adobe Campaign使您能够构建最准确的目标:您可以根据收件人的年龄、本地化、他们购买的商品，如果他们点击了先前投放中的链接，等等。 使用Adobe Campaign，您还可以定义测试用户档案、对照组和种子地址，以确保目标正确。

## 目标映射{#target-mappings}

在Campaign Classic中，默认为投放模板目标&#x200B;**收件人**。 Adobe Campaign为投放优惠其他目标映射，您可以根据需要进行更改。

例如，您可以将用户档案交付给通过社交网络收集的访客或订阅信息服务的访客。

这些映射在本节](../../delivery/using/selecting-a-target-mapping.md)中显示为[。

您还可以创建和使用自定义目标映射。 如需详细信息，请参阅[此部分](../../configuration/using/target-mapping.md)。

## 外部收件人{#external-recipients}

您可以将存储在外部文件而非保存在收件人库中的传送到数据库。 请阅读本节[了解更多信息。](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

## 发送给您的订阅者{#send-to-subscribers}

要向新闻稿的订阅者发送消息，您可以直接将订阅者目标到相应的信息服务。 请阅读本节[了解更多信息。](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service)


## 测试收件人和种子地址{#test-recipients-seed-addresses}

要测试投放，请在发送到主目标前使用验证。

请确保您选择适当的验证收件人，因为它们会验证表单和消息的内容。 定义验证收件人的步骤在本节[中介绍。](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)

种子地址用于目标不符合定义的目标标准的收件人，以便在发送到主目标之前测试投放。 在本节](../../delivery/using/about-seed-addresses.md)中显示它们[。

## 消除重复地址{#deduplicate-addresses}

请务必避免重复电子邮件地址，因为这可能会影响您的目标:

* 在拆分目标时，可以多次发送同一消息。

* 如果收件人在收到消息后取消订阅，其重复用户档案仍将收到将来的消息。

消除重复地址可保护您的发送信誉并确保良好的隔离管理。

**相关主题：**

* [外部重复数据删除活动](../../workflow/using/deduplication.md)。
* [用例：使用外部重复数据删除活动的合并功能](../../workflow/using/deduplication-merge.md)

## 索引电子邮件地址{#index-addresses}

要优化应用程序中使用的SQL查询的性能，可以从数据模式的主元素中声明索引。

在此部分[中显示向电子邮件地址添加索引的步骤。](../../configuration/using/database-mapping.md#indexed-fields)
