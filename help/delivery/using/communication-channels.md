---
solution: Campaign Classic
product: campaign
title: 通信渠道
description: 创建投放内容，在不同渠道上发送不同的个性化消息。
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 12%

---


# 通信渠道{#communication-channels}

借助Adobe Campaign，您可以发送跨渠道活动，包括电子邮件、短信、LINE消息、推送通知和直接邮件，并使用各种专用[报告](../../reporting/using/delivery-reports.md)衡量其有效性。 这些消息是通过投放设计和发送的，并且可以针对每个收件人进行个性化。

核心功能包括定位、消息的定义和个性化、通信的执行和相关的运营报告。 主要功能接入点是投放向导。 此接入点可实现Adobe Campaign覆盖的多种功能。

>[!NOTE]
>
>Adobe Campaign优惠一组工具，用于监控您的交付能力并优化电子邮件发送。 请阅读[本节](../../delivery/using/about-deliverability.md)了解更多信息。

投放发送可以通过准备投放和/或在工作流过程中发送它来实现自动化。 有关工作流中投放类型活动的详细信息，请参阅[本节](../../workflow/using/about-action-activities.md)。

Adobe Campaign优惠以下投放渠道:

1. **电子邮件渠道**:电子邮件投放可让您向目标群发送个性化电子邮件。请参阅[关于电子邮件渠道](../../delivery/using/about-email-channel.md)。
1. **直邮渠道**:直接邮件投放允许您生成包含目标填充数据的提取文件。请参阅[关于直邮渠道](../../delivery/using/about-direct-mail-channel.md)。
1. **移动渠道**:移动渠道上的投放可让您向目标群发送个性化的SMS或LINE消息。请参阅[SMS渠道](../../delivery/using/sms-channel.md)。
1. **移动应用程序渠道**:移动应用程序投放可让您向iOS和Android系统发送通知。请参阅[移动应用程序渠道](../../delivery/using/about-mobile-app-channel.md)一章。

   其他渠道在[此页](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)中有介绍。

   >[!NOTE]
   >
   >可用渠道的数量取决于您的合同。 请核实您的许可协议。

投放可以执行&#x200B;**联机**(通过电子邮件，移动渠道和推送通知之一)和&#x200B;**脱机**(直接邮件渠道)。

根据渠道,投放模式可以是：

* 通过Adobe Campaign直接成批投放(电子邮件渠道的默认模式)。
* 外部投放通过专家操作员进行，该操作员获得由投放向导生成的输出文件(直接邮件渠道的默认模式)。

外部帐户通过&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;节点配置。 此配置应仅由专家用户执行。

## 电子邮件投放 {#email-deliveries}

[电子邮件渠道](../../delivery/using/about-email-channel.md)是Adobe Campaign的核心渠道之一，允许您计划个性化电子邮件并将其发送给特定目标。

您可以发送不同类型的电子邮件：

* 单一发送电子邮件：可发送一次到定义目标的电子邮件。 它们通常用于推广将仅准备和发送一次的特定内容（新闻稿、促销电子邮件等）。
* 循环电子邮件：在活动中，定期发送相同的电子邮件，并定期聚合每次发送及其报告。 同一电子邮件会根据发送当天的合格目标发送，但通常会发送到其他目标。 一个常见的示例是生日电子邮件。 有关详细信息，请参阅[循环投放](../../workflow/using/recurring-delivery.md)。
* 交易电子邮件：基于客户行为触发的统一电子邮件。 请参阅[Transactional messaging](../../message-center/using/about-transactional-messaging.md)。

要了解投放使用情况和建议，请查阅活动 [投放最佳做法](../../delivery/using/delivery-best-practices.md)。

