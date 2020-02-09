---
title: 消息中心服务级别
seo-title: 消息中心服务级别
description: 消息中心服务级别
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 消息中心服务级别{#message-center-service-level}

此报告显示与事务性消息相关的传送统计信息以及错误细分。 单击错误类型可显示其详细信息。 此报告针对技术管理员，也可以通过控制实例中 **[!UICONTROL Monitoring]** 的范围访问。

![](assets/mc_reports_1.png)

在此报告中，您可以选择显示整体统计信息或与特定执行实例相关的统计信息。 您还可以按渠道和特定时间段过滤数据。 在选定的时间段内 **[!UICONTROL Indicators over the period]** 将计算该部分中显示的指示符：

* **[!UICONTROL Incoming (throughput event/h)]** :消息中心队列中输入的平均每小时事件数。
* **[!UICONTROL Incoming (event vol)]** :在消息中心队列中输入的事件数。
* **[!UICONTROL Outgoing (throughput msg/h)]** :发送成功的消息中心事件（由分发发送）的平均每小时数。
* **[!UICONTROL Outgoing (msg vol)]** :传出消息中心事件（由分发发送）的成功数量。
* **[!UICONTROL Average sending time (seconds)]** :成功处理事件时在消息中心停留的平均时间。 该计算考虑了处理时间和发送时间。
* **[!UICONTROL Error rate]** :与进入消息中心队列的事件数相比，存在错误的事件数。 会考虑以下错误：路由错误、过期事件（队列中的事件过长）、交付错误，交付被忽略（隔离等）。

>[!NOTE]
>
>可以在部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅监 [控阈值](../../message-center/using/monitoring-thresholds.md)。

