---
product: campaign
title: 在Adobe Campaign中监控投放能力
description: 了解Adobe Campaign中有关可投放性监视的工具和准则
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 1%

---

# 监控您的可投放性{#monitoring-deliverability}

在下方，您将找到有关Adobe Campaign提供的各种监控工具的详细信息，以及有关利用Adobe Campaign提供的功能来监控平台可投放性的其他准则。

## 关于可投放性监测 {#about-deliverability-monitoring}

此功能通过Adobe Campaign中的专用包提供。 要使用该软件包，必须安装此软件包。 完成后，请重新启动服务器以将包考虑在内。
* 对于托管和混合客户端，Adobe技术支持和顾问已在实例上配置了&#x200B;**可投放性监控**。 有关更多信息，请与您的Adobe客户经理联系。

* 对于内部部署，必须通过&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;菜单安装&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;包。 有关详细信息，请参阅[安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md)。

在Adobe Campaign Classic中，**可投放性监控**&#x200B;由&#x200B;**[!UICONTROL Refresh for deliverability]**&#x200B;工作流管理。 默认情况下，它安装在所有实例上，允许您初始化退回邮件鉴别规则列表、域列表和MX列表。 安装&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;包后，此工作流每夜运行以定期更新规则列表，并让您能够主动管理平台可投放性。

通过可投放性包，您可以访问：

* [收件箱呈现报告](inbox-rendering.md)允许您预览主要电子邮件客户端上的邮件，以便扫描内容和信誉。
* 邮件质量概述（收件箱、垃圾邮件）。

## 监控工具 {#monitoring-tools}

您还可以使用以下工具：

* **[!UICONTROL Delivery throughput]**&#x200B;报告提供给定时段内整个平台的吞吐量概览。 有关更多信息，请参阅[此小节](../../reporting/using/global-reports.md#delivery-throughput)。
* 每个投放为不同的Internet服务提供商(ISP)生成广播统计报告。 其中显示了一些可能会影响您的可投放性的数据质量和信誉指标，包括以下数字：
   * **[!UICONTROL Hard bounces]**&#x200B;指示数据质量。 此数字应小于2%。
   * **[!UICONTROL Soft bounces]**&#x200B;指示信誉。 对于任何给定的ISP，此数字不应大于10%。

  有关详细信息，请参阅[投放统计信息](../../reporting/using/global-reports.md#delivery-statistics)部分。
* 更一般而言，[投放仪表板](about-delivery-monitoring.md)授予您访问：
   * [投放摘要](delivery-dashboard.md#delivery-summary)，显示发送的详细信息，以及成功发送、处理和发送的邮件数；
   * [投放日志和历史记录](delivery-dashboard.md#delivery-logs-and-history)，其中显示了已排除的目标以及原因；
   * [跟踪日志](delivery-dashboard.md#tracking-logs)，显示打开数和点击数等跟踪信息。

## 监测准则 {#monitoring-guidelines}

以下是有关可投放性监测的其他准则：

* 定期检查整个平台的[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)，以验证它是否与原始设置一致。
* 检查投放模板中是否正确设置了[重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)（重试期间为30分钟，重试次数超过20次）。
* 定期验证[退回](understanding-delivery-failures.md#bounce-mail-management)邮箱是否可访问，以及帐户是否即将过期。
* 检查可从[投放仪表板](delivery-dashboard.md)访问的每个投放吞吐量，以确保其与投放内容的有效性一致（例如，“闪速销售”应以分钟而不是天投放）。
* 使用[波次](steps-sending-the-delivery.md#sending-using-multiple-waves)时，请验证每个波次在触发下一个波次之前是否有足够的时间完成。
* 检查错误数和新的[隔离](understanding-quarantine-management.md)与其他投放是否一致。
* 列入阻止列表请仔细查阅[投放日志](delivery-dashboard.md#delivery-logs-and-history)以详细检查突出显示的错误类型（、DNS问题、反垃圾邮件规则等）。
