---
product: campaign
title: 消息中心处理时间
description: 了解有关消息中心处理时间报告的更多信息
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 6%

---

# 消息中心处理时间 {#message-center-processing-time}



此报表显示与实时队列相关的主要指标。

还可以通过以下方式访问此针对技术管理员的报告： **[!UICONTROL Monitoring]** 选项卡上。

![](assets/mc_reports_2.png)

就像在 **[!UICONTROL Message Center service level]** 报表中，您可以选择显示总体统计信息或特定执行实例的相关统计信息。 您还可以按渠道和特定时段过滤数据。

显示的指示器 **[!UICONTROL Indicators over the period]** 部分在所选的时段内计算：

* **[!UICONTROL Average queuing time]** ：成功处理事件在消息中心所花费的平均时间。 仅考虑处理时间。
* **[!UICONTROL Average message sending time (s)]** ：成功处理事件在消息中心所花费的平均时间。 只考虑mta投放时间。
* **[!UICONTROL Average processing time (s)]** ：成功处理事件在消息中心所花费的平均时间。 该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Maximum number of queued events]** ：在任何给定时刻消息中心队列中存在的最大事件数。
* **[!UICONTROL Minimum number of queued events]** ：在任何给定时刻消息中心队列中存在的最小事件数。
* **[!UICONTROL Average number of queued events]** ：在任何给定时刻消息中心队列中存在的平均事件数。

>[!NOTE]
>
>可以在Adobe Campaign部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅 [监测阈值](../../message-center/using/additional-configurations.md#monitoring-thresholds).
