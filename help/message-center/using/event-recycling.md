---
title: 活动循环
seo-title: 活动循环
description: 活动循环
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 活动循环{#event-recycling}

如果在特定渠道上传递消息失败，Adobe Campaign可以使用其他渠道重新发送消息。 例如，如果SMS渠道上的分发失败，则会使用电子邮件渠道重新发送消息。

为此，您需要配置一个工作流，该工作流会重新创建所有具有“ **Delivery** error”（传送错误）状态的事件，并为它们分配一个不同的渠道。

>[!CAUTION]
>
>此步骤只能使用工作流执行，因此保留给专家用户。 有关详细信息，请与Adobe客户经理联系。

