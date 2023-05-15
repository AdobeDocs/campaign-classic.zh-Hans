---
product: campaign
title: 关于 Adobe Experience Cloud 触发器
description: Adobe Experience Cloud Triggers实施快速入门
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# 使用Campaign和Experience Cloud触发器{#about-adobe-experience-triggers}



[!DNL Triggers] 是Adobe Campaign与Adobe Analytics之间使用管道的集成。 管道从您的网站中检索用户的操作或触发器。 放弃购买是触发器的一个示例。 在Adobe Campaign中处理触发器可近乎实时地发送电子邮件。

>[!CAUTION]
>
>此功能并非作为产品的一部分现成可用。对于此实施，您首先需要打开一个具有Adobe支持的票证。 然后，您将能够按照 [页面](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] 在用户操作后的短时间内运行营销操作。 典型响应时间不到1小时。

它允许更灵活的集成，因为配置很小，并且不涉及第三方。
它还支持大量流量，而不会影响营销活动的性能。 例如，集成每小时可处理百万个触发器。

## [!DNL Triggers] 架构 {#triggers-architecture}

的 [!DNL pipelined] 进程始终在Adobe Campaign营销服务器上运行。 它连接到管道，检索事件并立即处理它们。

![](assets/triggers_2.png)

的 [!DNL pipelined] 进程使用身份验证服务登录到Experience Cloud并发送私钥。 身份验证服务返回令牌。 令牌用于在检索事件时进行身份验证。

有关身份验证的更多信息，请参阅此 [页面](../../integrations/using/configuring-adobe-io.md).
