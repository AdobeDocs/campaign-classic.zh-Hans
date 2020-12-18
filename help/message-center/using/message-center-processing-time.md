---
solution: Campaign Classic
product: campaign
title: 消息中心处理时间
description: 消息中心处理时间
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---


# 消息中心处理时间{#message-center-processing-time}

此报告显示与实时队列相关的主要指标。 此报告面向技术管理员，也可通过控制实例中的&#x200B;**[!UICONTROL Monitoring]**&#x200B;范围访问。

![](assets/mc_reports_2.png)

与&#x200B;**[!UICONTROL Message Center service level]**&#x200B;报告一样，您可以选择显示整体统计信息或与特定执行实例相关的统计信息。 您还可以按渠道和特定时间段来筛选数据。 在&#x200B;**[!UICONTROL Indicators over the period]**&#x200B;部分中显示的指示器是在所选期间内计算的：

* **[!UICONTROL Average queuing time]** :成功处理事件在消息中心所用的平均时间。只考虑处理时间。
* **[!UICONTROL Average message sending time (s)]** :成功处理事件在消息中心所用的平均时间。只考虑投放时间。
* **[!UICONTROL Average processing time (s)]** :成功处理事件在消息中心所用的平均时间。该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Maximum number of queued events]** :消息中心队列中任意给定时刻的最大事件数。
* **[!UICONTROL Minimum number of queued events]** :消息中心队列中任意给定时刻存在的最小事件数。
* **[!UICONTROL Average number of queued events]** :消息中心队列中任意给定时刻的平均事件数。

>[!NOTE]
>
>可以在Adobe Campaign部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅[监视阈值](../../message-center/using/monitoring-thresholds.md)。

