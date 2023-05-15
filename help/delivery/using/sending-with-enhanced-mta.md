---
product: campaign
title: S与Adobe Campaign Classic中的Enhanced MTA
description: 了解使用Adobe Campaign Enhanced MTA发送电子邮件的范围和特性
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1999'
ht-degree: 4%

---

# 使用增强 MTA 发送 {#sending-with-enhanced-mta}



的 **Adobe Campaign增强MTA** （邮件传输代理）提供了升级的发送基础结构，以改进投放能力、信誉、吞吐量、报告、退件处理、IP升级和连接设置管理。

它的实施旨在提高可扩展性、提高投放吞吐量并帮助更快地发送更多电子邮件。 这是通过新的自适应投放技术实现的，这种技术可以根据互联网服务提供商的反馈实时更改电子邮件发送设置。

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA仅适用于托管Campaign Classic或混合客户。 Campaign Classic内部部署安装无法升级为使用Enhanced MTA。

如果您在2018年9月后配置了Campaign Classic实例，则您将使用增强的MTA。 对于所有其他Campaign Classic客户，请参阅 [常见问题解答](#enhanced-mta-faq) 下。

增强的MTA实施可能会影响一些现有的Campaign功能。 有关此内容的更多信息，请参阅 [增强的MTA特性](#enhanced-mta-impacts).

>[!NOTE]
>
>如果您是Adobe Campaign的最终用户，并且想知道您的实例是否已升级到Enhanced MTA，请与您的内部Campaign管理员联系。

## 常见问题 {#enhanced-mta-faq}

### 使用和好处

**什么是Enhanced MTA?**

Adobe Campaign现在可以升级为使用新的MTA（邮件传输代理），该MTA运行SparkPost的商业电子邮件MTA，名为 **动量**.

Mommentum代表了创新的高性能MTA技术，该技术包括更智能的跳出处理和自动投放能力优化功能，可帮助发件人实现并保持最佳收件箱投放率。 <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**有什么好处？**

* Adobe Campaign客户使用Enhanced MTA时，已看到 <!--300%-->总吞吐量速度的大幅提升， <!--90%+-->软退回显着减少。
* Enhanced MTA使用最新的MTA技术为您的电子邮件投放提供最佳吞吐量速度。
* 通过即时且自动地适应收到的反馈，它还可确保利用实时投放数据进行更准确、更智能的电子邮件投放。

**我能否同时使用本机Adobe Campaign MTA和Enhanced MTA?**

没有。升级实例后，电子邮件投放只能使用Enhanced MTA。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升级到增强的MTA

**升级到Enhanced MTA需要什么？**

如果您在2018年9月后配置了Campaign Classic实例，则无需执行任何操作，因为您已在使用增强MTA。

对于所有其他托管或部分托管（混合）客户，Adobe Campaign团队将联系以协调迁移日期，并提供迁移所需适当步骤的详细信息。

>[!IMPORTANT]
>
>Enhanced MTA不适用于内部部署安装。

**将我的实例升级到Enhanced MTA的过程是什么？**

托管实例的整个过程需要几分钟的停机时间。 Adobe将在升级后长达24小时内监控电子邮件吞吐量和投放能力，以评估对电子邮件投放的任何影响。

如果发现任何问题，Adobe可以快速并临时将您的实例还原到本机Adobe Campaign MTA。

目前，增强型MTA仅影响电子邮件渠道。 您的推送通知和短信投放将继续使用本机Campaign MTA，并且不会因升级而受到任何影响。

**升级到Enhanced MTA后，是否需要再次经历IP升温？**

没有。升级不需要切换到新IP，因此您可以继续使用现有的已热电子邮件IP。

**升级到Enhanced MTA会影响当前正在进行的任何营销活动或投放吗？**

升级实例以使用增强型MTA之前准备的任何投放，都需要重新准备，才能正确使用新的MTA。

对于使用Adobe Campaign事务型消息传递功能的客户，任何用于触发电子邮件的API调用都将在很短的升级停机时间内排队等候，并将在升级完成后尝试执行。

## 增强的MTA特性 {#enhanced-mta-impacts}

### 增强的MTA标头

最新的Campaign Classic实例包括可向每条消息添加所需增强MTA标头的代码。 如果您使用的是Adobe Campaign 19.1（版本9032）或更高版本，并且情况并非如此，则必须请求 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 将&quot;useMomentum=true&quot;参数添加到执行实例配置(在 [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) 文件)，这可能是您的营销实例， [中间源实例](../../installation/using/mid-sourcing-server.md)或 [事务性消息执行实例](../../message-center/using/configuring-instances.md#execution-instance)，具体取决于您的配置。

但是，如果您使用的是不包含此代码的旧实例，则会使用名为 **[!UICONTROL Typology Rule for Enhanced MTAs]** 必须添加到Campaign实例中的所有现有分类。
此规则由 **[!UICONTROL Typology]** 包，作为升级到Enhanced MTA的一部分进行安装。

>[!IMPORTANT]
>
>如果您在分类中看到此分类规则，请勿以任何方式删除或修改该分类规则。 否则，您的电子邮件投放可能会受到不利影响。

此 **[!UICONTROL Typology]** 包需要安装在Adobe Campaign营销实例上。

如果您是混合客户端，Adobe Campaign团队将为您提供有关如何安装 **[!UICONTROL Typology]** 包，作为升级到Enhanced MTA的一部分。 请联系您的客户经理以获取完整的说明。

>[!IMPORTANT]
>
>Adobe Campaign团队提供的有关如何安装 **[!UICONTROL Typology]** 应当仔细地遵循一揽子计划。 否则，您可能会遇到用于发送电子邮件的IP存在的主要问题。

有关分类的更多信息，请参阅 [此部分](../../campaign-opt/using/about-campaign-typologies.md).

### 新MX规则

不再使用MX管理投放吞吐量规则。 Enhanced MTA有其自己的MX规则，允许根据您自己的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，按域自定义您的吞吐量。

有关MX配置的更多信息，请参阅 [此部分](../../installation/using/email-deliverability.md#mx-configuration).

### 退回鉴别

营销活动中的退回资格 **[!UICONTROL Delivery log qualification]** 表格不再用于 **同步** 投放失败错误消息。 Enhanced MTA可确定退件类型和资格条件，并将该信息发回至Campaign。

>[!NOTE]
>
>Enhanced MTA符合SMTP退回的条件，并以映射到促销活动退回原因和鉴别的退回代码的形式，将该鉴别发送回Campaign。

有关退回鉴别的更多信息，请参阅 [此部分](understanding-delivery-failures.md#bounce-mail-qualification).

### 投放吞吐量

促销活动投放吞吐量图将不再向电子邮件收件人显示吞吐量。 该图表现在将显示消息从Campaign中继到增强型MTA的吞吐量速度。

有关投放吞吐量的更多信息，请参阅 [此部分](../../reporting/using/global-reports.md#delivery-throughput).

>[!NOTE]
>
>使用 [电子邮件反馈服务](#email-feedback-service) (EFS)功能（目前作为测试版提供），“促销活动投放”吞吐量图仍显示电子邮件收件人的吞吐量。

### 重试

Campaign不再使用投放中的重试设置。 软退件重试次数及其间隔时间，由Enhanced MTA根据从消息电子邮件域返回的退回响应的类型和严重性确定。

有关重试的更多信息，请参阅 [此部分](steps-sending-the-delivery.md#configuring-retries).

### 有效期

仅当将设置为 **3.5天或以下**. 如果您在Campaign中定义的值超过3.5天，则不会将其考虑在内。

例如，如果在Campaign中将有效期设置为默认值5天，则软跳出消息将进入Enhanced MTA重试队列，并在消息到达Enhanced MTA后仅重试3.5天。 在这种情况下，将不使用Campaign中设置的值。

消息在 Enhanced MTA 队列中停留 3.5 天且投放失败后，该消息将超时，在投放日志中的状态将从 **[!UICONTROL Sent]** 更新为 **[!UICONTROL Failed]**。

有关有效期的更多信息，请参阅 [此部分](steps-sending-the-delivery.md#defining-validity-period).

### DKIM签名

DKIM（域名识别邮件）电子邮件身份验证签名由Enhanced MTA完成。 在本机Campaign MTA的DKIM签名将在域管理表中作为Enhanced MTA升级的一部分关闭。
有关DKIM的更多信息，请参阅 [Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 交付成功报告

在 **[!UICONTROL Summary]** 电子邮件投放的视图 [仪表板](delivery-dashboard.md), **[!UICONTROL Success]** 百分比从100%开始，然后在整个交付过程中逐渐下降 [有效期](steps-sending-the-delivery.md#defining-validity-period)，因为软退回和硬退回会从Enhanced MTA报告回Campaign。

事实上，所有报文都显示为 **[!UICONTROL Sent]** 在 [发送日志](delivery-dashboard.md#delivery-logs-and-history) 一旦成功从Campaign中转到增强型MTA，就立即将它们转发到。 除非或直到 [跳出](understanding-delivery-failures.md#delivery-failure-types-and-reasons) ，则该消息会从Enhanced MTA传回至Campaign。

当硬弹回消息从增强型MTA报告回时，其状态会从 **[!UICONTROL Sent]** to **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比相应地减少。

当从增强MTA报告软弹回消息时，它们仍显示为 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比尚未更新。 然后是软弹跳消息 [重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 在整个投放有效期内：

* 如果在有效期结束前重试成功，则消息状态将保持为 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比保持不变。

* 否则，状态将更改为 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比相应地减少。

因此，您应等到有效期结束才查看最终 **[!UICONTROL Success]** 百分比，以及实际的 **[!UICONTROL Sent]** 和 **[!UICONTROL Failed]** 消息。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 电子邮件反馈服务（测试版） {#email-feedback-service}

利用电子邮件反馈服务(EFS)功能，可以准确报告每封电子邮件的状态，因为反馈是直接从增强型MTA（邮件传输代理）中捕获的。

>[!IMPORTANT]
>
>电子邮件反馈服务当前作为测试版功能提供。
>
>如果您有兴趣参加此测试版计划，请填写 [此窗体](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) 我们会回到你身边。

投放开始后， **[!UICONTROL Success]** 成功从Campaign中继到增强型MTA时的百分比。

<!--![](assets/efs-sending.png)-->

投放日志显示 **[!UICONTROL Taken into account by the service provider]** 每个目标地址的状态。

<!--![](assets/efs-pending.png)-->

当消息实际被投放到目标用户档案，并且从Enhanced MTA实时报告此信息后，投放日志会显示 **[!UICONTROL Sent]** 成功接收消息的每个地址的状态。 的 **[!UICONTROL Success]** 百分比随每次成功交付而相应增加。

当硬弹回消息从增强型MTA返回报告时，其日志状态会从 **[!UICONTROL Taken into account by the service provider]** to **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

当从Enhanced MTA报告软弹回消息时，其日志状态保持不变(**[!UICONTROL Taken into account by the service provider]**):只有 [错误原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 已更新<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. 的 **[!UICONTROL Success]** 百分比保持不变。 然后，在整个投放中重试软弹回消息 [有效期](steps-sending-the-delivery.md#defining-validity-period):

* 如果在有效期结束前重试成功，则消息状态将更改为 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比也相应地增加。

* 否则，状态将更改为 **[!UICONTROL Failed]**. 的 **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->百分比保持不变。

>[!NOTE]
>
>有关硬退回和软退回的更多信息，请参阅 [此部分](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>有关投放临时失败后重试的更多信息，请参阅 [此部分](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


下表显示了EFS功能引入的KPI变化以及发送日志状态。

**使用电子邮件反馈服务**

| 发送流程中的步骤 | KPI摘要 | 发送日志状态 |
|--- |--- |--- |
| 已成功将消息从Campaign中继到增强MTA | **[!UICONTROL Success]** 百分比未显示（从0%开始） | 由服务提供商考虑 |
| 硬弹回消息从增强的MTA中报回 | 中未更改 **[!UICONTROL Success]** 百分比 | 已失败 |
| 从Enhanced MTA报告软弹回消息 | 中未更改 **[!UICONTROL Success]** 百分比 | 由服务提供商考虑 |
| 软弹回消息重试成功 | **[!UICONTROL Success]** 百分比相应地增加 | 已发送 |
| 软弹回消息重试失败 | 中未更改 **[!UICONTROL Success]** 百分比 | 已失败 |

**没有电子邮件反馈服务**

| 发送流程中的步骤 | KPI摘要 | 发送日志状态 |
|--- |--- |--- |
| 已成功将消息从Campaign中继到增强MTA | **[!UICONTROL Success]** 百分比从100%开始 | 已发送 |
| 硬弹回消息从增强的MTA中报回 | **[!UICONTROL Success]** 百分比相应降低 | 已失败 |
| 从Enhanced MTA报告软弹回消息 | 中未更改 **[!UICONTROL Success]** 百分比 | 已发送 |
| 软弹回消息重试成功 | 中未更改 **[!UICONTROL Success]** 百分比 | 已发送 | **[!UICONTROL Success]** 百分比相应地增加 | 已发送 |
| 软弹回消息重试失败 | **[!UICONTROL Success]** 百分比相应降低 | 已失败 |
