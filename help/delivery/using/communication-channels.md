---
title: 通信渠道
seo-title: 通信渠道
description: 通信渠道
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# 通信渠道{#communication-channels}

借助Adobe Campaign，您可以发送跨渠道营销活动，包括电子邮件、短信、LINE消息、推送通知和直邮，并使用各种专用报告衡量其 [效果](../../reporting/using/reports-on-deliveries.md#accessing-existing-reports)。 这些消息是通过发送来设计和发送的，并且可以为每个收件人个性化。

核心功能包括定位、消息定义和个性化、通信执行和相关的运营报告。 主要功能访问点是交付向导。 此访问点可带来Adobe Campaign涵盖的多项功能。

>[!NOTE]
>
>Adobe Campaign提供一套工具，用于监控您的投放能力并优化电子邮件发送。 有关详细信息，请参阅 [Deliverability入门和](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)[Deliverability管理](../../delivery/using/about-deliverability.md)。

交付发送可以通过准备交付和／或在工作流程过程中发送来实现自动化。 有关工作流中的交付类型活动的详细信息，请参 [阅此部分](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供以下交付渠道：

1. **电子邮件渠道**:电子邮件发送允许您向目标人群发送个性化的电子邮件。 请参阅关 [于电子邮件渠道](../../delivery/using/about-email-channel.md)。
1. **直邮渠道**:通过直邮发送，您可以生成包含目标人群数据的提取文件。 请参阅关 [于直邮渠道](../../delivery/using/about-direct-mail-channel.md)。
1. **移动渠道**:通过移动渠道发送，您可以向目标人群发送个性化的SMS或LINE消息。 请参阅 [SMS频道](../../delivery/using/sms-channel.md)。
1. **移动应用程序渠道**:移动应用程序交付允许您向iOS和Android系统发送通知。 请参阅移动应 [用程序渠道一章](../../delivery/using/about-mobile-app-channel.md) 。

   本页介绍了其 [他渠道](../../delivery/using/other-channels.md)。

   >[!NOTE]
   >
   >使用多个渠道取决于您的包。 请检查您的许可协议。

可以联机(通过 **电子邮件** 、移动渠道和推送通知之一)和脱 **机** （直邮渠道）进行交付。

根据渠道的不同，交付模式可以是：

* 通过Adobe Campaign直接进行成批交付（电子邮件渠道的默认模式）。
* 通过专家操作员进行外部分发，该操作员将收到由分发向导生成的输出文件（直邮渠道的默认模式）。

外部帐户通过节点进行 **[!UICONTROL Administration > Platform > External accounts]** 配置。 此配置应仅由专家用户执行。

## 电子邮件发送 {#email-deliveries}

电 [子邮件渠道](../../delivery/using/about-email-channel.md) 是Adobe Campaign中的核心渠道之一，允许您计划个性化电子邮件并将其发送到特定目标。

您可以发送不同类型的电子邮件：

* 单发电子邮件：您只需发送一次至定义的目标的电子邮件。 它们通常用于提升特定内容，该内容只准备和发送一次（新闻稿、促销电子邮件等）。
* 循环电子邮件：在营销活动中，定期发送相同的电子邮件，并定期汇总每个发送及其报告。 同一电子邮件会根据发送日期的合格目标发送，但通常会发送到其他目标。 一个常见的示例是生日电子邮件。 For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* 交易电子邮件：基于客户行为触发的统一电子邮件。 请参阅 [Transactional messaging](../../message-center/using/about-transactional-messaging.md)。

要了解分发使用情况和建议，请参阅Campaign [Delivery最佳实践](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)。

有关不同类型的交付的详细信息，请参 [阅此部分](../../delivery/using/types-of-deliveries.md)。

## 移动交付 {#mobile-deliveries}

Adobe Campaign允许您在移动 [设备上](../../delivery/using/sms-channel.md) 发 [送SMS和](../../delivery/using/line-channel.md) LINE消息。

对于SMS消息，您只能以文本格式创建、修改和个性化消息。 您还可以在发送SMS消息之前预览这些消息。

对于LINE消息，可以发送文本或图像和链接。

要将SMS或LINE消息传送到移动电话，您需要：

* 在渠道上或渠道上 **[!UICONTROL Mobile (SMS)]** 配置的外部帐 **[!UICONTROL LINE]** 户。
* 正确链接到此外部帐户的SMS或LINE交付模板。

## 推送通知 {#push-notifications}

Adobe Campaign允许您通过专用应用程序在iOS和Android [移动设备上](../../delivery/using/about-mobile-app-channel.md) ，发送个性化的分段推送通知。 执行配置和集成步骤后，即可创建和发送iOS和Android交付。 您还可以设计包含图像或视频的丰富通知。

## 直邮 {#direct-mail}

[直邮是线下渠道](../../delivery/using/about-direct-mail-channel.md) ，它允许您个性化和生成直邮提供商所需的文件。 它使您能够在客户旅程中混合使用线上和线下渠道。

在线渠道允许您创建消息（电子邮件、短信、移动应用交付等）并直接从Adobe Campaign将其发送给您的受众。 离线渠道则有所不同。 在准备直邮递送时，Adobe Campaign会生成一个文件，其中包含所有目标配置文件和选定的联系信息（例如邮政地址）。 然后，您可以将此文件发送给直接邮件提供商，由其负责实际发送。
