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
source-git-commit: c1f7ff6a281c2830ac23ad995b750dc09ade5e92
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 1%

---


# 通信渠道{#communication-channels}

利用Adobe Campaign，您可以发送跨渠道活动，包括电子邮件、短信、LINE消息、推送通知和直接邮件，并使用各种专用报告衡量其 [有效性](../../reporting/using/delivery-reports.md)。 这些消息是通过投放设计和发送的，并且可以针对每个收件人进行个性化。

核心功能包括定位、消息定义和个性化、通信执行和相关的运营报告。 主要功能接入点是投放向导。 此接入点可实现Adobe Campaign涵盖的多种功能。

>[!NOTE]
>
>Adobe Campaign优惠一组工具，用于监控您的交付能力并优化电子邮件发送。 有关详细信息，请参 [阅交付性入门](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 和 [交付性管理](../../delivery/using/about-deliverability.md)。

投放发送可以通过准备投放和／或在工作流过程中发送它来实现自动化。 有关工作流中投放类型活动的详细信息，请参 [阅本节](../../workflow/using/about-action-activities.md)。

Adobe Campaign优惠以下投放渠道:

1. **电子邮件渠道**: 电子邮件投放可让您向目标群发送个性化电子邮件。 请参阅关 [于电子邮件渠道](../../delivery/using/about-email-channel.md)。
1. **直邮渠道**: 直接邮件投放允许您生成包含目标数据的提取文件。 请参阅关 [于直邮渠道](../../delivery/using/about-direct-mail-channel.md)。
1. **移动渠道**: 移动渠道上的投放可让您向目标群发送个性化的SMS或LINE消息。 请参阅 [SMS渠道](../../delivery/using/sms-channel.md)。
1. **移动应用程序渠道**: 移动应用程序投放允许您向iOS和Android系统发送通知。 请参阅移动 [应用程序渠道](../../delivery/using/about-mobile-app-channel.md) 一章。

   本页介绍了其 [他渠道](../../delivery/using/communication-channels.md#other-channels)。

   >[!NOTE]
   >
   >使用多个渠道取决于您的包。 请检查您的许可协议。

投放可以 **联机** (通过电子邮件、移动渠道和推送通知之一)和 **脱机** (直邮渠道)。

根据渠道,投放模式可以是：

* 通过Adobe Campaign直接进行批量投放(电子邮件渠道的默认模式)。
* 外部投放通过专家操作员进行，该操作员将获得由投放向导生成的输出文件(直接邮件渠道的默认模式)。

外部帐户通过节点 **[!UICONTROL Administration > Platform > External accounts]** 配置。 此配置应仅由专家用户执行。

## 电子邮件投放 {#email-deliveries}

电子 [邮件渠道](../../delivery/using/about-email-channel.md) 是Adobe Campaign的核心渠道之一，允许您计划个性化电子邮件并发送给特定目标。

您可以发送不同类型的电子邮件：

* 单发电子邮件： 您只需发送一次至定义目标的电子邮件。 它们通常用于推广将仅准备和发送一次的特定内容（新闻稿、促销电子邮件等）。
* 循环电子邮件： 在活动中，定期发送相同的电子邮件，并定期聚合每次发送及其报告。 同一电子邮件会根据发送日期的合格目标发送，但通常会发送至其他目标。 一个常见的示例是生日电子邮件。 For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* 交易电子邮件： 基于客户行为触发的统一电子邮件。 请参阅 [Transactional Messaging](../../message-center/using/about-transactional-messaging.md)。

要了解投放使用情况和建议，请查阅活动 [投放最佳实践](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)。

有关不同投放类型的详细信息，请参 [阅本节](../../delivery/using/types-of-deliveries.md)。

## 移动投放 {#mobile-deliveries}

Adobe Campaign允许您在 [手机上](../../delivery/using/sms-channel.md) 提 [供SMS](../../delivery/using/line-channel.md) 和LINE消息。

对于SMS消息，您只能以文本格式创建、修改和个性化消息。 您还可以在发送SMS消息之前预览这些消息。

对于LINE消息，可以发送文本或图像和链接。

要将SMS或LINE消息传送到移动电话，您需要：

* 在外部帐户上或 **[!UICONTROL Mobile (SMS)]** 渠道上配置的 **[!UICONTROL LINE]** 渠道。
* 正确链接到此投放模板的SMS或LINE外部帐户。

## 推送通知 {#push-notifications}

Adobe Campaign允许您通过专用应用程 [序在iOS](../../delivery/using/about-mobile-app-channel.md) 和Android移动设备上发送个性化的分段推送通知。 执行配置和集成步骤后，即可创建和发送iOS和Android投放。 您还可以设计包含图像或视频的丰富通知。

## 直邮 {#direct-mail}

[直接邮寄](../../delivery/using/about-direct-mail-channel.md) 是一种离线渠道，它允许您个性化并生成直接邮寄提供商所需的文件。 它使您能够在客户旅程中混合线上和线下渠道。

在线渠道允许您创建消息(电子邮件、短信、移动应用投放等) 并直接从受众发送给Adobe Campaign。 离线渠道则不同。 在准备直邮投放时，Adobe Campaign会生成一个文件，其中包括所有目标用户档案和所选联系信息（例如邮政地址）。 然后，您可以将此文件发送给直接邮件提供商，由其负责实际发送。

## 其他渠道 {#other-channels}

Adobe Campaign优惠代理或电话投放模板，用于创建外部投放。 使用这些渠道意味着您设置了专门的方法来处理输出文件。 配置步骤与直接邮件 [渠道相同](../../delivery/using/about-direct-mail-channel.md)。

此外，“其他”类型投放使用不执行进程的特定技术模板： 这样，他们就可以管理在Adobe Campaign平台之外执行的营销操作。

此渠道没有具体机制。 它是一个通用渠道，它具有自己的外部帐户路由选项、投放模板类型和活动工作流活动，就像Adobe Campaign中提供的任何其他通信渠道一样。

此渠道仅用于描述性目的，例如，定义要跟踪在非Adobe Campaign工具中执行的活动的目标的投放。
