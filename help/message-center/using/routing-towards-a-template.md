---
solution: Campaign Classic
product: campaign
title: 模板路由
description: 模板路由
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 9%

---


# 模板路由{#routing-towards-a-template}

在消息模板发布到执行实例上后，将自动生成两个要实时链接到某个批次事件的模板。 路由步骤包括将事件链接到相应的消息模板。 链接基于事件本身和模板属性中指定的事件类型。

事件属性中的事件类型定义：

![](assets/messagecenter_event_type_001.png)

消息模板属性中事件类型的定义：

![](assets/messagecenter_event_type_002.png)

默认情况下，路由基于以下信息：

* 事件类型
* 要使用的渠道(默认情况下：电子邮件)
* 最新投放模板，基于发布日期
