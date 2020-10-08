---
title: 消息服务器
seo-title: 消息服务器
description: 消息服务器
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 4%

---


# 消息服务器{#messaging-server}

Adobe Campaign可以本机处理出站电子邮件，但传统电子邮件服务器需要接收链接到返回电子邮件(来自虚拟邮箱)的传入邮件。 应用程序将自动处理在此服务器上配置的邮箱。

如果为POP3访问配置的所有服务器在拾取邮件时保留SMTP“邮件-ID”标头，则可以使用它们接收返回邮件。 例如，使用Qmail、SendMail和Microsoft Exchange的实施当前正在生产中。 但是，Lotus Notes/domino的某些安装显示了维护“Message-Id”标头时的问题。

>[!CAUTION]
>
>此邮件服务器可能必须处理繁重的负载：在初始阶段，典型列表的弹回率最高可达10%（如果您发送100,000条消息，预期会收到10,000条弹回率）。
>
>因此，我们建议不要为此公司使用您的任务消息服务器，因为它可能受到强烈影响。
>
>建议为弹回邮件配置DNS的特定子域和专用服务器。
