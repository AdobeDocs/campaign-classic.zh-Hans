---
product: campaign
title: 消息中心服务级别
description: 了解有关消息中心服务级别报告的更多信息
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 3%

---

# 消息中心服务级别 {#message-center-service-level}



此报表显示与事务型消息相关的投放统计数据以及错误细分。 您可以单击错误类型以显示其详细信息。

还可以通过以下方式访问此针对技术管理员的报告： **[!UICONTROL Monitoring]** 选项卡上。

![](assets/mc_reports_1.png)

在此报表中，您可以选择显示总体统计信息或与特定执行实例相关的统计信息。 您还可以按渠道和特定时段过滤数据。

显示的指示器 **[!UICONTROL Indicators over the period]** 部分在所选的时段内计算：

* **[!UICONTROL Incoming (throughput event/h)]** ：在消息中心队列中输入的平均每小时事件数。
* **[!UICONTROL Incoming (event vol)]** ：在消息中心队列中输入的事件数。
* **[!UICONTROL Outgoing (throughput msg/h)]** ：成功的传出消息中心事件的平均每小时数（由投放发送）。
* **[!UICONTROL Outgoing (msg vol)]** ：成功的传出消息中心事件数（由投放发送）。
* **[!UICONTROL Average sending time (seconds)]** ：成功处理事件的消息中心平均逗留时间。 该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Error rate]** ：与进入消息中心队列的事件数相比，出现错误的事件数。 考虑以下错误：路由错误、过期事件（队列中的事件过长）、投放错误、被投放忽略（隔离等）。

>[!NOTE]
>
>可以在部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅 [监测阈值](../../message-center/using/additional-configurations.md#monitoring-thresholds).
