---
product: campaign
title: 消息中心服务级别
description: 了解有关消息中心服务级别报告的更多信息
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# 消息中心服务级别 {#message-center-service-level}



此报表显示与事务型消息相关的投放统计数据以及错误细分。 您可以单击错误类型以显示其详细信息。

还可以通过控制实例上的&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡访问此针对技术管理员的报告。

![](assets/mc_reports_1.png)

在此报表中，您可以选择显示总体统计信息或与特定执行实例相关的统计信息。 您还可以按渠道和特定时段过滤数据。

**[!UICONTROL Indicators over the period]**&#x200B;部分中显示的指示符是在所选时段内计算的：

* **[!UICONTROL Incoming (throughput event/h)]** ：在消息中心队列中输入的事件平均每小时数。
* **[!UICONTROL Incoming (event vol)]** ：在消息中心队列中输入的事件数。
* **[!UICONTROL Outgoing (throughput msg/h)]** ：成功的传出消息中心事件的平均小时数（由投放发送）。
* **[!UICONTROL Outgoing (msg vol)]** ：成功的传出消息中心事件数（由投放发送）。
* **[!UICONTROL Average sending time (seconds)]** ：成功处理事件的消息中心平均逗留时间。 该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Error rate]** ：带有错误的事件数与进入消息中心队列的事件数之比较。 考虑以下错误：路由错误、过期事件（队列中的事件过长）、投放错误、被投放忽略（隔离等）。

>[!NOTE]
>
>可以在部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅[监视器阈值](../../message-center/using/additional-configurations.md#monitoring-thresholds)。
