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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 6%

---


# 消息中心服务级别{#message-center-service-level}

此报告显示与投放相关的事务性消息统计信息以及错误细分。 单击错误类型可显示其详细信息。 此报告面向技术管理员，也可通过控制实例 **[!UICONTROL Monitoring]** 中的范围访问。

![](assets/mc_reports_1.png)

在此报告中，您可以选择显示整体统计信息或与特定执行实例相关的统计信息。 您还可以按渠道和特定时间段来筛选数据。 在选定的时段内 **[!UICONTROL Indicators over the period]** 计算该部分中显示的指示符：

* **[!UICONTROL Incoming (throughput event/h)]** :在消息中心队列中输入的平均每小时事件数。
* **[!UICONTROL Incoming (event vol)]** :在消息中心队列中输入的事件数。
* **[!UICONTROL Outgoing (throughput msg/h)]** :成功传出消息中心事件(由投放发送)的平均每小时数。
* **[!UICONTROL Outgoing (msg vol)]** :成功传出的消息中心事件数(由投放发送)。
* **[!UICONTROL Average sending time (seconds)]** :消息中心花费的平均时间，以便成功处理事件。 该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Error rate]** :与已进入“消息中心”队列的事件数相比，存在错误的事件数。 会考虑以下错误：路由错误、过期事件(队列中的事件过长)、投放错误，被投放忽略(隔离等)。

>[!NOTE]
>
>可以在部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅监 [控阈值](../../message-center/using/monitoring-thresholds.md)。

