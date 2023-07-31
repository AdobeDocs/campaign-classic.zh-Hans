---
product: campaign
title: 关于 Adobe Experience Cloud 触发器
description: Adobe Experience Cloud Triggers实施入门
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 7%

---

# 使用Campaign和Experience Cloud触发器{#about-adobe-experience-triggers}

[!DNL Triggers] 是Adobe Campaign与Adobe Analytics之间使用管道的集成。 管道从您的网站检索用户的操作或触发器。 放弃购物车就是一个触发器示例。 在Adobe Campaign中处理触发器，以近乎实时地发送电子邮件。

>[!CAUTION]
>
>此功能并非作为产品的一部分现成可用。对于此实施，您首先需要向Adobe支持部门提交工单。 然后，您将能够执行中详述的步骤 [页面](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] 在用户执行操作后，在短时间内运行营销操作。 典型响应时间不到一小时。

由于配置很少且没有第三方参与，因此它允许更敏捷的集成。
它还支持高流量而不影响营销活动的性能。 例如，集成每小时可处理100万个触发器。

![](assets/do-not-localize/book.png) 了解如何 [创建Experience Cloud触发器](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) 识别、定义并监控关键消费者行为。

## [!DNL Triggers] 体系结构 {#triggers-architecture}

此 [!DNL pipelined] 进程始终在Adobe Campaign Marketing Server上运行。 它连接到管道，检索事件，并立即处理它们。

![](assets/triggers_2.png)

此 [!DNL pipelined] 进程使用身份验证服务登录到Experience Cloud并发送私钥。 身份验证服务返回一个令牌。 令牌用于在检索事件时进行身份验证。

有关身份验证的详细信息，请参阅此 [页面](../../integrations/using/configuring-adobe-io.md).
