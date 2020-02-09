---
title: 活动集合
seo-title: 活动集合
description: 活动集合
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 活动集合{#event-collection}

可以使用两种模式收集由信息系统生成的事件：

* 调用SOAP方法可让您在Adobe Campaign中推送活动：pushevent方法允许您一次发送一个事件，而PushEvents方法允许您一次发送多个事件。 请参阅活 [动说明](../../message-center/using/event-description.md)。
* 通过创建工作流，您可以通过导入文件或通过SQL网关(使用 **Federated Data Access选项** )恢复事件。

收集事件后，在等待链接到消息模板时，事件会按技术工作流在执行实例的实时队列和批处理队列之间进行细分。

![](assets/messagecenter_events_queues_001.png)

