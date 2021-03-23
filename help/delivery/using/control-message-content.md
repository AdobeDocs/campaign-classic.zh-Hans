---
solution: Campaign Classic
product: campaign
title: 关于Adobe Campaign Classic中的可交付性
description: 了解有关在Adobe Campaign Classic中管理交付性的更多信息。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: d6a581ae86e50c17ac20fe54baf305b864e11790
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 4%

---


# 控制消息内容{#control-message-content}

要确保您的电子邮件能够触及您的收件人并提高您的电子邮件发送率，他们必须遵守许多规则。 否则，某些消息的内容可被检测为垃圾邮件。 Adobe Campaign为您提供多种工具，使您的内容符合这些规则。

在设计消息内容时，请遵循以下列出的原则：

* [发件人地址](#sender-address):地址必须明确地识别发件人。域必须由发送方拥有并注册。 域注册不得私有化。
* [个性化](#personalization):个性化内容并为每个收件人定义发送时间会增加打开消息的机会。
* 图像和文本：请遵守适当的文本/图像比率（例如，60%的文本和40%的图像）。
* [退订](#opt-out) 链接和登陆页:退订链接至关重要。它必须可见且有效，并且表单必须能够正常工作。
* 预览:使用Adobe Campaign提供的工具检查和优化您的电子邮件内容（[收件箱呈现](#message-responsiveness)、[ SpamAssan](#spamassassin)）。

有关在设计内容时优化交付性的其他提示，请参阅[《Adobe交付性最佳实践指南》](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html)。

>[!NOTE]
>
>有关编辑电子邮件内容的详细信息，请参阅[定义电子邮件内容](../../delivery/using/defining-the-email-content.md)和[构建个性化内容](../../delivery/using/design-and-personalize.md)。

## 发件人地址{#sender-address}

某些ISP在接受消息前检查发送者地址(**[!UICONTROL From]**)的有效性。 格式不良的地址可能导致接收服务器拒绝它。

您必须确保在实例级别（菜单&#x200B;**[!UICONTROL Tools > Advanced > Deployment wizard...]**）或最频繁使用的情况下提供正确的地址。

有关详细信息，请参阅[定义发送者](../../delivery/using/defining-the-email-content.md)。

## 个性化{#personalization}

为了改善收件人的体验并使他们打开您的电子邮件，Adobe Campaign使您能够个性化您的信息。

有关在Adobe Campaign中使用个性化字段的详细信息，请参阅[本节](../../delivery/using/personalization-fields.md)。

在构建内容时优化个性化的一些提示将在[本节](../../delivery/using/design-and-personalize.md#optimize-personalization)中介绍。

## 退出链接和表单{#opt-out}

默认情况下，在分析消息时，[类型规则](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)会检查是否已包含退出链接，并在消息缺失时生成警告。 您可以更改此规则，以便引发错误而不是简单警告，并阻止投放离开此链接。

在每次发送之前，您必须检查退出链接是否工作正常。 例如，在发送验证时，请确保链接有效、表单联机且验证该表单会将&#x200B;**[!UICONTROL No longer contact this recipient]**&#x200B;字段的值更改为&#x200B;**[!UICONTROL Yes]**。 您应系统性地进行此检查，因为进入链接或更改表单时总是可能出现人为错误。

了解如何在本节](../../delivery/using/personalization-blocks.md#personalization-blocks-example)中插入退出链接[。

如果在启动退订后检测到有关投放的问题，则仍然可以手动（例如，使用成批更新功能）对单击退出链接的收件人执行退订，即使他们无法确认其选择。

通常情况下，不要试图阻碍希望退出的收件人，例如要求他们填写电子邮件地址或姓名等字段。 表单应仅包含一个验证按钮，并且只应对加密标识符执行对帐。

请求其他确认是不可靠的：用户可能有两个电子邮件地址被重定向到同一框(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件人只能记住第一个地址，并希望通过发送给另一个地址的消息取消订阅，则表单将拒绝此请求，因为输入的加密标识符和电子邮件地址不匹配。

## 收件箱呈现 {#message-responsiveness}

在发送消息之前，您可以通过检查消息在不同设备上的显示情况来测试消息响应。 这是为了确保以最佳方式在各种Web客户端、Web邮件和设备上显示。

为了实现此功能，Adobe Campaign 会捕捉渲染状态并提供在专用报告中。这样，您就可以预览不同消息接收环境下所收到之消息的显示情况。

有关详细信息，请参阅[收件箱渲染](../../delivery/using/inbox-rendering.md)。

## SpamAssassin {#spamassassin}

Adobe Campaign可配置为与SpamAssassin一起使用。 这使得对电子邮件进行评分以确定邮件是否存在被接收时使用的防垃圾邮件工具视为垃圾邮件的风险。

在启动投放之前，**[!UICONTROL Preview]**&#x200B;选项卡允许您评估风险。 将显示一条警告消息，提示测试结果。

请阅读此[部分](../../delivery/using/spamassassin.md)了解更多信息。