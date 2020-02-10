---
title: 关于Adobe Campaign Classic中的可交付性
description: 了解有关在Adobe Campaign Classic中管理可交付性的更多信息。
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# 控制消息内容{#control-message-content}

要提高电子邮件的发送率并确保电子邮件到达收件人，该电子邮件必须遵守下面详细介绍的某些规则。

## 发件人地址 {#sender-address}

某些ISP在接受消息之前检查发送者地址（发件人）的有效性。 格式不良的地址可能导致接收服务器拒绝它。 您必须确保在实例级别（菜单）或最常使用的情 **[!UICONTROL Tools > Advanced > Deployment wizard...]**&#x200B;况下提供正确的地址。

## 退出链接和表单 {#opt-out}

默认情况下，在分析消息时，排版规则检查是否包含退出链接，并在消息缺失时生成警告。 您可以更改此规则，以便引发错误而不是简单的警告，并阻止分发离开此链接。

在每次发送之前，您必须检查退出链接是否工作正常。 例如，发送证明时，请确保链接有效，表单联机，验证此操作会将字段的值更 **[!UICONTROL No longer contact this recipient]** 改为 **[!UICONTROL Yes]**。 您应该系统性地进行此检查，因为进入链接或更改表单时，总是可能出现人为错误。

如果在发送开始后检测到关于取消订阅的问题，则仍然可以为那些单击退出链接的接收者手动执行取消订阅（例如，使用成批更新功能），即使他们无法确认其选择。

通常，不要试图通过要求收件人填写电子邮件地址或姓名等字段来妨碍希望退出的收件人。 表单应仅具有一个验证按钮，并且只应对加密标识符执行协调。 请求其他确认不可靠：用户可能有两个电子邮件地址被重定向到同一个框(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件人只能记住第一个地址并希望通过发送给另一个地址的消息取消订阅，则表单将拒绝此项，因为输入的加密标识符和电子邮件地址不匹配。

## SpamAssassin {#spamassassin}

可以将Adobe Campaign配置为与SpamAssassin结合使用。 这样，可以对电子邮件进行评分以确定邮件是否存在被收到时使用的防垃圾邮件工具视为垃圾邮件的风险。

在开始交付之前，预览选项卡允许您评估风险。 将显示一条警告消息，提示测试结果。

在本节中了解更多 [信息](../../delivery/using/spamassassin.md)。