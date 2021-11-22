---
product: campaign
title: 消息中心处理时间
description: 了解有关消息中心处理时间报告的更多信息。
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# 消息中心处理时间 {#message-center-processing-time}

![](../../assets/v7-only.svg)

此报表显示与实时队列相关的主要指标。

此外，还可以通过 **[!UICONTROL Monitoring]** 选项卡。

![](assets/mc_reports_2.png)

就象 **[!UICONTROL Message Center service level]** 报表中，您可以选择显示整体统计信息或与特定执行实例相关的统计信息。 您还可以按渠道和特定时段过滤数据。

显示在 **[!UICONTROL Indicators over the period]** 部分会在选定的时段内计算：

* **[!UICONTROL Average queuing time]** :成功处理事件在消息中心花费的平均时间。 只考虑处理时间。
* **[!UICONTROL Average message sending time (s)]** :成功处理事件在消息中心花费的平均时间。 只考虑mta提交时间。
* **[!UICONTROL Average processing time (s)]** :成功处理事件在消息中心花费的平均时间。 计算时会考虑处理时间和mta发送时间。
* **[!UICONTROL Maximum number of queued events]** :消息中心队列中在任何给定时刻存在的最大事件数。
* **[!UICONTROL Minimum number of queued events]** :消息中心队列中在任何给定时刻存在的最小事件数。
* **[!UICONTROL Average number of queued events]** :消息中心队列在任何给定时刻存在的平均事件数。

>[!NOTE]
>
>可以在Adobe Campaign部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅 [监视阈值](../../message-center/using/additional-configurations.md#monitoring-thresholds).
