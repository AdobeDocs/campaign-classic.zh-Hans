---
product: campaign
title: 在Adobe Campaign Classic中监控投放能力
description: 了解有关Adobe Campaign Classic中投放能力监控的工具和准则。
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 1%

---

# 监控投放能力{#monitoring-deliverability}

![](../../assets/common.svg)

在下面，您将找到有关Adobe Campaign提供的不同监控工具的详细信息，以及有关利用Adobe Campaign提供的功能监控平台投放能力的其他一些准则。

## 关于投放能力监控 {#about-deliverability-monitoring}

此功能可通过Adobe Campaign中的专用包获取。 要使用它，必须安装此包。 完成后，重新启动服务器以考虑包。
* 对于托管和混合客户端， **投放能力监控** 由Adobe技术支持和顾问在您的实例上配置。 有关更多信息，请联系您的Adobe客户经理。

* 对于内部部署安装，您必须安装 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 包 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 菜单。 有关此内容的更多信息，请参阅 [安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md).

在Adobe Campaign Classic, **投放能力监控** 由 **[!UICONTROL Refresh for deliverability]** 工作流。 默认情况下，它安装在所有实例上，并允许您初始化退回邮件鉴别规则列表、域列表和MX列表。 一旦 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 包安装后，此工作流每晚运行以定期更新规则列表，并让您能够主动管理平台可交付性。

可投放性包允许您访问：

* 的 [收件箱呈现报告](inbox-rendering.md) 这样，您就可以在主要电子邮件客户端上预览邮件，以扫描内容和声誉。
* 消息质量概述（收件箱、垃圾邮件）。

## 监控工具 {#monitoring-tools}

您还可以使用以下工具：

* 的 **[!UICONTROL Delivery throughput]** 报表概述给定时段内整个平台的吞吐量。 有关更多信息，请参阅[此章节](../../reporting/using/global-reports.md#delivery-throughput)。
* 每个投放都会为不同的互联网服务提供商(ISP)生成广播统计报告。 它会显示一些可能影响投放能力的数据质量和声誉量度，包括以下数字：
   * **[!UICONTROL Hard bounces]** 指示数据质量。 此数字应小于2%。
   * **[!UICONTROL Soft bounces]** 表明声誉。 对于任何给定的ISP，此数字不应高于10%。

   有关此内容的更多信息，请参阅 [投放统计](../../reporting/using/global-reports.md#delivery-statistics) 中。
* 更一般地说， [投放仪表板](about-delivery-monitoring.md) 允许您访问：
   * the [投放摘要](delivery-dashboard.md#delivery-summary)，显示发送的详细信息以及发送、处理和发送成功消息的数量；
   * the [投放日志和历史记录](delivery-dashboard.md#delivery-logs-and-history)，显示排除的目标及原因；
   * the [跟踪日志](delivery-dashboard.md#tracking-logs)，显示打开和点击量等跟踪信息。

## 监测准则 {#monitoring-guidelines}

以下是有关投放能力监控的其他一些准则：

* 定期查看 [投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput) 供整个平台验证是否与原始设置一致。
* 检查 [重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 在投放模板中正确设置（重试时段为30分钟，重试次数超过20次）。
* 定期验证 [跳出](understanding-delivery-failures.md#bounce-mail-management) 邮箱可访问，且帐户不会过期。
* 检查每个投放吞吐量，可从 [投放仪表板](delivery-dashboard.md)，以确保其与投放内容的有效性(例如，“flash sales”应在数分钟（而非数天）内交付。
* 使用 [批次](steps-sending-the-delivery.md#sending-using-multiple-waves)，请验证在触发下一个波形之前，每个波形是否有足够的时间完成。
* 检查错误和新错误的数量 [隔离](understanding-quarantine-management.md) 与其他投放一致。
* 请仔细查阅 [投放日志](delivery-dashboard.md#delivery-logs-and-history) 详细检查突出显示的错误类型(阻止列表、DNS问题、反垃圾邮件规则等)。
