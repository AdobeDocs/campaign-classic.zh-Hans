---
solution: Campaign Classic
product: campaign
title: 消息中心服务级别
description: 消息中心服务级别
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 5%

---


# 消息中心服务级别{#message-center-service-level}

此报表显示与投放相关的事务性消息统计信息以及错误细分。 您可以单击某个错误类型来显示其详细信息。 此报告面向技术管理员，也可通过控制实例中的&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡访问。

![](assets/mc_reports_1.png)

在此报表中，您可以选择显示整体统计信息或与特定执行实例相关的统计信息。 您还可以按渠道和特定时间段来筛选数据。 在&#x200B;**[!UICONTROL Indicators over the period]**&#x200B;部分中显示的指示器将在选定期间计算：

* **[!UICONTROL Incoming (throughput event/h)]** :在消息中心队列中输入的平均每小时事件数。
* **[!UICONTROL Incoming (event vol)]** :在消息中心队列中输入的事件数。
* **[!UICONTROL Outgoing (throughput msg/h)]** :传出消息中心事件(由投放发送)的平均每小时数。
* **[!UICONTROL Outgoing (msg vol)]** :成功传出消息中心事件的数目(由投放发送)。
* **[!UICONTROL Average sending time (seconds)]** :在消息中心逗留的平均时间，以成功处理事件。该计算将处理时间和mta发送时间考虑在内。
* **[!UICONTROL Error rate]** :与已进入“消息中心”队列的事件数相比，存在错误的事件数。会考虑以下错误：路由错误、过期事件(在队列中的事件过长)、投放错误，被投放忽略(隔离等)。

>[!NOTE]
>
>可以在部署向导中配置警告（橙色）和警告（红色）指示器阈值。 请参阅[监视阈值](../../message-center/using/monitoring-thresholds.md)。

