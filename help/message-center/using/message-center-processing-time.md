---
product: campaign
title: 消息中心处理时间
description: 了解有关消息中心处理时间报告的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# 消息中心处理时间 {#message-center-processing-time}



此报表显示与实时队列相关的主要指标。

还可以通过以下方式访问此面向技术管理员的报告： **[!UICONTROL Monitoring]** 选项卡。

![](assets/mc_reports_2.png)

就像 **[!UICONTROL Message Center service level]** 报告，您可以选择显示整体统计信息或相对于特定执行实例的统计信息。 您还可以按渠道和特定时段过滤数据。

中显示的指示器 **[!UICONTROL Indicators over the period]** 部分在所选时段内计算：

* **[!UICONTROL Average queuing time]** ：成功处理在消息中心花费的事件的平均时间。 仅考虑处理时间。
* **[!UICONTROL Average message sending time (s)]** ：成功处理在消息中心花费的事件的平均时间。 只考虑mta交付时间。
* **[!UICONTROL Average processing time (s)]** ：成功处理在消息中心花费的事件的平均时间。 该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Maximum number of queued events]** ：在任何给定时刻Message Center队列中存在的最大事件数。
* **[!UICONTROL Minimum number of queued events]** ：在任何给定时刻Message Center队列中存在的最小事件数。
* **[!UICONTROL Average number of queued events]** ：在任何给定时刻消息中心队列中存在的平均事件数。

>[!NOTE]
>
>可以在Adobe Campaign部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅 [监测阈值](../../message-center/using/additional-configurations.md#monitoring-thresholds).
