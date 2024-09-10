---
product: campaign
title: 消息中心处理时间
description: 了解有关消息中心处理时间报告的更多信息
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# 消息中心处理时间 {#message-center-processing-time}



此报表显示与实时队列相关的主要指标。

还可以通过控制实例上的&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡访问此针对技术管理员的报告。

![](assets/mc_reports_2.png)

与&#x200B;**[!UICONTROL Message Center service level]**&#x200B;报告一样，您可以选择显示总体统计信息或相对于特定执行实例的统计信息。 您还可以按渠道和特定时段过滤数据。

**[!UICONTROL Indicators over the period]**&#x200B;部分中显示的指示符是在所选时段内计算的：

* **[!UICONTROL Average queuing time]** ：成功处理消息中心所花费的事件的平均时间。 仅考虑处理时间。
* **[!UICONTROL Average message sending time (s)]** ：成功处理消息中心所花费的事件的平均时间。 只考虑mta投放时间。
* **[!UICONTROL Average processing time (s)]** ：成功处理消息中心所花费的事件的平均时间。 该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Maximum number of queued events]** ：在任何给定时刻消息中心队列中存在的最大事件数。
* **[!UICONTROL Minimum number of queued events]** ：在任何给定时刻消息中心队列中存在的最小事件数。
* **[!UICONTROL Average number of queued events]** ：在任何给定时刻消息中心队列中存在的平均事件数。

>[!NOTE]
>
>可以在Adobe Campaign部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅[监视器阈值](../../message-center/using/additional-configurations.md#monitoring-thresholds)。
