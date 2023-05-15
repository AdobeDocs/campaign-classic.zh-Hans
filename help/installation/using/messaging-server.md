---
product: campaign
title: 消息服务器
description: 消息服务器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# 消息服务器{#messaging-server}



Adobe Campaign本地处理出站电子邮件，但是，需要传统的电子邮件服务器才能接收链接到返回电子邮件（从邮件守护程序）的传入消息。 应用程序将自动处理在此服务器上配置的邮箱。

为POP3访问配置的所有服务器，如果在提取邮件时保留SMTP“邮件 — ID”标头，则可用于接收回邮。 例如，使用Qmail、SendMail和Microsoft Exchange的实施当前正在生产中。 但是，Lotus Notes/domino的一些安装显示了维护“消息ID”标头时出现的问题。

>[!CAUTION]
>
>此邮件服务器可能必须处理大量负载：在初始阶段，典型列表最多可产生10%的跳出率（如果您发送100,000条消息，预计会收到10,000条退回）。
>
>因此，我们建议您禁止在公司邮件服务器中使用此任务，因为此任务可能会受到强烈影响。
>
>建议为退件邮件配置DNS的特定子域和专用服务器。
