---
title: 消息传递服务器
seo-title: 消息传递服务器
description: 消息传递服务器
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 消息传递服务器{#messaging-server}

Adobe Campaign可以本机处理出站电子邮件，但传统的电子邮件服务器需要接收链接到返回电子邮件（从邮件守护程序）的传入消息。 在此服务器上配置的邮箱将由应用程序自动处理。

如果为POP3访问配置的所有服务器在拾取邮件时保留SMTP的“邮件-ID”标题，则可以使用它们接收回邮。 例如，使用Qmail、SendMail和Microsoft exchange的实施目前正在生产中。 但是，Lotus Notes/domino的某些安装显示了维护“Message-Id”标题时的问题。

>[!CAUTION]
>
>此邮件服务器可能必须处理大量负载：在初始阶段，典型列表最高可产生10%的弹回率（如果您发送100,000条消息，预期会收到10,000条弹回）。
>
>因此，我们建议不要为此任务使用公司消息服务器，因为它可能会受到强烈影响。
>
>建议为弹回邮件配置DNS的特定子域和专用服务器。
