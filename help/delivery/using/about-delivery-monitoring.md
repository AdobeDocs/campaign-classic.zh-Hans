---
product: campaign
title: 投放监测入门
description: 详细了解Campaign Classic投放监测功能
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 2%

---

# 投放监测入门 {#about-delivery-monitoring}

>[!IMPORTANT]
>
>本页介绍了针对混合部署和内部部署的特定于&#x200B;**Campaign Classic v7的监视功能**。

## 监控功能

### 投放监测 {#monitoring-deliveries}

**对于Campaign Classic v7混合/内部部署**，服务器资源和MTA（邮件传输代理）配置需要额外的监视。

#### 挂起投放疑难解答 {#pending-deliveries}

如果未发送投放且其状态仍为&#x200B;**待处理**，该怎么办？

* 执行过程正在等待某些资源的可用性。 MTA可能尚未启动。
检查您的mta@instance模块是否已在MTA服务器上启动，并根据需要启动MTA模块。 [了解详情](../../production/using/administration.md)。

* 投放可能使用未在发送实例上配置的关联性。
提示：检查流量管理（IP关联）的配置。 有关详细信息，请参阅控制传出SMTP流量。

>[!NOTE]
>
>这些步骤只能由内部部署安装的专家用户执行。

### 投放能力监控 {#deliverability-monitoring}

#### 可投放性包安装 {#deliverability-package}

此功能通过Adobe Campaign中的专用包提供。 要使用该软件包，必须安装此软件包。 完成后，请重新启动服务器以将包考虑在内。

* 对于托管和混合客户端，Adobe技术支持和顾问已在实例上配置了&#x200B;**可投放性监控**。 有关更多信息，请与您的Adobe客户经理联系。

* 对于内部部署，必须通过&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]** > **[!UICONTROL Tools]** > **[!UICONTROL Advanced]**&#x200B;菜单安装&#x200B;**[!UICONTROL Import package]**&#x200B;包。 有关详细信息，请参阅[安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md)。

#### 可投放性工作流 {#deliverability-workflow}

在Adobe Campaign Classic中，**可投放性监控**&#x200B;由&#x200B;**[!UICONTROL Refresh for deliverability]**&#x200B;工作流管理。 默认情况下，它安装在所有实例上，允许您初始化退回邮件鉴别规则列表、域列表和MX列表。 安装&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;包后，此工作流每夜运行以定期更新规则列表，并让您能够主动管理平台可投放性。

**可投放性包允许您访问：**

* [收件箱呈现报告](inbox-rendering.md)允许您预览主要电子邮件客户端上的邮件，以便扫描内容和信誉。
* 邮件质量概述（收件箱、垃圾邮件）。

#### 监控工具 {#monitoring-tools}

**对于内部部署**，您可以使用以下监视工具：

* **[!UICONTROL Delivery throughput]**&#x200B;报告提供给定时段内整个平台的吞吐量概览。 有关更多信息，请参阅[此小节](../../reporting/using/global-reports.md#delivery-throughput)。
* 每个投放为不同的Internet服务提供商(ISP)生成广播统计报告。 其中显示了一些可能会影响您的可投放性的数据质量和信誉指标，包括以下数字：
   * **[!UICONTROL Hard bounces]**&#x200B;指示数据质量。 此数字应小于2%。
   * **[!UICONTROL Soft bounces]**&#x200B;指示信誉。 对于任何给定的ISP，此数字不应大于10%。

  有关详细信息，请参阅[投放统计信息](../../reporting/using/global-reports.md#delivery-statistics)部分。

#### 监测准则 {#monitoring-guidelines}

**对于内部部署安装**，以下是有关可投放性监视的其他准则：

* 定期检查整个平台的[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)，以验证它是否与原始设置一致。
* 检查投放模板中是否正确设置了[重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)（重试期间为30分钟，重试次数超过20次）。
* 定期验证[退回](understanding-delivery-failures.md#bounce-mail-management)邮箱是否可访问，以及帐户是否即将过期。
* 检查可从[投放仪表板](delivery-dashboard.md)访问的每个投放吞吐量，以确保其与投放内容的有效性一致（例如，“闪速销售”应以分钟而不是天投放）。
* 使用波次时，请确保在触发下一个波次之前，每个波次都有足够的时间完成。
* 检查错误数和新的[隔离](understanding-quarantine-management.md)与其他投放是否一致。
* 列入阻止列表请仔细查阅[投放日志](delivery-dashboard.md#delivery-logs-and-history)以详细检查突出显示的错误类型（、DNS问题、反垃圾邮件规则等）。

### 故障排除 {#delivery-troubleshooting}

在&#x200B;**混合/内部部署**&#x200B;中遇到投放问题时可以执行特定操作：

* [可投放性问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [图像显示问题](../../production/using/image-display-issues.md)
* [投放性能问题](delivery-performances.md)
* [临时文件问题](../../production/using/temporary-files.md) — 仅&#x200B;*内部部署客户*

## 一般监控主题

**监视您的投放：**

* [在Campaign UI中监视投放](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}（Campaign v8文档）
* [投放性能和最佳实践](delivery-performances.md)
* [了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}（Campaign v8文档 — v7和v8的综合指南）

特定于&#x200B;**v7的配置：**

* [退回邮件管理配置](understanding-delivery-failures.md)（v7混合/内部部署）
* [隔离管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}（Campaign v8文档 — v7和v8的综合指南）
* [隔离配置](understanding-quarantine-management.md)（v7混合/内部部署）

**跟踪邮件：**

* [消息跟踪入门](about-message-tracking.md)

## 相关主题

* [投放状态](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"}（Campaign v8文档）
