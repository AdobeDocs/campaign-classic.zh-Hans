---
product: campaign
title: 消息中心服务级别
description: 在消息中心服务级别报告中了解详情
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# 消息中心服务级别 {#message-center-service-level}



此报表显示与事务型消息相关的投放统计信息以及错误细分。 您可以单击错误类型以显示其详细信息。

还可以通过以下方式访问此面向技术管理员的报告： **[!UICONTROL Monitoring]** 选项卡。

![](assets/mc_reports_1.png)

在此报表中，您可以选择显示整体统计信息或相对于特定执行实例的统计信息。 您还可以按渠道和特定时段过滤数据。

中显示的指示器 **[!UICONTROL Indicators over the period]** 部分在所选时段内计算：

* **[!UICONTROL Incoming (throughput event/h)]** ：在消息中心队列中输入的事件平均每小时数。
* **[!UICONTROL Incoming (event vol)]** ：在消息中心队列中输入的事件数。
* **[!UICONTROL Outgoing (throughput msg/h)]** ：成功的传出消息中心事件的平均每小时数（由投放发送）。
* **[!UICONTROL Outgoing (msg vol)]** ：成功的传出消息中心事件数（由投放发送）。
* **[!UICONTROL Average sending time (seconds)]** ：成功处理事件的平均在消息中心逗留时间。 该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Error rate]** ：发生错误的事件数与已进入消息中心队列的事件数之比较。 考虑以下错误：路由错误、过期事件（队列中的事件过长）、投放错误、被投放忽略（隔离等）。

>[!NOTE]
>
>可以在部署向导中配置警告（橙色）和警报（红色）指示器阈值。 请参阅 [监测阈值](../../message-center/using/additional-configurations.md#monitoring-thresholds).
