---
title: 消息中心处理时间
seo-title: 消息中心处理时间
description: 消息中心处理时间
seo-description: null
page-status-flag: never-activated
uuid: 06aca2c2-33c0-4839-bee4-fd838c49ce76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: d1f591d2-95e8-4d99-bc60-955c96b532eb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 消息中心处理时间{#message-center-processing-time}

此报告显示与实时队列相关的主要指示符。 此报告针对技术管理员，也可以通过控制实例中 **[!UICONTROL Monitoring]** 的范围访问。

![](assets/mc_reports_2.png)

与报表一样， **[!UICONTROL Message Center service level]** 您可以选择显示整体统计信息或与特定执行实例相关的统计信息。 您还可以按渠道和特定时间段过滤数据。 在选定的时间段内 **[!UICONTROL Indicators over the period]** 将计算该部分中显示的指示符：

* **[!UICONTROL Average queuing time]** :成功处理事件在消息中心停留的平均时间。 只考虑处理时间。
* **[!UICONTROL Average message sending time (s)]** :成功处理事件在消息中心停留的平均时间。 只考虑投递时间。
* **[!UICONTROL Average processing time (s)]** :成功处理事件在消息中心停留的平均时间。 该计算考虑了处理时间和发送时间。
* **[!UICONTROL Maximum number of queued events]** :消息中心队列中任意给定时刻存在的最大事件数。
* **[!UICONTROL Minimum number of queued events]** :消息中心队列中任意给定时刻存在的最小事件数。
* **[!UICONTROL Average number of queued events]** :消息中心队列中任意给定时刻的平均事件数。

>[!NOTE]
>
>可以在Adobe Campaign部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅监 [控阈值](../../message-center/using/monitoring-thresholds.md)。

