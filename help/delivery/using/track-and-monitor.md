---
product: campaign
title: 跟踪和监控消息
description: 了解如何跟踪和监控消息
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Monitoring, Reporting
role: User
hide: true
hidefromtoc: true
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---

# 跟踪和监视 {#track-and-monitor}

您已单击&#x200B;**发送**&#x200B;按钮？ 让我们看看会发生什么。 发送投放后，借助Adobe Campaign，您可以跟踪已发送的消息，并了解收件人对投放的反应。 这将帮助您改进未来发送并优化下一个营销活动。

## 监测投放 {#monitoring-deliveries}

要控制活动，您必须确保消息确实已发送给收件人。

在Campaign投放仪表板中，您可以检查已处理的消息和投放审核日志。
您还可以控制投放日志中消息的状态。 [了解详情](about-delivery-monitoring.md)。

如果未发送投放且其状态仍为&#x200B;**待处理**，该怎么办？

* 执行过程正在等待某些资源的可用性。 MTA可能尚未启动。
检查您的mta@instance模块是否已在MTA服务器上启动，并根据需要启动MTA模块。 [了解详情](../../production/using/administration.md)。

* 投放可能使用未在发送实例上配置的关联性。
提示：检查流量管理（IP关联）的配置。 有关详细信息，请参阅控制传出SMTP流量。

>[!NOTE]
>
>这些步骤只能由专家用户执行。

## 跟踪行为 {#track-behaviour}

为了更好地了解收件人的行为，您可以跟踪他们对投放的反应：接收、打开、单击链接、取消订阅等。 在Campaign Classic中，此信息显示在投放所定向的收件人的Tracking选项卡和投放的Tracking选项卡中。

**提示**：默认情况下启用邮件跟踪。 要配置URL，请选择投放助手下方的显示URL选项。 对于消息的每个URL，您可以选择是否激活跟踪。

有关详细信息，请参阅[配置跟踪](how-to-configure-tracked-links.md)部分和[跟踪指示器](../../reporting/using/delivery-reports.md#tracking-indicators)说明。

## 投放性能 {#delivery-performances}

要测量消息投放的速度，您可以控制投放吞吐量。 标准是每小时发送的消息数以及消息的大小（以位/秒为单位）。 有关此内容的详细信息，请参阅[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**：

* 请勿将投放置于实例上的失败状态，因为这样可维护临时表并影响性能。

* 从数据库中删除不再需要的投放和不活动的收件人，以维护地址质量。

* 不要试图一起安排大型投放。 请注意，将负载均匀分布到系统可能需要5到10分钟。

## 投放疑难解答 {#delivery-troubleshooting}

遇到投放问题时，可以执行特定操作：

* [可投放性问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [图像显示问题](../../production/using/image-display-issues.md)

* [投放性能问题](delivery-performances.md)

* [临时文件问题](../../production/using/temporary-files.md) — 仅&#x200B;*内部部署客户*
