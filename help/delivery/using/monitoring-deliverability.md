---
solution: Campaign Classic
product: campaign
title: 监控Adobe Campaign Classic中的交付能力
description: 了解有关Adobe Campaign Classic中交付性监控的工具和指南。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: fa5679d91808edb8e3916d5f0e0f54c73198e934
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 2%

---


# 监控投放能力{#monitoring-deliverability}

在下面，您将找到关于Adobe Campaign提供的不同监控工具的详细信息以及关于交付能力监控的其他一些准则。

## 监视工具{#monitoring-tools}

使用Adobe Campaign提供的功能监控平台的交付能力。

Deliverability包允许您访问：

* [收件箱呈现报告](../../delivery/using/inbox-rendering.md)允许您在主要电子邮件客户端上预览邮件以扫描内容和声誉。
* 邮件质量概述（收件箱、垃圾邮件）。

您还可以使用以下工具：

* **[!UICONTROL Delivery throughput]**&#x200B;报告概述了给定时间段内整个平台的吞吐量。 有关更多信息，请参阅[此章节](../../reporting/using/global-reports.md#delivery-throughput)。
* 每个投放为不同的Internet服务提供商(ISP)生成广播统计报告。 它显示一些可能影响交付能力的数据质量和声誉指标，包括以下数字：
   * **[!UICONTROL Hard bounces]** 指示数据质量。此数字应小于2%。
   * **[!UICONTROL Soft bounces]** 表明信誉。对于任何给定的ISP，此数字不应高于10%。

   有关详细信息，请参阅[投放统计](../../reporting/using/global-reports.md#delivery-statistics)部分。
* 更一般地，[投放仪表板](../../delivery/using/about-delivery-monitoring.md)允许您访问：
   * [投放摘要](../../delivery/using/delivery-dashboard.md#delivery-summary)，显示发送的详细信息以及发送、处理和发送成功的消息数；
   * [投放日志和历史记录](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)，显示哪些目标已被排除以及原因；
   * [跟踪日志](../../delivery/using/delivery-dashboard.md#tracking-logs)，显示打开和单击等跟踪信息。

## 监控准则 {#monitoring-guidelines}

以下是有关交付能力监测的一些附加准则：

* 定期检查整个平台的[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)，以验证它是否与原始设置一致。
* 检查是否在投放模板中正确设置了[重试](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)(重试时间为30分钟，重试超过20分钟)。
* 定期验证[bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)邮箱是否可访问以及帐户是否即将过期。
* 检查每个投放吞吐量，确保其与投放内容的有效性一致(例如，“flash sales”应在数分钟内交付，而非数天内交付)。
* 使用[批次](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)时，请验证在触发下一波之前，每个波形是否有足够的时间完成。
* 检查错误数和新的[隔离](../../delivery/using/understanding-quarantine-management.md)是否与其他投放一致。
* 请仔细查阅[投放日志](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)，以检查高亮显示的错误类型(阻止列表、DNS问题、防垃圾邮件规则等)。

## 信号垃圾邮件{#signal-spam}

Signal Spam是一种法国服务，它优惠了法国ISP(Orange， SFR)的匿名反馈循环报告。

* 此服务可让您跟踪法国ISP的声誉并跟踪客户的活动演变。

* Signal Spam还提供最终用户通过专用界面登录的直接投诉。 然后，这些投诉将被隔离在电子邮件地址数据库中。

## 250ok {#deliverability-250ok}

[250okis](https://250ok.com/) 是Adobe交付能力内部工具的补充监控解决方案，提供IP和域阻止列表以及信誉指标。

提供的信息是实时的，它允许主动提供协助。

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
