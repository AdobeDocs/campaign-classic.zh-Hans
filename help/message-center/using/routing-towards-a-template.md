---
title: 向模板传送
seo-title: 向模板传送
description: 向模板传送
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 向模板传送{#routing-towards-a-template}

一旦消息模板发布到执行实例上，将自动生成两个要实时链接到或批处理事件的模板。 路由步骤包括将事件链接到相应的消息模板。 链接基于在事件本身和模板的属性中指定的事件类型。

事件属性中事件类型的定义：

![](assets/messagecenter_event_type_001.png)

消息模板属性中事件类型的定义：

![](assets/messagecenter_event_type_002.png)

默认情况下，路由基于以下信息：

* 活动类型，
* 要使用的渠道(默认：电子邮件),
* 基于发布日期的最新分发模板。

