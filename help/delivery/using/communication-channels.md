---
product: campaign
title: 通信渠道
description: 创建投放，在不同渠道上发送个性化信息
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 20%

---

# 通信渠道{#communication-channels}

借助Adobe Campaign，您可以发送跨渠道活动内容，包括电子邮件、短信、LINE消息、推送通知和直邮，并使用各种专门设置来衡量其有效性 [报表](../../reporting/using/delivery-reports.md). 这些消息通过投放设计和发送，并且可以针对每个收件人进行个性化。

核心功能包括定位、消息定义和个性化、通信执行和相关的运营报告。主要功能访问点是投放向导。 此接入点可导向 Adobe Campaign 涵盖的多种功能。

>[!NOTE]
>
>Adobe Campaign提供了一组工具来监控投放能力并优化电子邮件发送。 在[此章节](about-deliverability.md)中了解更多信息。

通过在工作流中准备投放和/或发送投放，可以自动进行投放发送。 有关工作流中投放类型活动的更多信息，请参阅 [本节](../../workflow/using/about-action-activities.md).

Adobe Campaign提供以下交付渠道：

1. **电子邮件渠道**：电子邮件投放可让您向目标群体发送个性化电子邮件。请参阅 [关于电子邮件渠道](about-email-channel.md).
1. **直邮渠道**：直邮投放允许您生成包含目标群体数据的提取文件。请参阅 [关于直邮渠道](about-direct-mail-channel.md).
1. **移动渠道**：移动渠道中的投放可让您向目标群体发送个性化的SMS或LINE消息。 请参阅 [短信渠道](sms-channel.md).
1. **移动应用程序渠道**：移动应用程序投放可让您向 iOS 和 Android 系统发送通知。请参阅 [移动应用程序渠道](about-mobile-app-channel.md) 章节。

   有关其他渠道的介绍，请参见 [此页面](steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >可用渠道的数量取决于您的合同。 请核实您的许可协议。

可以执行投放 **在线** （通过电子邮件、移动渠道之一和推送通知），以及 **离线** （直邮渠道）。

根据渠道的不同，投放模式可以是：

* 通过Adobe Campaign直接批量投放（电子邮件渠道的默认模式）。
* 通过专家操作员进行外部投放，操作员将获得投放向导生成的输出文件（直邮渠道的默认模式）。

外部帐户是通过 **[!UICONTROL Administration > Platform > External accounts]** 节点。 此配置应仅由专家用户执行。

## 电子邮件投放 {#email-deliveries}

此 [电子邮件渠道](about-email-channel.md) 是Adobe Campaign中的核心渠道之一，允许您向特定目标计划和发送个性化电子邮件。

您可以发送不同类型的电子邮件：

* 单次发送电子邮件：可发送给已定义目标的电子邮件。 它们通常用于促销只需准备并发送一次的特定内容（新闻稿、促销电子邮件等）。
* 定期电子邮件：在营销活动中，定期发送相同的电子邮件，并定期汇总每个发送及其报告。 同一电子邮件会发送，但通常根据发送日期的符合条件目标发送给其他目标。 一个常见示例是生日电子邮件。 有关详细信息，请参见 [定期投放](../../workflow/using/recurring-delivery.md).
* 事务性电子邮件：根据客户的行为触发的统一电子邮件。 请参阅 [事务性消息传递](../../message-center/using/about-transactional-messaging.md).

要了解投放使用方法和建议，请查阅Campaign [投放最佳实践](delivery-best-practices.md).

有关不同类型投放的更多信息，请参阅 [本节](#types-of-deliveries).

## 移动投放 {#mobile-deliveries}

Adobe Campaign允许您交付 [短信](sms-channel.md) 和 [折线图](line-channel.md) 手机上的消息。

对于短信消息，您可以仅以文本格式创建、修改和个性化消息。 您还可以在发送短信之前预览短信。

对于LINE消息，可以发送文本或图像和链接。

要将SMS或LINE消息投放到手机，您需要：

* 在上配置的外部帐户 **[!UICONTROL Mobile (SMS)]** 频道或在 **[!UICONTROL LINE]** 渠道。
* 正确链接到此外部帐户的SMS或LINE投放模板。

## 推送通知 {#push-notifications}

Adobe Campaign允许您发送个性化和分段的 [推送通知](about-mobile-app-channel.md) 在iOS和Android移动设备上，通过专用应用程序访问。 执行配置和集成步骤后，即可创建和发送iOS和Android投放。 您还可以设计包含图像或视频的丰富通知。

## 直邮 {#direct-mail}

[直邮是一种线下渠道，用于生成直邮提供商所需的个性化文件。](about-direct-mail-channel.md)利用这种手段，可将线上和线下渠道有机地结合，用在客户历程中。

利用线上渠道，可创建消息（电子邮件、短信、移动应用投放等）并直接从 Adobe Campaign 发送至受众。线下渠道则不同。在准备直邮投放时，Adobe Campaign 会生成一个文件，其中包含了所有定向的用户档案和选定的联系信息（例如邮政地址）。然后，您可以将此文件发送给直邮提供商，由其负责发送纸质信函。

## 其他渠道 {#other-channels}

Adobe Campaign提供电话投放模板，用于创建外部投放。 使用此渠道意味着您设置专用方法来处理输出文件。 配置步骤与相同 [直邮渠道](about-direct-mail-channel.md).

>[!NOTE]
>
>电话渠道不可开箱即用。 其实施需要与Adobe咨询或Adobe合作伙伴合作。 有关更多信息，请联系您的Adobe代表。

此外，“其他”类型投放使用不会执行流程的特定技术模板：这使他们能够管理在Adobe Campaign平台之外执行的营销操作。

此渠道没有特定的机制。 该渠道与在Adobe Campaign中提供的任何其他通信渠道一样，具有自己的外部帐户路由选项、投放模板类型和活动工作流活动。

此渠道仅用于描述性目的，例如，定义要跟踪在Adobe Campaign以外的工具中执行的营销活动目标的投放。

## 投放类型{#types-of-deliveries}

Campaign中有三种类型的投放对象：

### 单个投放 {#single-delivery}

A **投放** 是一个独立投放对象，只执行一次。 它可以重复，再次准备，但只要它处于最终状态（已取消、已停止、已完成），就无法重复使用。

可以从投放列表创建投放，也可以通过在工作流中创建投放 [投放](../../workflow/using/delivery.md) 活动。

工作流还可根据要使用的渠道类型提供特定的投放活动。 有关这些活动的更多信息，请参阅 [本节](../../workflow/using/cross-channel-deliveries.md).

### 循环投放 {#recurring-delivery}

A **循环投放** 用于每次执行活动时创建新投放。 这可让您不必为周期性任务创建新投放。

例如，如果您每月运行一次此类活动，那么一年后最终将有12次投放。

定期投放是通过在工作流中创建的 [循环投放活动](../../workflow/using/recurring-delivery.md). 此部分中介绍了正在使用的此活动的示例： [在定位工作流中创建循环投放](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### 连续投放 {#continuous-delivery}

A **连续投放** 允许您将新收件人添加到现有投放，从而避免每次执行投放时都创建新投放。

如果投放中的信息发生更改（内容、名称等），则会在投放执行时创建新投放对象。 如果未更改任何信息，则将重用同一投放对象，并将投放和跟踪日志添加到同一对象中。

例如，如果您每月运行一次此类活动，那么一年后您将只运行一次投放（前提是您未对投放进行任何更改）。

连续投放是通过在工作流中创建的 [连续投放活动](../../workflow/using/continuous-delivery.md).
