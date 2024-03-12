---
product: campaign
title: 在Adobe Campaign Classic中使用增强MTA发送
description: 了解使用Adobe Campaign Enhanced MTA发送电子邮件的范围和特性
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: bc6f5d569d0c8a5eba4499a854af370258ce83a2
workflow-type: tm+mt
source-wordcount: '1380'
ht-degree: 1%

---

# 使用增强MTA发送 {#sending-with-enhanced-mta}

此 **Adobe Campaign增强型MTA** （邮件传输代理）提供升级的发送基础架构，从而改进可投放性、信誉、吞吐量、报告、退回处理、IP提升和连接设置管理。

实施它可改善可扩展性、提高投放吞吐量并帮助更快地发送更多电子邮件。 这是通过新的自适应投放技术实现的，该技术根据来自互联网服务提供商的反馈实时更改电子邮件发送设置。

>[!IMPORTANT]
>
>Adobe Campaign增强MTA仅适用于托管Campaign Classic或混合型客户。 无法将Campaign Classic内部部署安装升级为使用增强型MTA。

如果您在2018年9月之后配置了Campaign Classic实例，则您使用的是增强型MTA。 对于所有其他Campaign Classic客户，请参见 [常见问题解答](#enhanced-mta-faq) 下。

增强的MTA实施可能会影响一些现有的Campaign功能。 有关此方面的更多信息，请参见 [增强的MTA特异性](#enhanced-mta-impacts).

>[!NOTE]
>
>如果您是Adobe Campaign的最终用户，并且想知道实例是否已升级到增强MTA，请联系您的内部Campaign管理员。

## 常见问题 {#enhanced-mta-faq}

### 使用情况和好处

**什么是增强MTA？**

Adobe Campaign现在可以升级，以使用新的MTA（邮件传输代理），该代理运行SparkPost的商业电子邮件MTA，称为 **动量**.

Momentum代表创新的高性能MTA技术，其中包括更智能的退回处理和自动化可投放性优化功能，可帮助发件人实现并保持最佳收件箱投放率。 <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**有哪些好处？**

* 使用增强型MTA的Adobe Campaign客户端发现 <!--300%-->整体吞吐速度的大幅提升，以及 <!--90%+-->软退回显着减少。
* Enhanced MTA使用最新的MTA技术，为您的电子邮件投放提供最佳吞吐速度。
* 通过即时且自动地适应其收到的反馈，它还可以确保利用实时投放数据更准确、更智能地投放电子邮件。

**我能否同时使用本机Adobe Campaign MTA和增强MTA？**

没有。实例升级后，只有增强型MTA可用于电子邮件投放。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升级至增强型MTA

**升级到增强MTA需要什么？**

如果您在2018年9月之后配置了Campaign Classic实例，则无需执行任何操作，因为您已在使用增强MTA。

对于所有其他托管或部分托管（混合）客户，Adobe Campaign团队将联系协调迁移日期，并提供有关迁移所需的相应步骤的详细信息。

>[!IMPORTANT]
>
>增强型MTA不适用于内部部署。

**将我的实例升级到增强MTA的过程是怎样的？**

托管实例的整个过程需要几分钟的停机时间。 Adobe将在升级后24小时内监测电子邮件吞吐量和可投放性，以评估对电子邮件投放的任何影响。

如果发现任何问题，Adobe可以快速地将您的实例暂时恢复为本机Adobe Campaign MTA。

目前，增强型MTA仅影响电子邮件渠道。 您的推送通知和短信投放将继续使用本机Campaign MTA，不会受到升级的任何影响。

**升级到Enhanced MTA后是否需要再次进行IP预热？**

没有。升级不需要切换到新IP，因此您可以继续使用现有的预热电子邮件IP。

**升级到增强MTA是否会影响当前正在进行的任何活动或投放？**

对于使用Adobe Campaign事务性消息传递功能的客户，触发电子邮件的任何API调用都将在升级停机时间很短时排队等待，并将在升级完成后尝试。

## 增强的MTA特异性 {#enhanced-mta-impacts}

### 新的MX规则

不再使用MX管理投放吞吐量规则。 Enhanced MTA拥有自己的MX规则，允许它根据您自己的历史电子邮件信誉以及来自您发送电子邮件之域的实时反馈，按域自定义您的吞吐量。

有关MX配置的更多信息，请参见 [本节](../../installation/using/email-deliverability.md#mx-configuration).

### 退回鉴别

Campaign中的退回鉴别 **[!UICONTROL Delivery log qualification]** 表不再用于 **同步** 投放失败错误消息。 增强型MTA可确定退回类型并进行鉴别，然后将该信息发回至Campaign。

>[!NOTE]
>
>增强MTA符合SMTP退回的条件，并以映射到Campaign退回原因和资格的退回代码的形式将该条件发送回Campaign。

有关退回鉴别的更多信息，请参阅 [本节](understanding-delivery-failures.md#bounce-mail-qualification).

### 投放

投放一旦传输到增强型MTA后，即无法停止 — 即使它与 **[!UICONTROL Stopped]** Campaign中的状态。

### 投放吞吐量

Campaign投放吞吐量图表将不再向电子邮件收件人显示吞吐量。 该图表现在将显示消息从Campaign中继到Enhanced MTA的吞吐量速度。

有关投放吞吐量的更多信息，请参阅 [本节](../../reporting/using/global-reports.md#delivery-throughput).

### 重试

Campaign不再使用投放中的重试设置。 软退回重试次数以及它们之间的时间长度由Enhanced MTA根据从消息的电子邮件域返回的退回响应的类型和严重性确定。

有关重试的详细信息，请参阅 [本节](steps-sending-the-delivery.md#configuring-retries).

### 有效期

只有当设置为时，Campaign投放中的有效期设置才会由增强型MTA使用 **3.5天或以下**. 如果您在Campaign中定义的值超过3.5天，则不会考虑该值。

例如，如果在Campaign中将有效期设置为默认值5天，则软退回消息将进入Enhanced MTA重试队列，并从该消息达到Enhanced MTA时起最多重试3.5天。 在这种情况下，将不使用Campaign中设置的值。

消息在Enhanced MTA队列中停留3.5天且投放失败后，该消息将超时，其状态将从 **[!UICONTROL Sent]** 到 **[!UICONTROL Failed]** 在投放日志中。

有关有效期的更多信息，请参阅 [本节](steps-sending-the-delivery.md#defining-validity-period).

### DKIM签名

DKIM（域名识别邮件）电子邮件身份验证签名由Enhanced MTA完成。 作为增强MTA升级的一部分，本机Campaign MTA的DKIM签名将在域管理表中关闭。
有关DKIM的更多信息，请参见 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 投放成功报告

在 **[!UICONTROL Summary]** 电子邮件投放视图 [仪表板](delivery-dashboard.md)， **[!UICONTROL Success]** 百分比从100%开始，然后在整个投放过程中逐步下降 [有效期](steps-sending-the-delivery.md#defining-validity-period)，因为软退回和硬退回会从Enhanced MTA报告回Campaign。

事实上，所有消息都显示为 **[!UICONTROL Sent]** 在 [发送日志](delivery-dashboard.md#delivery-logs-and-history) 只要它们成功从Campaign中继到增强MTA。 除非或直至 [跳出](understanding-delivery-failures.md#delivery-failure-types-and-reasons) ，则该消息会从Enhanced MTA传回Campaign。

从Enhanced MTA报告硬退回消息时，其状态会从 **[!UICONTROL Sent]** 到 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比亦会相应减少。

当从增强MTA报告软退回消息时，它们仍显示为 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比尚未更新。 然后，软退回消息 [已重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 在整个投放有效期内：

* 如果在有效期结束前重试成功，则消息状态将保持为 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比保持不变。

* 否则，状态将更改为 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比亦会相应减少。

因此，您应等到有效期结束才能看到最终版本 **[!UICONTROL Success]** 百分比，以及最终实际数量 **[!UICONTROL Sent]** 和 **[!UICONTROL Failed]** 消息。

下表显示了发送过程中的不同步骤以及相应的KPI和发送日志状态。

| 发送过程中的步骤 | KPI摘要 | 发送日志状态 |
|--- |--- |--- |
| 消息已成功从Campaign中继到增强型MTA | **[!UICONTROL Success]** 百分比从100%开始 | 已发送 |
| 从Enhanced MTA返回硬退回消息 | **[!UICONTROL Success]** 百分比将相应减少 | 已失败 |
| 从Enhanced MTA返回软退回消息 | 无更改 **[!UICONTROL Success]** 百分比 | 已发送 |
| 软退回消息重试成功 | 无更改 **[!UICONTROL Success]** 百分比 | 已发送 | **[!UICONTROL Success]** 百分比亦相应增加 | 已发送 |
| 软退回消息重试失败 | **[!UICONTROL Success]** 百分比将相应减少 | 已失败 |

