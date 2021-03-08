---
solution: Campaign Classic
product: campaign
title: 事件集合
description: 事件集合
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# 事件集合{#event-collection}

信息系统生成的事件可以采用两种模式进行收集：

* 调用SOAP方法可以在Adobe Campaign中推送事件:PushEvent方法允许您一次发送一个事件,PushEvents方法允许您一次发送多个。 请参阅[事件说明](../../message-center/using/event-description.md)。
* 创建工作流允许您通过导入文件或通过SQL网关(使用&#x200B;**联合数据访问**&#x200B;选项)恢复事件。

收集事件后，将按技术工作流在执行实例的实时队列和批处理队列之间划分，同时等待链接到消息模板。

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>在执行实例上，不能将&#x200B;**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;文件夹设置为视图，因为这可能导致访问权限问题。 有关将文件夹设置为视图的详细信息，请参阅[本节](../../platform/using/access-management-folders.md)。
