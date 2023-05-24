---
product: campaign
title: Adobe Campaign Classic中的增强MTA的
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



此 **Adobe Campaign Enhanced MTA** （邮件传输代理）提供升级的发送基础架构，从而改进可投放性、信誉、吞吐量、报告、退回处理、IP提升和连接设置管理。

实施它可提高可扩展性、提高投放吞吐量并帮助更快地发送更多电子邮件。 这是通过新的自适应投放技术实现的，该技术根据互联网服务提供商的反馈实时更改电子邮件发送设置。

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA仅适用于托管Campaign Classic或混合型客户。 无法将Campaign Classic内部部署安装升级为使用增强型MTA。

如果您在2018年9月之后配置了Campaign Classic实例，则您使用的是增强MTA。 对于所有其他Campaign Classic客户，请参阅 [常见问题解答](#enhanced-mta-faq) 下面的。

增强的MTA实施可能会影响一些现有Campaign功能。 有关此内容的更多信息，请参见 [增强的MTA特异性](#enhanced-mta-impacts).

>[!NOTE]
>
>如果您是Adobe Campaign的最终用户，并且想知道实例是否已升级到增强MTA，请联系您的内部Campaign管理员。

## 常见问题 {#enhanced-mta-faq}

### 使用情况和好处

**什么是增强MTA？**

Adobe Campaign现在可以升级，以使用新的MTA（邮件传输代理），该代理运行SparkPost的商业电子邮件MTA，称为 **动量**.

Momentum代表着一种创新的、高性能的MTA技术，其中包括更智能的退回处理以及自动化可投放性优化功能，可帮助发件人实现并维持最佳的收件箱投放率。 <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**有哪些好处？**

* 使用增强型MTA的Adobe Campaign客户端发现 <!--300%-->整体吞吐量速度的大幅提升，以及 <!--90%+-->显着减少了软退回。
* Enhanced MTA使用最新的MTA技术，为您的电子邮件投放提供最佳吞吐量速度。
* 通过即时和自动地适应它收到的反馈，它还可以确保使用实时投放数据更准确、更智能地投放电子邮件。

**我是否可以同时使用本机Adobe Campaign MTA和增强MTA？**

没有。实例升级后，只有增强型MTA可用于电子邮件投放。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升级至增强型MTA

**升级到Enhanced MTA需要什么？**

如果您在2018年9月之后配置了Campaign Classic实例，则无需执行任何操作，因为您已在使用增强MTA。

对于所有其他托管或部分托管（混合）的客户，Adobe Campaign团队将联系协调迁移日期，并提供有关迁移所需的相应步骤的详细信息。

>[!IMPORTANT]
>
>增强型MTA不适用于内部部署。

**将我的实例升级到增强MTA的过程是怎样的？**

托管实例的整个过程需要几分钟的停机时间。 Adobe将在升级后24小时内监控电子邮件吞吐量和可投放性，以评估对电子邮件投放的任何影响。

如果发现任何问题，Adobe可以快速地将您的实例暂时还原回本机Adobe Campaign MTA。

目前，增强型MTA仅影响电子邮件渠道。 您的推送通知和短信投放将继续使用本机Campaign MTA，不会受到升级的任何影响。

**升级到Enhanced MTA后，是否需要再次进行IP预热？**

没有。升级不需要切换到新IP，因此您可以继续使用现有、温暖的电子邮件IP。

**升级到增强MTA是否会影响当前正在进行的任何活动或投放？**

在升级实例以使用增强MTA之前准备的任何投放，都需要重新准备才能正确使用新MTA。

对于使用Adobe Campaign事务性消息传递功能的客户，触发电子邮件的任何API调用都将在极短的升级停机时间内排队，并在升级完成后尝试。

## 增强的MTA特异性 {#enhanced-mta-impacts}

### 增强的MTA标头

最新的Campaign Classic实例包含向每封邮件添加所需Enhanced MTA标头的代码。 如果您使用的是Adobe Campaign 19.1（内部版本9032）或更高版本，并且如果不是这种情况，则必须请求 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 将“useMomentum=true”参数添加到执行实例配置(在 [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) 文件)，可以是您的营销实例， [中间源实例](../../installation/using/mid-sourcing-server.md)，或 [事务性消息传递执行实例](../../message-center/using/configuring-instances.md#execution-instance)，具体取决于您的配置。

但是，如果您使用的旧实例不包括此代码，则会有一个名为的新分类规则 **[!UICONTROL Typology Rule for Enhanced MTAs]** 必须添加到Campaign实例中的所有现有分类中。
此规则由添加 **[!UICONTROL Typology]** 在升级到增强MTA时安装的包。

>[!IMPORTANT]
>
>如果您在分类中看到此分类规则，请不要以任何方式删除或修改它。 否则，您的电子邮件投放可能会受到不利影响。

此 **[!UICONTROL Typology]** 程序包需要安装在Adobe Campaign营销实例上。

如果您是混合客户端，Adobe Campaign团队将为您提供有关如何安装 **[!UICONTROL Typology]** 作为升级到增强MTA的一部分，在营销实例上打包。 请联系您的客户经理以获取完整说明。

>[!IMPORTANT]
>
>Adobe Campaign团队提供的关于如何安装 **[!UICONTROL Typology]** 包裹要小心携带。 否则，您可能会遇到用于发送电子邮件的IP的主要问题。

有关分类的详细信息，请参阅 [本节](../../campaign-opt/using/about-campaign-typologies.md).

### 新的MX规则

不再使用MX管理投放吞吐量规则。 Enhanced MTA有自己的MX规则，这些规则允许MTA根据您自己的历史电子邮件信誉以及来自您发送电子邮件之域名的实时反馈，按域自定义您的吞吐量。

有关MX配置的更多信息，请参见 [本节](../../installation/using/email-deliverability.md#mx-configuration).

### 退回鉴别

Campaign中的退回鉴别 **[!UICONTROL Delivery log qualification]** 表不再用于 **同步** 投放失败错误消息。 增强型MTA可确定退回类型和鉴别，并将该信息发送回Campaign。

>[!NOTE]
>
>Enhanced MTA符合SMTP退回的条件，并以映射到Campaign退回原因和条件的退回代码的形式将该条件发送回Campaign。

有关退回鉴别的更多信息，请参阅 [本节](understanding-delivery-failures.md#bounce-mail-qualification).

### 投放吞吐量

Campaign投放吞吐量图表将不再向电子邮件收件人显示吞吐量。 该图现在将显示消息从Campaign中继到Enhanced MTA的吞吐量速度。

有关投放吞吐量的更多信息，请参阅 [本节](../../reporting/using/global-reports.md#delivery-throughput).

>[!NOTE]
>
>使用 [电子邮件反馈服务](#email-feedback-service) (EFS)功能（当前为测试版），Campaign投放吞吐量图表仍显示发送给电子邮件收件人的吞吐量。

### 重试

Campaign不再使用投放中的重试设置。 软退回重试次数以及它们之间的时间长度由Enhanced MTA根据从消息的电子邮件域返回的退回响应的类型和严重性确定。

有关重试的详细信息，请参阅 [本节](steps-sending-the-delivery.md#configuring-retries).

### 有效期

Campaign投放中的有效期设置只有设置为时，Enhanced MTA才会使用 **3.5天或以下**. 如果您在Campaign中定义的值超过3.5天，则不会考虑该值。

例如，如果在Campaign中将有效期设置为默认值5天，则软退回消息将进入Enhanced MTA重试队列，并从该消息到达Enhanced MTA时起最多重试3.5天。 在这种情况下，将不使用Campaign中设置的值。

消息在 Enhanced MTA 队列中停留 3.5 天且投放失败后，该消息将超时，在投放日志中的状态将从 **[!UICONTROL Sent]** 更新为 **[!UICONTROL Failed]**。

有关有效期的更多信息，请参阅 [本节](steps-sending-the-delivery.md#defining-validity-period).

### DKIM签名

DKIM（域名识别邮件）电子邮件身份验证签名由Enhanced MTA完成。 作为Enhanced MTA升级的一部分，本机Campaign MTA的DKIM签名将在域管理表中关闭。
有关DKIM的更多信息，请参见 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 投放成功报告

在 **[!UICONTROL Summary]** 电子邮件投放视图 [仪表板](delivery-dashboard.md)，则 **[!UICONTROL Success]** 百分比从100%开始，然后在交付过程中逐步下降 [有效期](steps-sending-the-delivery.md#defining-validity-period)，因为软退回和硬退回会从Enhanced MTA报告回Campaign。

事实上，所有消息都显示为 **[!UICONTROL Sent]** 在 [发送日志](delivery-dashboard.md#delivery-logs-and-history) 只要它们成功从Campaign中继到增强型MTA即可。 除非或直至 [跳出](understanding-delivery-failures.md#delivery-failure-types-and-reasons) ，则该消息会从Enhanced MTA传回Campaign。

从Enhanced MTA报告硬退回消息时，其状态将从 **[!UICONTROL Sent]** 到 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比亦会相应减少。

当从Enhanced MTA报告软退回消息时，它们仍显示为 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比尚未更新。 然后，软退回消息 [已重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 在整个投放有效期内：

* 如果在有效期结束前重试成功，则消息状态将保持为 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比保持不变。

* 否则，状态将更改为 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比亦会相应减少。

因此，您应等到有效期结束才能看到最终版本 **[!UICONTROL Success]** 百分比，以及最终实际数量 **[!UICONTROL Sent]** 和 **[!UICONTROL Failed]** 消息。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 电子邮件反馈服务（测试版） {#email-feedback-service}

借助电子邮件反馈服务(EFS)功能，每个电子邮件的状态均可准确报告，因为反馈是直接从Enhanced MTA（邮件传输代理）中捕获的。

>[!IMPORTANT]
>
>电子邮件反馈服务目前作为测试版功能提供。
>
>如果您有兴趣参与此Beta计划，请填写 [此表单](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) 我们会再联系你的。

投放开始后， **[!UICONTROL Success]** 消息成功从Campaign中继到Enhanced MTA时的百分比。

<!--![](assets/efs-sending.png)-->

投放日志显示 **[!UICONTROL Taken into account by the service provider]** 每个目标地址的状态。

<!--![](assets/efs-pending.png)-->

当消息实际发送到目标用户档案并且一旦从Enhanced MTA实时报告此信息后，投放日志显示 **[!UICONTROL Sent]** 成功接收消息的每个地址的状态。 此 **[!UICONTROL Success]** 百分比会随着每次成功交付而相应增加。

从Enhanced MTA报告硬退回消息时，其日志状态将从 **[!UICONTROL Taken into account by the service provider]** 到 **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

从Enhanced MTA报告软退回消息时，其日志状态保持不变(**[!UICONTROL Taken into account by the service provider]**)：仅 [错误原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 已更新<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. 此 **[!UICONTROL Success]** 百分比保持不变。 然后，在整个投放过程中重试软退回消息 [有效期](steps-sending-the-delivery.md#defining-validity-period)：

* 如果在有效期结束前重试成功，则消息状态将更改为 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比亦会相应增加。

* 否则，状态将更改为 **[!UICONTROL Failed]**. 此 **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->百分比保持不变。

>[!NOTE]
>
>有关硬退信和软退信的更多信息，请参阅 [本节](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>有关投放临时失败后重试的更多信息，请参阅 [本节](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


下表显示了EFS功能引入的KPI和发送日志状态的变化。

**使用电子邮件反馈服务**

| 发送过程中的步骤 | KPI摘要 | 发送日志状态 |
|--- |--- |--- |
| 消息已成功从Campaign中继到增强型MTA | **[!UICONTROL Success]** 百分比不显示（从0%开始） | 由服务提供商考虑 |
| 从Enhanced MTA返回硬退回消息 | 无更改 **[!UICONTROL Success]** 百分比 | 已失败 |
| 从Enhanced MTA返回软退回消息 | 无更改 **[!UICONTROL Success]** 百分比 | 由服务提供商考虑 |
| 软退回消息重试成功 | **[!UICONTROL Success]** 百分比亦相应增加 | 已发送 |
| 软退回消息重试失败 | 无更改 **[!UICONTROL Success]** 百分比 | 已失败 |

**无电子邮件反馈服务**

| 发送过程中的步骤 | KPI摘要 | 发送日志状态 |
|--- |--- |--- |
| 消息已成功从Campaign中继到增强型MTA | **[!UICONTROL Success]** 百分比从100%开始 | 已发送 |
| 从Enhanced MTA返回硬退回消息 | **[!UICONTROL Success]** 百分比将相应减少 | 已失败 |
| 从Enhanced MTA返回软退回消息 | 无更改 **[!UICONTROL Success]** 百分比 | 已发送 |
| 软退回消息重试成功 | 无更改 **[!UICONTROL Success]** 百分比 | 已发送 | **[!UICONTROL Success]** 百分比亦相应增加 | 已发送 |
| 软退回消息重试失败 | **[!UICONTROL Success]** 百分比将相应减少 | 已失败 |
