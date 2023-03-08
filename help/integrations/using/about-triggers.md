---
product: campaign
title: 关于 Adobe Experience Cloud 触发器
description: Adobe Experience Cloud Triggers实施入门
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 0a59b0dbdbe70cf8993ce7153b8f3c049c1f1108
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# 使用Campaign和Experience Cloud触发器{#about-adobe-experience-triggers}

![](../../assets/common.svg)

[!DNL Triggers] 是Adobe Campaign与Adobe Analytics之间使用管道的集成。 管道从您的网站检索用户的操作或触发器。 放弃购物车就是一个触发器示例。 在Adobe Campaign中处理触发器以近乎实时地发送电子邮件。

>[!CAUTION]
>
>此功能并非作为产品的一部分现成可用。对于此实施，您首先需要通过Adobe支持开立工单。 然后，您将能够执行中详述的步骤 [页面](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] 在用户执行操作后，在短时间内运行营销操作。 典型响应时间少于1小时。

由于配置很少且没有第三方参与，因此它允许更敏捷的集成。
它还支持高流量而不影响营销活动的性能。 例如，集成每小时可以处理100万个触发器。

## [!DNL Triggers] 体系结构 {#triggers-architecture}

此 [!DNL pipelined] 进程始终在Adobe Campaign marketing server上运行。 它连接到管道，检索事件，并立即处理它们。

![](assets/triggers_2.png)

此 [!DNL pipelined] 进程使用身份验证服务登录到Experience Cloud并发送私钥。 身份验证服务返回一个令牌。 令牌用于在检索事件时进行身份验证。

有关身份验证的更多信息，请参阅此 [页面](../../integrations/using/configuring-adobe-io.md).
