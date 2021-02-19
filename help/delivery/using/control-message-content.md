---
solution: Campaign Classic
product: campaign
title: 关于Adobe Campaign Classic中的可交付性
description: 了解有关在Adobe Campaign Classic中管理交付性的更多信息。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# 控制消息内容{#control-message-content}

要提高电子邮件的发送率，并确保您的电子邮件已送达收件人，该电子邮件必须遵守下面详述的特定规则。

## 发件人地址{#sender-address}

某些ISP在接受消息前检查发送者地址（发件人）的有效性。 格式不良的地址可能导致接收服务器拒绝它。 您必须确保在实例级别（菜单&#x200B;**[!UICONTROL Tools > Advanced > Deployment wizard...]**）或最频繁使用的情况下提供正确的地址。

## 退出链接和表单{#opt-out}

默认情况下，在分析消息时，类型规则会检查是否包含退出链接，并在消息缺失时生成警告。 您可以更改此规则，以便引发错误而不是简单警告，并阻止投放离开此链接。

在每次发送之前，您必须检查退出链接是否工作正常。 例如，在发送验证时，请确保链接有效、表单联机且验证该表单会将&#x200B;**[!UICONTROL No longer contact this recipient]**&#x200B;字段的值更改为&#x200B;**[!UICONTROL Yes]**。 您应系统性地进行此检查，因为进入链接或更改表单时总是可能出现人为错误。

如果在启动退订后检测到有关投放的问题，则仍然可以手动（例如，使用成批更新功能）对单击退出链接的收件人执行退订，即使他们无法确认其选择。

通常情况下，不要试图阻碍希望退出的收件人，例如要求他们填写电子邮件地址或姓名等字段。 表单应仅包含一个验证按钮，并且只应对加密标识符执行对帐。 请求其他确认是不可靠的：用户可能有两个电子邮件地址被重定向到同一框(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件人只能记住第一个地址，并希望通过发送给另一个地址的消息取消订阅，则表单将拒绝此请求，因为输入的加密标识符和电子邮件地址不匹配。

## SpamAssassin {#spamassassin}

Adobe Campaign可配置为与SpamAssassin一起使用。 这使得对电子邮件进行评分以确定邮件是否存在被接收时使用的防垃圾邮件工具视为垃圾邮件的风险。

在开始投放之前，预览选项卡允许您评估风险。 将显示一条警告消息，提示测试结果。

请阅读此[部分](../../delivery/using/spamassassin.md)了解更多信息。