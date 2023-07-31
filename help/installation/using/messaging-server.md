---
product: campaign
title: 消息服务器
description: 消息服务器
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 8%

---

# 消息服务器{#messaging-server}



Adobe Campaign本机处理出站电子邮件，但需要传统电子邮件服务器接收链接到返回电子邮件（来自邮件程序守护程序）的传入消息。 应用程序将自动处理在此服务器上配置的邮箱。

如果为POP3访问配置的所有服务器在提取邮件时保留了SMTP“邮件ID”标头，则可以使用这些服务器接收回邮件。 例如，使用Qmail、SendMail和Microsoft Exchange的实施当前处于生产阶段。 但是，一些Lotus Notes/domino的安装揭示了“Message-Id”标头的维护问题。

>[!CAUTION]
>
>此邮件服务器可能必须处理大量负载：在初始阶段，典型列表可能会产生最多10%的跳出率（如果您发送100,000条消息，预计将收到10,000条跳出）。
>
>因此，我们建议不要将您的公司消息服务器用于此任务，因为这样可能会产生重大影响。
>
>建议配置DNS的特定子域和退回邮件的专用服务器。
