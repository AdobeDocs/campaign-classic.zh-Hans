---
title: 关于Adobe Experience Manager
seo-title: 关于Adobe Experience Manager
description: 关于Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---


# 关于 Adobe Experience Cloud 触发器{#about-adobe-experience-triggers}

[!DNL Triggers] 是Adobe Campaign和Adobe Analytics利用管道的整合。 管道从您的网站检索用户的操作或触发器。 放弃购物车是触发器的一个示例。 触发器将以Adobe Campaign处理，以近乎实时地发送电子邮件。

[!DNL Triggers] 在用户操作后的短时间内运行营销操作。 典型响应时间不到1小时。

它允许更灵活的集成，因为配置是最小的，不涉及第三方。
它还支持大量流量，而不会影响营销活动的性能。 例如，集成每小时可以处理一百万个触发器。

## [!DNL Triggers] 体系结构 {#triggers-architecture}

流 [!DNL pipelined] 程始终在Adobe Campaign营销服务器上运行。 它连接到管线，检索事件并立即处理它们。

![](assets/triggers_2.png)

进 [!DNL pipelined] 程使用身份验证服务登录到Experience Cloud并发送私钥。 身份验证服务返回一个令牌。 在检索事件时，令牌用于进行身份验证。

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).

>[!NOTE]
>
>事件的进一步处理是作为默认实现外部提供的ACX包的一部分完成的。 接收的事件会立即使用JavaScript代码进行处理。 它将保存到数据库表中，无需进行进一步的实时处理。 触发器用于通过发送电子邮件的活动工作流进行定位。 活动已设置，因此触发事件的客户将收到电子邮件。
