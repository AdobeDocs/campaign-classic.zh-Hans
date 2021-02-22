---
solution: Campaign Classic
product: campaign
title: 关于 Adobe Experience Cloud 触发器
description: Adobe Experience Cloud Triggers实施入门
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 11%

---


# 开始使用Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] 是Adobe Campaign与Adobe Analytics之间使用管道的集成。管道从您的网站中检索用户的操作或触发器。 放弃购物车是触发器的一个示例。 触发器会以Adobe Campaign处理，以近乎实时地发送电子邮件。

>[!CAUTION]
>
>此功能并非作为产品的一部分现成可用。实施需要咨询 Adobe。请联系您的Adobe代表以了解更多

[!DNL Triggers] 在用户操作后的短时间内运行营销操作。典型响应时间不足1小时。

它允许更灵活的集成，因为配置最少，不涉及第三方。
它还支持大量流量，而不会影响营销活动的性能。 例如，集成每小时可以处理上百万个触发器。

## [!DNL Triggers] 体系结构  {#triggers-architecture}

[!DNL pipelined]进程始终在Adobe Campaign营销服务器上运行。 它连接到管线，检索事件并立即处理它们。

![](assets/triggers_2.png)

[!DNL pipelined]进程使用身份验证服务登录到Experience Cloud并发送私钥。 身份验证服务返回令牌。 在检索事件时，令牌用于进行身份验证。

有关身份验证的详细信息，请参阅此[页面](../../integrations/using/configuring-adobe-io.md)。
