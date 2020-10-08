---
title: 模板路由
seo-title: 模板路由
description: 模板路由
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 12%

---


# 模板路由{#routing-towards-a-template}

在消息模板发布到执行实例上后，将自动生成两个要实时链接到某个批次事件的模板。 路由步骤包括将事件链接到相应的消息模板。 链接基于事件类型本身和模板属性中指定的事件。

事件类型属性中的事件定义：

![](assets/messagecenter_event_type_001.png)

消息模板属性中事件类型的定义：

![](assets/messagecenter_event_type_002.png)

默认情况下，路由基于以下信息：

* 事件类型,
* 要使用的渠道(默认情况下：电子邮件)、
* 最新投放模板，基于发布日期。

