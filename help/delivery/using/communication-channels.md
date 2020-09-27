---
title: 通信渠道
seo-title: 通信渠道
description: 创建投放，在不同渠道上发送个性化信息。
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
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 11%

---


# 通信渠道{#communication-channels}

利用Adobe Campaign，您可以发送跨渠道活动，包括电子邮件、短信、LINE消息、推送通知和直接邮件，并使用各种专用报告衡量其 [有效性](../../reporting/using/delivery-reports.md)。 这些消息是通过投放设计和发送的，并且可以针对每个收件人进行个性化。

核心功能包括定位、消息定义和个性化、通信执行和相关的运营报告。 主要功能接入点是投放向导。 此接入点可实现Adobe Campaign涵盖的多种功能。

>[!NOTE]
>
>Adobe Campaign优惠一组工具，用于监控您的交付能力并优化电子邮件发送。 有关详细信息，请参 [阅交付性入门](../../delivery/using/deliverability-key-points.md) 和 [交付性管理](../../delivery/using/about-deliverability.md)。

投放发送可以通过准备投放和／或在工作流过程中发送它来实现自动化。 有关工作流中投放类型活动的详细信息，请参 [阅本节](../../workflow/using/about-action-activities.md)。

Adobe Campaign优惠以下投放渠道:

1. **电子邮件渠道**:电子邮件投放可让您向目标群发送个性化电子邮件。 请参阅关 [于电子邮件渠道](../../delivery/using/about-email-channel.md)。
1. **直邮渠道**:直接邮件投放允许您生成包含目标数据的提取文件。 请参阅关 [于直邮渠道](../../delivery/using/about-direct-mail-channel.md)。
1. **移动渠道**:移动渠道上的投放可让您向目标群发送个性化的SMS或LINE消息。 请参阅 [SMS渠道](../../delivery/using/sms-channel.md)。
1. **移动应用程序渠道**:移动应用程序投放允许您向iOS和Android系统发送通知。 请参阅移动 [应用程序渠道](../../delivery/using/about-mobile-app-channel.md) 一章。

   本页介绍了其 [他渠道](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)。

   >[!NOTE]
   >
   >使用多个渠道取决于您的包。 请核实您的许可协议。

投放可以 **联机** (通过电子邮件、移动渠道和推送通知之一)和 **脱机** (直邮渠道)。

根据渠道,投放模式可以是：

* 通过Adobe Campaign直接进行批量投放(电子邮件渠道的默认模式)。
* 外部投放通过专家操作员进行，该操作员将获得由投放向导生成的输出文件(直接邮件渠道的默认模式)。

外部帐户通过节点 **[!UICONTROL Administration > Platform > External accounts]** 配置。 此配置应仅由专家用户执行。

## 电子邮件投放 {#email-deliveries}

电子 [邮件渠道](../../delivery/using/about-email-channel.md) 是Adobe Campaign的核心渠道之一，允许您计划个性化电子邮件并发送给特定目标。

您可以发送不同类型的电子邮件：

* 单发电子邮件：您只需发送一次至定义目标的电子邮件。 它们通常用于推广将仅准备和发送一次的特定内容（新闻稿、促销电子邮件等）。
* 循环电子邮件：在活动中，定期发送相同的电子邮件，并定期聚合每次发送及其报告。 同一电子邮件会根据发送日期的合格目标发送，但通常会发送至其他目标。 一个常见的示例是生日电子邮件。 For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* 交易电子邮件：基于客户行为触发的统一电子邮件。 请参阅 [Transactional Messaging](../../message-center/using/about-transactional-messaging.md)。

要了解投放使用情况和建议，请查阅活动 [投放最佳实践](../../delivery/using/delivery-best-practices.md)。

有关不同投放类型的详细信息，请参 [阅本节](#types-of-deliveries)。

## 移动投放 {#mobile-deliveries}

Adobe Campaign允许您在 [手机上](../../delivery/using/sms-channel.md) 提 [供SMS](../../delivery/using/line-channel.md) 和LINE消息。

对于SMS消息，您只能以文本格式创建、修改和个性化消息。 您还可以在发送SMS消息之前预览这些消息。

对于LINE消息，可以发送文本或图像和链接。

要将SMS或LINE消息传送到移动电话，您需要：

* 在外部帐户上或 **[!UICONTROL Mobile (SMS)]** 渠道上配置的 **[!UICONTROL LINE]** 渠道。
* 正确链接到此投放模板的SMS或LINE外部帐户。

## 推送通知 {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](../../delivery/using/about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. 执行配置和集成步骤后，即可创建和发送iOS和Android投放。 您还可以设计包含图像或视频的丰富通知。

## 直邮 {#direct-mail}

[直邮是一种线下渠道，用于生成直邮提供商所需的个性化文件。](../../delivery/using/about-direct-mail-channel.md)利用这种手段，可将线上和线下渠道有机地结合，用在客户历程中。

利用线上渠道，可创建消息（电子邮件、短信、移动应用投放等）并直接从 Adobe Campaign 发送至受众。线下渠道则不同。在准备直邮投放时，Adobe Campaign 会生成一个文件，其中包含了所有定向的用户档案和选定的联系信息（例如邮政地址）。然后，您可以将此文件发送给直邮提供商，由其负责发送纸质信函。

## 其他渠道 {#other-channels}

Adobe Campaign优惠代理或电话投放模板，用于创建外部投放。 使用这些渠道意味着您设置了专门的方法来处理输出文件。 配置步骤与直接邮件 [渠道相同](../../delivery/using/about-direct-mail-channel.md)。

此外，“其他”类型投放使用不执行进程的特定技术模板：这样，他们就可以管理在Adobe Campaign平台之外执行的营销操作。

此渠道没有具体机制。 它是一个通用渠道，它具有自己的外部帐户路由选项、投放模板类型和活动工作流活动，就像Adobe Campaign中提供的任何其他通信渠道一样。

此渠道仅用于描述性目的，例如，定义要跟踪在非Adobe Campaign工具中执行的活动的目标的投放。

## 投放类型{#types-of-deliveries}

活动中有三种类型的投放对象：

### 单一投放 {#single-delivery}

投放 **是执** 行一次的独立投放对象。 它可以重复、重新准备，但只要它处于最终状态（取消、停止、完成），它就不能再使用。

投放可以从投放的列表创建，也可以通过投放活动在工作流 [中创](../../workflow/using/delivery.md) 建。

工作流还根据您要使用的投放类型提供特定的渠道活动。 For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### 循环投放 {#recurring-delivery}

重复 **投放** ，允许您在每次执行活动时创建新投放。 这可避免您为重复投放创建新任务。

例如，如果每月运行一次此类活动，则一年后将有12个投放。

循环投放通过循环投放活动在 [工作流内创建](../../workflow/using/recurring-delivery.md)。 本节介绍了此活动的示例： [在定位工作流中创建重复投放](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

### 连续投放 {#continuous-delivery}

连 **续投放** 允许您向现有投放添加新收件人，这样就无需在每次执行时创建新投放。

如果投放中的信息发生更改（内容、名称等），则在投放执行时将创建新的投放对象。 如果未更改任何信息，则重复使用同一投放对象，并将投放和跟踪日志添加到同一对象中。

例如，如果每月运行一次此类活动，则一年后将有一个投放(前提是未对投放进行任何更改)。

连续投放通过连续投放活动在 [工作流中创建](../../workflow/using/continuous-delivery.md)。
