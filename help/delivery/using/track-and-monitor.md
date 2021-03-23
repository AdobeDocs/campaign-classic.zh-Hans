---
solution: Campaign Classic
product: campaign
title: 跟踪和监视消息
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 53e239c04f9c4239a5c32e4f25549cbc5f6ece50
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 3%

---


# 跟踪和监视 {#track-and-monitor}

您单击了&#x200B;**发送**&#x200B;按钮？ 让我们看看会发生什么。 发送投放后，Adobe Campaign使您能够跟踪已发送的消息并了解收件人对您的投放的反应。 这将帮助您改进未来发送并优化您的下一个活动。

## 监控投放 {#monitoring-deliveries}

要控制您的活动，您必须确保消息确实已送达您的收件人。

从活动投放仪表板中，您可以检查已处理的消息和投放审核日志。
您还可以控制投放日志中消息的状态。 [了解详情](../../delivery/using/about-delivery-monitoring.md)。

如果投放未发送，且其状态仍为&#x200B;**待定**，该怎么办？

* 执行过程正在等待某些资源的可用性。 MTA可能尚未启动。
检查您的mta@instance模块是否已在您的MTA服务器上启动，并根据需要开始MTA模块。 [了解详情](../../production/using/administration.md)。

* 投放可能使用的是尚未在发送实例上配置的关联。
提示：检查流量管理(IP关联)的配置。 有关详细信息，请参阅控制传出SMTP通信。

>[!NOTE]
>
>这些步骤只能由专家用户执行。

## 跟踪 {#tracking-deliveries}

要更好地了解收件人的行为，您可以跟踪他们对投放的反应：接收、打开、点击链接、退订等。 在Campaign Classic中，此信息显示在投放所针对的收件人的“跟踪”选项卡和投放的“跟踪”选项卡中。 在Campaign Standard中，它显示在投放的“跟踪日志”选项卡中。

**提示**:默认情况下，消息跟踪处于启用状态。要配置URL，请选择投放向导下半部分的“显示URL”选项。 对于邮件的每个URL，您可以选择是否激活跟踪。

有关详细信息，请参阅[配置跟踪](../../delivery/using/how-to-configure-tracked-links.md)部分和[跟踪指示器](../../reporting/using/delivery-reports.md#tracking-indicators)说明。

## 投放性能{#delivery-performances}

要测量消息的传送速度，您可以控制投放吞吐量。 标准是每小时发送的消息数和消息的大小（以位/秒为单位）。 有关详细信息，请参阅[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**:

* 请勿在实例上将投放保留为失败状态，因为这会保留临时表并影响性能。

* 删除不再需要的投放，并从数据库中删除非活动收件人以保持地址质量。

* 切勿尝试将大投放计划在一起。 请注意，可能需要5到10分钟才能将负载均匀地分布到系统上。

## 传递疑难解答 {#delivery-troubleshooting}

遇到投放问题时，可以执行特定操作：

* [可交付性问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [图像显示问题](../../production/using/image-display-issues.md)

* [投放性能问题](../../delivery/using/delivery-performances.md)

* [临时文件问题](../../production/using/temporary-files.md) - *仅限预置型客户*
