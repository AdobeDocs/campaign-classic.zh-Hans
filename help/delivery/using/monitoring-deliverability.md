---
title: 在Adobe Campaign经典中监控交付性
description: 了解有关Adobe Campaign经典中交付性监控的工具和指南。
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a30c4a2d31c3f674ac4a7bb4827a6951b36014ab
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---


# 监控投放能力{#monitoring-deliverability}

在下面，您将找到Adobe Campaign提供的不同监控工具的详细信息，以及一些关于可交付性监控的其他准则。

## 监视工具 {#monitoring-tools}

使用Adobe Campaign提供的功能来监控平台的可交付性。

通过可交付性包，您可以访问：

* 有关日常交付性能的技术跟踪报告（技术监控）。 此报告可按需提供，允许您通过电子邮件在指定地址接收每日报告。 有关此方面的详细信息，请与Adobe客户关怀团队联系。
* 收件 [箱呈现报告](../../delivery/using/inbox-rendering.md) ，它允许您在主要电子邮件客户端预览邮件，以便扫描内容和声誉。
* 邮件质量概述（收件箱、垃圾邮件）。

您还可以使用以下工具：

* 该 **[!UICONTROL Delivery throughput]** 报告概述了给定时间段内整个平台的吞吐量。 For more on this, see [this section](../../reporting/using/global-reports.md#delivery-throughput).
* 该报 **[!UICONTROL Technical deliverability monitoring]** 告包含多个平台的可交付性质量指标。 For more on this, see [this section](#technical-deliverability-monitoring).
* 投放 [仪表板](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) ，您可以访问 [投放摘要](../../delivery/using/monitoring-a-delivery.md#delivery-summary)、投放日志 [、历史记录](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)[、跟踪日志](../../delivery/using/monitoring-a-delivery.md#tracking-logs)。 它们显示发送的详细信息、已排除的目标、原因以及打开和单击等跟踪信息。 <!--For more on this, see [Monitoring a delivery](../../delivery/using/monitoring-a-delivery.md).-->
* 您还可以检查要发送、处理并成功发送的邮件数。 For more on this, see [this section](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent)
   <!--[SpamAssassin](../../installation/using/configuring-spamassassin.md)?-->

## 监控指南 {#monitoring-guidelines}

以下是有关交付性监控的一些附加准则：

* 定期检查 [整个平台的投放](../../reporting/using/global-reports.md#delivery-throughput) 吞吐量，以验证它是否与原始设置一致。
* 检查 [重试](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) (重试期为30分钟，投放模板为20个以上)设置正确。
* 定期验证弹 [回邮箱](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) 是否可访问，以及帐户是否即将过期。
* 检查每个投放吞吐量，确保其与投放内容的有效性(例如， “flash sales”应在几分钟内交付，而不是几天内交付)。
* 在使用 [批次](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)时，请验证在触发下一个波形之前，每个波形是否有足够的时间完成。
* 检查错误和新隔离的 [数量](../../delivery/using/understanding-quarantine-management.md) ，与其他投放一致。
* 仔细查 [阅投放日志](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) ，检查突出显示的错误类型（灰色或黑名单、DNS问题、防垃圾邮件规则等……）。

## 信号垃圾邮件 {#signal-spam}

Signal Spam是一种法国服务，它为法国ISP(Orange, SFR)优惠匿名反馈循环报告。

* 此服务允许您关注法国ISP的声誉并跟踪客户的活动发展。

* Signal Spam还直接抱怨最终用户通过专用界面登录。 然后，这些投诉将被隔离在电子邮件地址数据库中。

## 250ok {#deliverability-250ok}

[250ok是Adobe](https://250ok.com/) 可交付性内部工具的补充性监控解决方案，可提供IP、域黑名单和信誉指标。

提供的信息是实时的，它允许主动提供帮助。

## 技术交付性监控报告 {#technical-deliverability-monitoring}

技术可交付性监视报告每天更新，并通过导航到> **[!UICONTROL Monitoring]** 并 **[!UICONTROL Overview]** 单击Adobe Campaign **[!UICONTROL Technical monitoring]** 选项卡中的链 **[!UICONTROL Home]** 接可用。 它包括许多适用于您的平台的交付质量指标。

这些指标每天上午9点更新。

>[!NOTE]
>
>此外，您还可以通过电子邮件在指定的地址接收每日报告。 通过电子邮件或Adobe Campaign外部网告知我们请求的电子邮件地址。

![](assets/s_tn_del_monitoring.png)

报告中使用了以下指标：

* **[!UICONTROL Reverse DNS]** : Adobe Campaign检查是否为IP地址提供反向DNS，并且这正确地指向IP。

* **[!UICONTROL SPF]** （发送方策略框架）: 一种身份验证机制，使ISP和邮箱提供商能够检查发送域上的电子邮件发送者是否已获得授权。

* **[!UICONTROL DomainKeys]** : 由Yahoo开发、旨在验证电子邮件发件人身份的服务。

* **[!UICONTROL IP and RBL domain]** (实时黑洞列表): 列表IP地址和域，这些IP地址和域已被区块列表组织标记为发送信誉不佳。 这些列表由专用组织（如Spamhaus、Spampoc、SURBL/URIBL等）进行维护。 Adobe Campaign当前处理对RBL的检查，这些RBL对交付能力有显着影响。 这些RBL反映发送的声誉，在接受接收您的电子邮件前，可能会由ISP引用。

* **[!UICONTROL SNDS]** （智能网络数据服务）: Windows [Live Hotmail防垃圾邮件服务](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx)。 Hotmail是唯一提供此类信息的ISP。 基准分数是一个绿色过滤结果，投诉率低于0.1%，垃圾邮件陷阱为零。

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
