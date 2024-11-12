---
product: campaign
title: 通信渠道
description: 创建投放，在不同渠道上发送个性化信息
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 61%

---

# 通信渠道{#communication-channels}

借助Adobe Campaign，您可以发送跨渠道营销活动，包括电子邮件、短信、LINE消息、推送通知和直邮，并使用各种专门的[报告](../../reporting/using/delivery-reports.md)衡量其有效性。 这些消息通过投放设计和发送，并且可以针对每个收件人进行个性化。

核心功能包括定位、消息定义和个性化、通信执行和相关的运营报告。主要功能接入点是投放助手。此接入点可导向 Adobe Campaign 涵盖的多种功能。

>[!NOTE]
>
>Adobe Campaign提供了一组工具来监控投放能力并优化电子邮件发送。 可在[此部分](about-deliverability.md)中了解详情。

通过在工作流中准备投放和/或发送投放，可以自动进行投放发送。 有关工作流中投放类型的活动的详细信息，请参阅[此章节](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供以下交付渠道：

1. **电子邮件渠道**：电子邮件投放可让您向目标群体发送个性化电子邮件。请参阅[关于电子邮件渠道](about-email-channel.md)。
1. **直邮渠道**：直邮投放允许您生成包含目标群体数据的提取文件。请参阅[关于直邮渠道](about-direct-mail-channel.md)。
1. **移动渠道**：移动渠道中的投放可让您向目标群体发送个性化的SMS或LINE消息。 请参阅[短信渠道](sms-channel.md)。
1. **移动应用程序渠道**：移动应用程序投放允许您向iOS和Android系统发送通知。 请参阅[移动设备应用程序渠道](about-mobile-app-channel.md)一章。

   有关其他渠道的介绍，请参见[本部分](#other-channels)。

   >[!NOTE]
   >
   >可用渠道的数量取决于您的合同。请核实您的许可协议。

可在&#x200B;**在线**（通过电子邮件、其中一个移动渠道和推送通知）和&#x200B;**离线**（直邮渠道）进行投放。

根据渠道的不同，投放模式可以是：

* 通过Adobe Campaign直接批量投放（电子邮件渠道的默认模式）。
* 通过专家操作员进行外部投放，操作员将获得投放助手生成的输出文件（直邮渠道的默认模式）。

外部帐户是通过&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;节点配置的。 此配置应仅由专家用户执行。

## 电子邮件投放 {#email-deliveries}

[电子邮件渠道](about-email-channel.md)是 Adobe Campaign 中的核心渠道之一，允许您向特定目标计划和发送个性化电子邮件。

您可以发送不同类型的电子邮件：

* 单次发送电子邮件：可向定义的目标发送一次性电子邮件。它们通常用于推广某些只需准备并发送一次的特定内容（新闻稿、促销电子邮件等）。
* 定期电子邮件：在营销活动中，定期发送相同的电子邮件，并定期汇总每次发送及其报告。发送同一电子邮件，但通常会发送给符合发送日期条件的不同目标。常见的示例是生日电子邮件。有关详细信息，请参阅[定期投放](../../workflow/using/recurring-delivery.md)。
* 事务性电子邮件：根据客户行为触发的单一电子邮件。请参阅[事务性消息](../../message-center/using/about-transactional-messaging.md)。

要了解投放使用情况和建议，请参阅Campaign [投放最佳实践](delivery-best-practices.md)。

有关不同类型投放的详细信息，请参阅[此部分](#types-of-deliveries)。

## 移动投放 {#mobile-deliveries}

Adobe Campaign 允许您向移动设备投放[短信](sms-channel.md)和 [LINE](line-channel.md) 消息。

对于短信消息，您可以仅以文本格式创建、修改和个性化消息。您还可以在发送短信消息之前进行预览。

对于 LINE 消息，您可以发送文本/图像和链接。

要向手机投放短信和 LINE 消息，您需要：

* 在 **[!UICONTROL Mobile (SMS)]** 渠道或 **[!UICONTROL LINE]** 渠道上配置外部帐户。
* 正确链接到此外部帐户的短信或 LINE 投放模板。

## 推送通知 {#push-notifications}

Adobe Campaign允许您通过专用应用程序在iOS和Android移动设备上发送个性化和分段的[推送通知](about-mobile-app-channel.md)。 执行配置和集成步骤后，即可创建和发送iOS和Android投放。 您还可以设计包含图像或视频的丰富通知。

## 直邮 {#direct-mail}

[直邮](about-direct-mail-channel.md)是脱机渠道，允许您个性化并生成直邮提供商所需的文件。 利用这种手段，可将线上和线下渠道有机地结合，用在客户历程中。

利用在线渠道，可创建消息（电子邮件、短信、移动应用程序投放等），并直接从Adobe Campaign将其发送给受众。 线下渠道则不同。在准备直邮投放时，Adobe Campaign 会生成一个文件，其中包含了所有定向的用户档案和选定的联系信息（例如邮政地址）。然后，您可以将此文件发送给直邮提供商，由其负责发送纸质信函。

## 其他渠道 {#other-channels}

Adobe Campaign提供电话投放模板，用于创建外部投放。 使用此渠道意味着您设置专用方法来处理输出文件。 配置步骤与[直邮渠道](about-direct-mail-channel.md)相同。

>[!NOTE]
>
>电话渠道不可开箱即用。 实施时需要咨询 Adobe Consulting 或 Adobe 合作伙伴。有关更多信息，请联系您的 Adobe 代表。

此外，“其他”类型投放使用不会执行流程的特定技术模板：这使他们能够管理在Adobe Campaign平台之外执行的营销操作。

此渠道没有特定的机制。该渠道与在Adobe Campaign中提供的任何其他通信渠道一样，具有自己的外部帐户路由选项、投放模板类型和活动工作流活动。

此渠道仅用于描述性目的，例如定义要跟踪在 Adobe Campaign 以外的工具中执行的营销活动的目标投放。

## 投放类型{#types-of-deliveries}

Campaign 中有三种类型的投放对象：

### 单个投放 {#single-delivery}

**投放**&#x200B;是一个独立投放对象，只执行一次。可以重复再次准备投放，但如果投放处于最终状态（取消、停止、完成），就无法再重复使用。

可以从投放列表创建投放，也可以通过[投放](../../workflow/using/delivery.md)活动在工作流中创建投放。

工作流还可根据要使用的渠道类型提供特定的投放活动。有关这些活动的详细信息，请参阅[此部分](../../workflow/using/cross-channel-deliveries.md)。

### 定期投放 {#recurring-delivery}

**循环投放**&#x200B;允许您每次执行活动时都创建新投放。 这可让您不必为周期性任务创建新投放。

例如，如果您每月运行一次此类活动，那么一年后最终将有 12 次投放。

定期投放是通过[定期投放活动](../../workflow/using/recurring-delivery.md)在工作流中创建的。这一部分中介绍了使用此活动的示例：[在目标选择工作流中创建定期投放](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

### 持续投放 {#continuous-delivery}

**连续投放**&#x200B;允许您向现有投放添加新收件人，从而避免每次执行投放时都创建新投放。

如果投放中的信息发生更改（内容、名称等），则会在投放执行时创建新投放对象。如果未更改任何信息，则将重用同一投放对象，并将投放和跟踪日志添加到同一对象中。

例如，如果您每月运行一次此类活动，那么一年后您将只运行一次投放（如果您未对投放进行任何更改）。

持续投放是通过[持续投放活动](../../workflow/using/continuous-delivery.md)在工作流中创建的。
