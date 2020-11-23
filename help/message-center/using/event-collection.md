---
solution: Campaign Classic
product: campaign
title: 事件集合
description: 事件集合
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 5%

---


# 事件集合{#event-collection}

信息系统生成的事件可以采用两种模式进行收集：

* 调用SOAP方法可以在Adobe Campaign中推送事件:通过PushEvent方法可以一次发送一个事件，通过PushEvents方法可以一次发送多个数据。 请参阅 [事件说明](../../message-center/using/event-description.md)。
* 通过创建工作流，您可以通过导入文件或通过SQL网关(使用事件选项)恢 **复联合数据访问** 。

收集事件后，在等待链接到消息模板时，技术工作流会在执行实例的实时队列和批处理队列之间按细分。

![](assets/messagecenter_events_queues_001.png)
