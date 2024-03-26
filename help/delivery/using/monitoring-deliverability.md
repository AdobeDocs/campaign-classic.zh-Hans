---
product: campaign
title: 在Adobe Campaign中监控投放能力
description: 了解Adobe Campaign中有关可投放性监视的工具和准则
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---

# 监控您的可投放性{#monitoring-deliverability}

在下方，您将找到有关Adobe Campaign提供的各种监控工具的详细信息，以及有关利用Adobe Campaign提供的功能来监控平台可投放性的其他准则。

## 关于可投放性监测 {#about-deliverability-monitoring}

此功能通过Adobe Campaign中的专用包提供。 要使用该软件包，必须安装此软件包。 完成后，请重新启动服务器以将包考虑在内。
* 对于托管和混合客户端， **投放能力监控** 由Adobe技术支持和顾问在您的实例上配置。 有关更多信息，请与您的Adobe客户经理联系。

* 对于内部部署安装，您必须安装 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 通过打包 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 菜单。 有关此内容的更多信息，请参阅 [安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md).

在Adobe Campaign Classic中， **投放能力监控** 由 **[!UICONTROL Refresh for deliverability]** 工作流。 默认情况下，它安装在所有实例上，允许您初始化退回邮件鉴别规则列表、域列表和MX列表。 一旦 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 如果安装了包，则此工作流每夜运行以定期更新规则列表，并让您能够主动管理平台可交付性。

通过可投放性包，您可以访问：

* 此 [收件箱呈现报告](inbox-rendering.md) 这使您能够预览主要电子邮件客户端上的消息，以便扫描内容和信誉。
* 邮件质量概述（收件箱、垃圾邮件）。

## 监控工具 {#monitoring-tools}

您还可以使用以下工具：

* 此 **[!UICONTROL Delivery throughput]** 报告提供给定时段内整个平台的吞吐量概览。 有关更多信息，请参阅[此小节](../../reporting/using/global-reports.md#delivery-throughput)。
* 每个投放为不同的Internet服务提供商(ISP)生成广播统计报告。 其中显示了一些可能会影响您的可投放性的数据质量和信誉指标，包括以下数字：
   * **[!UICONTROL Hard bounces]** 指示数据质量。 此数字应小于2%。
   * **[!UICONTROL Soft bounces]** 指示信誉。 对于任何给定的ISP，此数字不应大于10%。

  有关此方面的更多信息，请参见 [投放统计信息](../../reporting/using/global-reports.md#delivery-statistics) 部分。
* 一般而言， [投放仪表板](about-delivery-monitoring.md) 允许您访问：
   * 该 [投放摘要](delivery-dashboard.md#delivery-summary)，显示发送的详细信息，成功发送、处理和发送的消息数；
   * 该 [投放日志和历史记录](delivery-dashboard.md#delivery-logs-and-history)，其中显示了已排除的目标以及排除原因；
   * 该 [跟踪日志](delivery-dashboard.md#tracking-logs)，其中显示打开数和点击数等跟踪信息。

## 监测准则 {#monitoring-guidelines}

以下是有关可投放性监测的其他准则：

* 定期查看 [投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput) 为整个平台验证其是否与原始设置一致。
* 检查 [重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 在投放模板中正确设置（重试期间为30分钟，重试次数超过20次）。
* 定期验证 [跳出](understanding-delivery-failures.md#bounce-mail-management) 邮箱可访问，且帐户不会过期。
* 检查每个投放吞吐量，可从 [投放仪表板](delivery-dashboard.md)，以确保其与投放内容的有效性一致（例如，“flash sales”应在几分钟内投放，而不是几天）。
* 使用时 [批次](steps-sending-the-delivery.md#sending-using-multiple-waves)，验证在触发下一个波动之前，每个波动都有足够的时间完成。
* 检查错误数和新的 [隔离](understanding-quarantine-management.md) 与其他投放一致。
* 请仔细查阅 [投放日志](delivery-dashboard.md#delivery-logs-and-history) 详细检查突出显示的错误类型(阻止列表、DNS问题、反垃圾邮件规则等)。
