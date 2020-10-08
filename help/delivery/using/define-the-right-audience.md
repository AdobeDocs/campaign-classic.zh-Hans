---
title: 定义正确的受众
seo-title: 定义正确的受众
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 1%

---


# 定义正确的受众 {#define-the-right-audience}

目标人口是关键：仔细构建列表，在流行的电子邮件客户端和移动设备上测试电子邮件，并确保电子邮件列表始终处于最新状态（没有未知或过时的地址）。 您还可以发送帮助设置完整验证周期的验证。

在本节中进一步了 [解目标群](../../delivery/using/steps-defining-the-target-population.md)

## 目标正确的受众 {#target-the-right-audience}

当您的内容准备就绪后，您需要仔细定义将收到您的消息的人。

为了使投放成功，您希望将最相关的个性化内容发送给正确的收件人。 Adobe Campaign使您能够构建最准确的目标:您可以根据收件人的年龄、本地化、他们购买的商品，如果他们点击了先前投放中的链接，等等。 使用Adobe Campaign，您还可以定义测试用户档案、对照组和种子地址，以确保目标正确。

## 目标映射 {#target-mappings}

在Campaign Classic中，默认情况下为投放模板收件人 **目标**。 Adobe Campaign为投放优惠其他目标映射，您可以根据需要进行更改。

例如，您可以将用户档案交付给通过社交网络收集的访客或订阅信息服务的访客。

本节将介绍这 [些映射](../../delivery/using/selecting-a-target-mapping.md)。

您还可以创建和使用自定义目标映射。 如需详细信息，请参阅[此部分](../../configuration/using/target-mapping.md)。

## 外部收件人 {#external-recipients}

您可以将存储在外部文件而非保存在收件人库中的传送到数据库。 在本节 [中了解更多](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

## 发送给您的订阅者 {#send-to-subscribers}

要向新闻稿的订阅者发送消息，您可以直接将订阅者目标到相应的信息服务。 在本节 [中了解更多](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service)。


## 测试收件人和种子地址 {#test-recipients-seed-addresses}

要测试投放，请在发送到主目标前使用验证。

请确保您选择适当的验证收件人，因为它们会验证表单和消息的内容。 定义验证收件人的步骤将在 [本节中介绍](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)。

种子地址用于目标不符合定义的目标标准的收件人，以便在发送到主目标之前测试投放。 本节将介 [绍这些内容](../../delivery/using/about-seed-addresses.md)。

## 消除重复地址 {#deduplicate-addresses}

请务必避免重复电子邮件地址，因为这可能会影响您的目标:

* 在拆分目标时，可以多次发送同一消息。

* 如果收件人在收到消息后取消订阅，其重复用户档案仍将收到将来的消息。

消除重复地址可保护您的发送信誉并确保良好的隔离管理。

通过此用 [例了解更多信息](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)。

## 索引电子邮件地址 {#index-addresses}

要优化应用程序中使用的SQL查询的性能，可以从数据模式的主元素中声明索引。

本节将介绍向电子邮件地址添加索引 [的步骤](../../configuration/using/database-mapping.md#indexed-fields)。