有关不同投放类型的详细信息，请参阅[本节](#types-of-deliveries)。

## 移动投放{#mobile-deliveries}

Adobe Campaign允许您在移动设备上传送[SMS](../../delivery/using/sms-channel.md)和[LINE](../../delivery/using/line-channel.md)消息。

对于SMS消息，您只能以文本格式创建、修改和个性化消息。 您还可以在发送SMS消息之前预览这些消息。

对于LINE消息，您可以发送文本或图像和链接。

要将SMS或LINE消息传送到移动电话，您需要：

* 在&#x200B;**[!UICONTROL Mobile (SMS)]**&#x200B;渠道或&#x200B;**[!UICONTROL LINE]**&#x200B;渠道上配置的外部帐户。
* 正确链接到此投放模板的SMS或LINE外部帐户。

## 推送通知 {#push-notifications}

Adobe Campaign允许您通过专用应用程序在iOS和Android移动设备上发送个性化的分段[推送通知](../../delivery/using/about-mobile-app-channel.md)。 执行配置和集成步骤后，即可创建和发送iOS和Android投放。 您还可以设计包含图像或视频的丰富通知。

## 直邮 {#direct-mail}

[直邮是一种线下渠道，用于生成直邮提供商所需的个性化文件。](../../delivery/using/about-direct-mail-channel.md)利用这种手段，可将线上和线下渠道有机地结合，用在客户历程中。

利用线上渠道，可创建消息（电子邮件、短信、移动应用投放等）并直接从 Adobe Campaign 发送至受众。线下渠道则不同。在准备直邮投放时，Adobe Campaign 会生成一个文件，其中包含了所有定向的用户档案和选定的联系信息（例如邮政地址）。然后，您可以将此文件发送给直邮提供商，由其负责发送纸质信函。

## 其他渠道 {#other-channels}

Adobe Campaign优惠电话投放模板，用于创建外部投放。 使用此渠道意味着您设置了处理输出文件的专用方法。 配置步骤与[直接邮件渠道](../../delivery/using/about-direct-mail-channel.md)相同。

>[!NOTE]
>
>电话渠道不是现成可用的。 其实施需要Adobe咨询或Adobe合作伙伴参与。 请联系您的Adobe代表以了解更多信息。

此外，“其他”类型投放使用不执行进程的特定技术模板：这使他们能够管理在Adobe Campaign平台之外执行的营销活动。

此渠道没有具体机制。 它是一个通用渠道，具有自己的外部帐户路由选项、投放模板类型和活动工作流活动，就像Adobe Campaign中提供的任何其他通信渠道一样。

此渠道仅用于描述性目的，例如，用于定义要跟踪在非Adobe Campaign工具中执行的活动目标的投放。

## 投放类型{#types-of-deliveries}

活动中有三种类型的投放对象：

### 单个投放{#single-delivery}

**投放**&#x200B;是执行一次的独立投放对象。 它可以重复、重新准备，但只要它处于最终状态（取消、停止、完成），它就不能再使用。

投放可以从投放的列表创建，也可以通过[投放](../../workflow/using/delivery.md)活动在工作流中创建。

工作流还根据您要使用的渠道类型提供特定的投放活动。 有关这些活动的详细信息，请参阅[此部分](../../workflow/using/cross-channel-deliveries.md)。

### 循环投放 {#recurring-delivery}

通过&#x200B;**循环投放**，您可以在每次执行活动时创建新投放。 这样可避免为重复投放创建新任务。

例如，如果每月运行一次此类活动，则一年后将有12个投放。

循环投放通过[循环投放活动](../../workflow/using/recurring-delivery.md)在工作流内创建。 本节介绍了此活动的示例：[在定位工作流](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)中创建重复投放。

### 连续投放 {#continuous-delivery}

**连续投放**&#x200B;允许您向现有投放添加新收件人，这样就不必在每次执行新投放时创建新。

如果投放中的信息（内容、名称等）发生更改，则在投放执行时将创建新的投放对象。 如果未更改任何信息，则重复使用同一投放对象，并将投放和跟踪日志添加到同一对象中。

例如，如果您每月运行一次此类活动，则一年后将只运行一次投放(前提是您未对投放进行任何更改)。

通过[连续投放活动](../../workflow/using/continuous-delivery.md)在工作流内创建连续投放。
