---
product: campaign
title: 关于Adobe Campaign Classic中的投放能力
description: 了解有关在Adobe Campaign中管理可投放性的更多信息
feature: Deliverability
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 5%

---

# 控制消息内容{#control-message-content}

![](../../assets/common.svg)

为确保您的电子邮件能够到达收件人并提高电子邮件的投放率，收件人必须遵守许多规则。 否则，某些消息的内容可能会被检测为垃圾邮件。 Adobe Campaign为您提供了多种工具，可让您的内容符合这些规则。

设计消息内容时，请遵循以下所列原则：

* [发件人地址](#sender-address):地址必须明确识别发件人。 域必须由发件人拥有并注册。 域注册表不得私有化。
* [个性化](#personalization):个性化内容并定义每个收件人的发送时间会增加打开消息的可能性。
* 图像和文本：应遵循适当的文本/图像比率（例如，60%的文本和40%的图像）。
* [退订链接](#opt-out) 和登陆页面：退订链接至关重要。 它必须可见且有效，并且表单必须有效。
* 预览：使用Adobe Campaign提供的工具检查并优化电子邮件的内容([收件箱呈现](#message-responsiveness), [SpamAssassin](#spamassassin))。

有关在设计内容时优化投放能力的其他提示，请参阅 [Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>有关编辑电子邮件内容的更多信息，请参阅 [定义电子邮件内容](defining-the-email-content.md) 和 [构建个性化内容](design-and-personalize.md).

## 发件人地址 {#sender-address}

某些ISP会检查发送者地址(**[!UICONTROL From]**)。 地址格式不正确可能导致接收服务器拒绝该地址。

您必须确保在实例级别（菜单）提供正确的地址 **[!UICONTROL Tools > Advanced > Deployment wizard...]**)或最常用的场景中。

有关更多信息，请参阅[此页面](defining-the-email-content.md)。

## 个性化 {#personalization}

为了改善收件人的体验并使其打开您的电子邮件，Adobe Campaign允许您个性化您的邮件。

有关在Adobe Campaign中使用个性化字段的更多信息，请参阅 [此部分](personalization-fields.md).

有关在构建内容时优化个性化的一些提示，请参阅 [此部分](design-and-personalize.md#optimize-personalization).

## 选择退出链接和表单 {#opt-out}

默认情况下，分析消息时， [类型规则](steps-validating-the-delivery.md#validation-process-with-typologies) 检查是否包含选择退出链接，如果缺少，则会生成警告。 您可以更改此规则，以便引发错误而不是简单的警告，并阻止投放在没有此链接的情况下退出。

在每次发送之前，您必须检查选择退出链接是否正常工作。 例如，在发送校样时，请确保链接有效、表单已联机且验证该活动会更改 **[!UICONTROL No longer contact this recipient]** 字段 **[!UICONTROL Yes]**. 您应该系统性地进行此检查，因为进入链接或更改表单时始终可能出现人为错误。

了解如何插入选择退出链接 [在此部分中](personalization-blocks.md#personalization-blocks-example).

如果在投放开始后检测到与退订有关的问题，则仍然可以为单击选择退订链接的收件人手动执行退订（例如使用批量更新功能），即使他们无法确认其选择。

通常，请不要尝试通过要求收件人填写诸如其电子邮件地址或姓名之类的字段来阻止希望选择退出的收件人。 表单应仅具有一个验证按钮，并且应仅对加密的标识符执行协调。

请求附加确认不可靠：用户可能具有两个重定向到同一框的电子邮件地址(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件人只能记住第一个地址，并希望通过发送给另一个地址的消息取消订阅，则表单将拒绝此请求，因为加密的标识符与输入的电子邮件地址不匹配。

## 收件箱呈现 {#message-responsiveness}

在发送消息之前，您可以通过检查消息在不同设备上的外观来测试消息的响应速度。 这是为了确保以最佳方式在各种Web客户端、Web邮件和设备上显示它。

为了实现此功能，Adobe Campaign 会捕捉渲染状态并提供在专用报告中。这样，您就可以预览不同消息接收环境下所收到之消息的显示情况。

有关此内容的更多信息，请参阅 [收件箱呈现](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign可配置为与SpamAssassin结合使用。 这样，就可以对电子邮件进行评分，以确定邮件是否存在被接收时使用的防垃圾邮件工具视为垃圾邮件的风险。

在开始投放之前， **[!UICONTROL Preview]** 选项卡，用于评估风险。 出现警告消息，显示测试结果。

在中了解详情 [部分](spamassassin.md).
