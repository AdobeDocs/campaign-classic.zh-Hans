---
product: campaign
title: 跟踪和监视消息
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 3%

---

# 跟踪和监测 {#track-and-monitor}

您是否单击了&#x200B;**Send**&#x200B;按钮？ 让我们看看会发生什么。 发送投放后，Adobe Campaign允许您跟踪已发送的消息，并了解收件人对您的投放有何反应。 这将帮助您改进将来的发送并优化后续促销活动。

## 监控投放 {#monitoring-deliveries}

要控制您的营销活动，您必须确保已将消息发送给收件人。

在Campaign投放仪表板中，您可以检查已处理的消息和投放审核日志。
您还可以控制投放日志中消息的状态。 [了解详情](about-delivery-monitoring.md)。

如果未发送投放，且其状态保持&#x200B;**Pending**，该怎么办？

* 执行过程正在等待某些资源的可用性。 MTA可能尚未启动。
检查您的mta@instance模块是否已在MTA服务器上启动，并在必要时启动MTA模块。 [了解详情](../../production/using/administration.md)。

* 投放可能使用的亲和度尚未在发送实例上配置。
提示：检查流量管理（IP亲和度）的配置。 有关更多信息，请参阅控制传出SMTP流量。

>[!NOTE]
>
>这些步骤只能由专家用户执行。

## 跟踪 {#tracking-deliveries}

为了更好地了解收件人的行为，您可以跟踪收件人对投放的反应：接收、打开、链接点击、退订等。 在Campaign Classic中，此信息显示在投放所定向收件人的跟踪选项卡和投放的跟踪选项卡中。

**提示**:默认启用消息跟踪。要配置URL，请在投放向导的下半部分选择显示URL选项。 对于消息的每个URL，您可以选择是否激活跟踪。

有关更多信息，请参阅[配置跟踪](how-to-configure-tracked-links.md)一节和[跟踪指示器](../../reporting/using/delivery-reports.md#tracking-indicators)说明。

## 投放性能 {#delivery-performances}

要测量消息的传送速度，您可以控制传送吞吐量。 标准是每小时发送的消息数量和消息的大小（以位/秒为单位）。 有关更多信息，请参阅[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**:

* 请勿在实例上将投放保持为失败状态，因为这会维护临时表并影响性能。

* 从数据库中删除不再需要的投放和不活动的收件人，以保持地址质量。

* 请勿尝试同时计划大型投放。 请注意，可能需要5到10分钟才能将负载均匀地分布到系统上。

## 投放疑难解答 {#delivery-troubleshooting}

当遇到投放问题时，可以执行特定操作：

* [投放能力问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [图像显示问题](../../production/using/image-display-issues.md)

* [交付性能问题](delivery-performances.md)

* [临时文件问题](../../production/using/temporary-files.md)  — 仅 *限内部部署客户*
