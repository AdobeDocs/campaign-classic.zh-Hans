---
product: campaign
title: 消息中心处理时间
description: 了解有关消息中心处理时间报告的更多信息
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
TQID: 'https://experienceleague.adobe.com/nESBoEHC7YU0SO4yJ0rscDa3E-ePk6yNbPKzusER7C4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
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
