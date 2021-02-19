---
solution: Campaign Classic
product: campaign
title: 消息服务器
description: 消息服务器
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---


# 消息服务器{#messaging-server}

Adobe Campaign可以本机处理出站电子邮件，但传统电子邮件服务器需要接收链接到返回电子邮件(来自虚拟邮箱)的传入邮件。 应用程序将自动处理在此服务器上配置的邮箱。

如果为POP3访问配置的所有服务器在拾取邮件时保留SMTP &quot;Message-ID&quot;标头，则可以使用它们接收返回邮件。 例如，使用Qmail、SendMail和Microsoft Exchange的实施当前正在生产中。 但是，Lotus Notes/domino的某些安装显示了维护“Message-Id”标头时出现的问题。

>[!CAUTION]
>
>此邮件服务器可能必须处理繁重的负载：在初始阶段，典型列表的跳出率最高可达10%（如果您发送100,000条消息，预计会收到10,000条跳出率）。
>
>因此，我们建议不要为此任务使用公司消息服务器，因为它可能会受到强烈影响。
>
>建议为弹回邮件配置DNS的特定子域和专用服务器。
