---
product: campaign
title: 在Adobe Campaign Classic中监控投放能力
description: 了解有关Adobe Campaign Classic中投放能力监控的工具和准则。
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---

# 监测可投放性{#monitoring-deliverability}

在下面，您将找到有关Adobe Campaign提供的不同监控工具的详细信息，以及有关利用Adobe Campaign提供的功能监控平台投放能力的其他一些准则。

## 投放能力监控 {#configuration}

此功能可通过Adobe Campaign中的专用包获取。 要使用它，必须安装此包。 完成后，重新启动服务器以考虑包。
* 对于托管和混合客户端，可通过Adobe技术支持和顾问在您的实例上配置&#x200B;**可交付性监控**。 有关更多信息，请联系您的Adobe客户经理。

* 对于内部部署安装，必须通过&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;菜单安装&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;包。 有关更多信息，请参阅[安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md)。

在Adobe Campaign Classic中， **投放能力监控**&#x200B;由&#x200B;**[!UICONTROL Refresh for deliverability]**&#x200B;工作流管理。 默认情况下，它安装在所有实例上，并允许您初始化退回邮件鉴别规则列表、域列表和MX列表。 安装&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;包后，此工作流将在夜间运行，以定期更新规则列表，并让您能够主动管理平台可交付性。

可投放性包允许您访问：

* [收件箱呈现报告](../../delivery/using/inbox-rendering.md)，用于预览主要电子邮件客户端上的邮件，以扫描内容和声誉。
* 消息质量概述（收件箱、垃圾邮件）。

## 监控工具{#monitoring-tools}

您还可以使用以下工具：

* **[!UICONTROL Delivery throughput]**&#x200B;报告概述了给定时间段内整个平台的吞吐量。 有关更多信息，请参阅[此章节](../../reporting/using/global-reports.md#delivery-throughput)。
* 每个投放都会为不同的互联网服务提供商(ISP)生成广播统计报告。 它会显示一些可能影响投放能力的数据质量和声誉量度，包括以下数字：
   * **[!UICONTROL Hard bounces]** 指示数据质量。此数字应小于2%。
   * **[!UICONTROL Soft bounces]** 表明声誉。对于任何给定的ISP，此数字不应高于10%。

   有关更多信息，请参阅[投放统计信息](../../reporting/using/global-reports.md#delivery-statistics)一节。
* 更一般地，[投放仪表板](../../delivery/using/about-delivery-monitoring.md)允许您访问：
   * [投放摘要](../../delivery/using/delivery-dashboard.md#delivery-summary)，显示发送的详细信息以及成功发送、处理和发送的消息数量；
   * [投放日志和history](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)，其中显示已排除的目标以及原因；
   * [跟踪日志](../../delivery/using/delivery-dashboard.md#tracking-logs)，显示打开和单击等跟踪信息。

## 监测准则 {#monitoring-guidelines}

以下是有关投放能力监控的其他一些准则：

* 定期检查整个平台的[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)，以验证它是否与原始设置一致。
* 检查投放模板中是否正确设置了[retries](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)（重试时间为30分钟，重试次数超过20次）。
* 定期验证是否可以访问[bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)邮箱，且帐户不会过期。
* 检查从[投放仪表板](../../delivery/using/delivery-dashboard.md)访问的每个投放吞吐量，以确保其与投放内容的有效性(例如，“flash sales”应在数分钟（而非数天）内交付。
* 使用[waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)时，请确认在触发下一个波动之前，每个波动有足够的时间完成。
* 检查错误数和新的[隔离](../../delivery/using/understanding-quarantine-management.md)与其他投放相一致。
* 请仔细查阅[投放日志](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)，以检查突出显示的错误类型(阻止列表、DNS问题、反垃圾邮件规则等)。

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
