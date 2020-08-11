---
title: 跟踪和监视消息
seo-title: 跟踪和监视消息
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# 跟踪和监视 {#track-and-monitor}

您单击了“发送”按钮？ 让我们看看会发生什么。 发送投放后，Adobe Campaign使您能够跟踪已发送的消息并了解收件人对投放的反应。 这将帮助您改进未来发送并优化您的下一活动。

## 监视投放 {#monitoring-deliveries}

要控制活动，您必须确保消息确实已送达收件人。

从活动投放仪表板中，您可以检查已处理的消息和投放审计日志。
您还可以控制投放日志中消息的状态。 [了解更多](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

如果投放未被发送，且其状态仍为“待 **定”**?

* 执行过程正在等待某些资源的可用性。 MTA可能尚未启动。
检查您的mta@instance模块是否已在MTA服务器上启动，并在必要时开始MTA模块。 [了解更多](../../production/using/administration.md).

* 投放可能正在使用尚未在发送实例上配置的关联。
提示：检查流量管理(IP关联)的配置。 有关详细信息，请参阅控制传出SMTP通信。

>[!NOTE]
>
>这些步骤只能由专家用户执行。

## 跟踪 {#tracking-deliveries}

要更好地了解收件人的行为，您可以跟踪他们对投放的反应：接收、打开、点击链接、退订等。 在Campaign Classic中，此信息显示在投放所定位的收件人的“跟踪”选项卡和投放的“跟踪”选项卡中。 在Campaign Standard中，它显示在投放的跟踪日志选项卡中。

**提示**:默认情况下，消息跟踪处于启用状态。 要配置URL，请选择投放向导下半部分的“显示URL”选项。 对于邮件的每个URL，您可以选择是否激活跟踪。

有关此方面的详细信息，请参 [阅配置跟踪](../../delivery/using/how-to-configure-tracked-links.md) 部分和跟踪 [指示器说明](../../reporting/using/delivery-reports.md#tracking-indicators) 。

## 投放性能 {#delivery-performances}

要测量消息的传送速度，您可以控制投放吞吐量。 标准是每小时发送的消息数和消息的大小（以位／秒为单位）。 有关详细信息，请参阅 [投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**:

* 请勿在实例上使投放处于失败状态，因为这会维护临时表并影响性能。

* 从投放库中删除不再需要的收件人和非活动的，以保持地址质量。

* 不要试着计划大投放。 请注意，可能需要5到10分钟才能将负载均匀分布到系统上。

## 投放疑难解答 {#delivery-troubleshooting}

遇到投放问题时，可以执行特定操作：

* [可交付性问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [图像显示问题](../../production/using/image-display-issues.md)

* [投放性能问题](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [临时文件问题](../../production/using/temporary-files.md) - *仅限预置型客户*
