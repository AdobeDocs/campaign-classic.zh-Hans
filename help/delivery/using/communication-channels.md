---
product: campaign
title: 通信渠道
description: 创建投放，在不同渠道上发送个性化信息
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 20%

---

# 通信渠道{#communication-channels}



借助Adobe Campaign，您可以发送跨渠道营销活动，包括电子邮件、短信、LINE消息、推送通知和直邮，并使用各种专用的 [报告](../../reporting/using/delivery-reports.md). 这些消息通过投放设计和发送，并且可以针对每个收件人进行个性化。

核心功能包括定位、消息定义和个性化、通信执行和相关的运营报告。主要功能接入点是投放向导。 此接入点可导向 Adobe Campaign 涵盖的多种功能。

>[!NOTE]
>
>Adobe Campaign提供一组工具来监控您的投放能力并优化电子邮件发送。 在[此章节](about-deliverability.md)中了解更多信息。

通过准备投放和/或在工作流过程中发送投放，可自动发送投放。 有关工作流中投放类型活动的更多信息，请参阅 [此部分](../../workflow/using/about-action-activities.md).

Adobe Campaign提供以下交付渠道：

1. **电子邮件渠道**：电子邮件投放可让您向目标群体发送个性化电子邮件。请参阅 [关于电子邮件渠道](about-email-channel.md).
1. **直邮渠道**：直邮投放允许您生成包含目标群体数据的提取文件。请参阅 [关于直邮渠道](about-direct-mail-channel.md).
1. **移动渠道**:通过移动渠道投放，您可以向目标群体发送个性化的短信或LINE消息。 请参阅 [短信渠道](sms-channel.md).
1. **移动应用程序渠道**：移动应用程序投放可让您向 iOS 和 Android 系统发送通知。请参阅 [移动应用程序渠道](about-mobile-app-channel.md) 章节。

   其他渠道在 [本页](steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >可用渠道的数量取决于您的合同。 请核实您的许可协议。

可以执行投放 **在线** （通过电子邮件，移动渠道之一和推送通知）以及 **离线** （直邮渠道）。

根据渠道，投放模式可以是：

* 通过Adobe Campaign直接批量交付（电子邮件渠道的默认模式）。
* 通过专家操作员进行外部投放，该操作员获得了投放向导生成的输出文件（直邮渠道的默认模式）。

外部帐户通过 **[!UICONTROL Administration > Platform > External accounts]** 节点。 此配置只应由专家用户执行。

## 电子邮件投放 {#email-deliveries}

的 [电子邮件渠道](about-email-channel.md) 是Adobe Campaign的核心渠道之一，允许您计划个性化电子邮件并发送到特定目标。

您可以发送不同类型的电子邮件：

* 单次发送电子邮件：您可以向定义的目标发送一次的电子邮件。 它们通常用于推广只准备和发送一次的特定内容（新闻稿、促销电子邮件等）。
* 定期电子邮件：在营销活动中，定期发送相同的电子邮件，并定期汇总每个发送及其报告。 会根据发送日期的合格目标，发送同一封电子邮件，但通常会发送到其他目标。 一个常见的示例是生日电子邮件。 有关更多信息，请参阅 [定期投放](../../workflow/using/recurring-delivery.md).
* 事务型电子邮件：基于客户行为触发的统一电子邮件。 请参阅 [事务型消息传递](../../message-center/using/about-transactional-messaging.md).

要了解投放使用情况和建议，请查阅Campaign [投放最佳实践](delivery-best-practices.md).

有关不同类型投放的更多信息，请参阅 [此部分](#types-of-deliveries).

## 移动投放 {#mobile-deliveries}

Adobe Campaign允许您交付 [短信](sms-channel.md) 和 [折线图](line-channel.md) 邮件。

对于短信消息，您只能以文本格式创建、修改和个性化消息。 您还可以在发送短信消息之前对其进行预览。

对于LINE消息，您可以发送文本或图像及链接。

要将短信或LINE消息投放到移动电话，您需要：

* 在 **[!UICONTROL Mobile (SMS)]** 渠道或 **[!UICONTROL LINE]** 渠道。
* 正确链接到此外部帐户的短信或行投放模板。

## 推送通知 {#push-notifications}

Adobe Campaign允许您发送个性化的分段 [推送通知](about-mobile-app-channel.md) 在iOS和Android移动设备上，通过专用应用程序。 执行配置和集成步骤后，即可创建和发送iOS和Android投放。 您还可以设计包含图像或视频的丰富通知。

## 直邮 {#direct-mail}

[直邮是一种线下渠道，用于生成直邮提供商所需的个性化文件。](about-direct-mail-channel.md)利用这种手段，可将线上和线下渠道有机地结合，用在客户历程中。

利用线上渠道，可创建消息（电子邮件、短信、移动应用投放等）并直接从 Adobe Campaign 发送至受众。线下渠道则不同。在准备直邮投放时，Adobe Campaign 会生成一个文件，其中包含了所有定向的用户档案和选定的联系信息（例如邮政地址）。然后，您可以将此文件发送给直邮提供商，由其负责发送纸质信函。

## 其他渠道 {#other-channels}

Adobe Campaign提供电话投放模板，用于创建外部投放。 使用此渠道意味着您设置专用方法来处理输出文件。 配置步骤与的相同 [直邮渠道](about-direct-mail-channel.md).

>[!NOTE]
>
>电话渠道不是现成可用的。 其实施需要Adobe咨询或Adobe合作伙伴参与。 请联系您的Adobe代表以了解更多信息。

此外，“其他”类型的投放使用不执行进程的特定技术模板：这允许他们管理在Adobe Campaign平台之外执行的营销操作。

此渠道没有特定机制。 它是一个通用渠道，具有自己的外部帐户路由选项、投放模板类型和促销活动工作流活动，就像Adobe Campaign中提供的任何其他通信渠道一样。

此渠道仅用于描述性目的，例如，定义要跟踪在非Adobe Campaign工具中执行的营销活动目标的投放。

## 投放类型{#types-of-deliveries}

Campaign中有三种类型的投放对象：

### 单个投放 {#single-delivery}

A **投放** 是执行一次的独立投放对象。 它可以重复、重新准备，但只要它处于最终状态（已取消、停止、完成），就不能重复使用。

可以从投放列表创建投放，也可以通过 [投放](../../workflow/using/delivery.md) 活动。

工作流还根据您要使用的渠道类型提供特定投放活动。 有关这些活动的更多信息，请参阅 [此部分](../../workflow/using/cross-channel-deliveries.md).

### 循环投放 {#recurring-delivery}

A **循环投放** 允许您在每次执行活动时创建新投放。 这样可避免为定期任务创建新投放。

例如，如果您每月运行一次此类活动，则一年后将有12次投放结束。

在工作流中通过 [定期投放活动](../../workflow/using/recurring-delivery.md). 本节将介绍此活动的示例： [在定位工作流中创建定期投放](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### 连续投放 {#continuous-delivery}

A **连续投放** 允许您向现有投放添加新收件人，这样便无需在每次执行新投放时都创建新投放。

如果投放中的信息（内容、名称等）发生更改，则会在投放执行时创建新的投放对象。 如果没有更改任何信息，则重复使用同一投放对象，并将投放和跟踪日志添加到同一对象中。

例如，如果您每月运行一次此类活动，则一年后最终将会有一个投放（前提是您未对投放进行任何更改）。

在工作流中，通过 [连续投放活动](../../workflow/using/continuous-delivery.md).
