---
product: campaign
title: 关于Adobe Campaign Classic中的可投放性
description: 了解有关在Adobe Campaign中管理可投放性的更多信息
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 6%

---

# 控制消息内容{#control-message-content}

为了确保您的电子邮件能够送达收件人并提高电子邮件可投放率，这些收件人必须遵守许多规则。 否则，某些邮件的内容可能会被检测为垃圾邮件。 Adobe Campaign提供了多种工具，用于使您的内容遵守这些规则。

设计消息内容时，请遵循下列原则：

* [发件人地址](#sender-address)：该地址必须明确识别发件人。 域必须由发件人拥有并向其注册。 域注册表不得私有化。
* [Personalization](#personalization)：个性化内容并定义每个收件人的发送时间会增加打开邮件的可能性。
* 图像和文本：遵循像样文本/图像比率（例如60%文本和40%图像）。
* [退订链接](#opt-out)和登陆页面：退订链接是必需的。 它必须可见且有效，并且表单必须有效。
* 预览：使用Adobe Campaign提供的工具检查和优化电子邮件的内容（[收件箱呈现](#message-responsiveness)，[SpamAssassin](#spamassassin)）。

有关在设计内容时优化可投放性的其他提示，请参阅[Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html)。

>[!NOTE]
>
>有关编辑电子邮件内容的详细信息，请参阅[定义电子邮件内容](defining-the-email-content.md)。

## 发件人地址 {#sender-address}

某些ISP在接受消息之前会检查发件人地址(**[!UICONTROL From]**)的有效性。 格式错误的地址可能导致接收服务器拒绝该地址。

您必须确保在实例级别（菜单&#x200B;**[!UICONTROL Tools > Advanced > deployment wizard...]**）或最常用的情况下提供了正确的地址。

有关更多信息，请参阅[此页面](defining-the-email-content.md)。

## 个性化 {#personalization}

为了改善收件人的体验并让他们打开您的电子邮件，Adobe Campaign允许您个性化您的消息。

有关在Adobe Campaign中使用个性化字段的更多信息，请参阅[此部分](personalization-fields.md)。

## 选择退出链接和表单 {#opt-out}

默认情况下，在分析消息时，[分类规则](steps-validating-the-delivery.md#validation-process-with-typologies)会检查是否包含选择退出链接，如果缺少该链接，则会生成警告。 您可以更改此规则，以便引发错误而不是简单的警告，并阻止投放在没有此链接的情况下退出。

在每次发送之前，必须检查选择退出链接是否正常工作。 例如，在发送校样时，请确保链接有效，表单处于联机状态，并且验证此操作会将&#x200B;**[!UICONTROL No longer contact this recipient]**&#x200B;字段的值更改为&#x200B;**[!UICONTROL Yes]**。 您应该系统地进行此检查，因为输入链接或更改表单时始终可能存在人为错误。

了解如何在此部分](personalization-blocks.md#personalization-blocks-example)中插入选择退出链接[。

如果在开始投放后检测到有关退订的问题，则仍然可以为单击选择退出链接的收件人手动执行退订（例如使用批量更新功能），即使他们无法确认自己的选择。

通常，不要试图通过要求希望选择退出的收件人（例如，填写其电子邮件地址或姓名等字段）来妨碍他们。 表单应只有一个验证按钮，并且只应对加密的标识符执行协调。

请求额外确认不可靠：用户可能有两个电子邮件地址被重定向到同一个框(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件人只能记住第一个地址，并希望通过发送给另一个地址的邮件取消订阅，则表单将拒绝此操作，因为加密标识符和输入的电子邮件地址不匹配。

## 收件箱呈现 {#message-responsiveness}

在发送消息之前，您可以通过检查消息在不同设备上的外观来测试消息的响应能力。 这是为了确保以最佳方式在各种Web客户端、Web邮件和设备上显示该内容。

为了实现此功能，Adobe Campaign 会捕捉渲染状态并提供在专用报告中。这样，您就可以预览不同消息接收环境下所收到之消息的显示情况。

有关此内容的详细信息，请参阅[收件箱呈现](inbox-rendering.md)。

## SpamAssassin {#spamassassin}

可以将Adobe Campaign配置为与SpamAssassin配合使用。 这使得对电子邮件进行评分以确定邮件在接收时是否具有被反垃圾邮件工具视为垃圾邮件的风险。

在开始投放之前，**[!UICONTROL Preview]**&#x200B;选项卡允许您评估风险。 出现警告消息，给出测试结果。

在此[部分](spamassassin.md)中了解详情。
