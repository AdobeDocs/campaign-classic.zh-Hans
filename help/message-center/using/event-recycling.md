---
title: 事件回收
seo-title: 事件回收
description: 事件回收
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# 事件回收{#event-recycling}

如果某个特定渠道上的消息投放失败，Adobe Campaign可以使用其他渠道重新发送该消息。 例如，如果SMS渠道上的投放失败，则使用电子邮件渠道重新发送消息。

为此，您需要配置一个工作流，该工作流会重新创建所有事件的 **投放错误** 状态，并为其分配一个不同的渠道。

>[!CAUTION]
>
>此步骤只能使用工作流执行，因此保留给专家用户。 有关详细信息，请与Adobe客户经理联系。

