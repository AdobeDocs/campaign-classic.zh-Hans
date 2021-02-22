---
solution: Campaign Classic
product: campaign
title: 使用Adobe Campaign Classic中增强的MTA发送
description: 了解使用Adobe Campaign增强的MTA发送电子邮件的范围和特性。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: c64b6eccd0ad45ebcf4ecc18150f4409f5c66bc2
workflow-type: tm+mt
source-wordcount: '1880'
ht-degree: 2%

---


# 使用增强的MTA {#sending-with-enhanced-mta}发送

**Adobe Campaign增强MTA**（邮件传输代理）提供了升级的发送基础架构，允许改进的发送能力、信誉、吞吐量、报告、跳出处理、IP加速和连接设置管理。

它的实施旨在提高可扩展性、提高投放吞吐量并帮助更快发送更多电子邮件。 这是通过新的自适应投放技术实现的，这些技术根据来自因特网服务提供商的反馈实时更改电子邮件发送设置。

>[!IMPORTANT]
>
>Adobe Campaign增强MTA仅适用于Campaign Classic托管或混合客户。 Campaign Classic本地安装无法升级为使用增强的MTA。

如果您在2018年9月之后设置了Campaign Classic实例，则您使用的是增强的MTA。 对于所有其他Campaign Classic客户，请参阅下面的[常见问题解答](#enhanced-mta-faq)。

增强的MTA实施可能会影响一些现有的活动功能。 有关详细信息，请参阅[增强的MTA特性](#enhanced-mta-impacts)。

>[!NOTE]
>
>如果您是Adobe Campaign的最终用户，并且想了解您的实例是否已升级到增强的MTA，请与您的内部活动管理员联系。

## 常见问题 {#enhanced-mta-faq}

### 使用和优势

**什么是增强的MTA?**

现在可以升级Adobe Campaign以使用新的MTA（邮件传输代理），该MTA运行SparkPost的名为&#x200B;**Momentum**&#x200B;的商业电子邮件MTA。

Momentum代表了创新的高性能MTA技术，其中包括更智能的弹回处理和自动化的可交付性优化功能，可帮助发送方实现和保持最佳收件箱投放率。<!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**有什么好处？**

* 使用增强MTA的Adobe Campaign客户端的整体吞吐量速度显着提高<!--300%-->，软边界显着降低<!--90%+-->。
* 增强的MTA使用最新的MTA技术为您的电子邮件投放提供最佳吞吐量速度。
* 通过即时、自动地适应收到的反馈，它还可确保利用实时投放数据实现更准确、智能的电子邮件投放。

**我是否可以同时使用本机Adobe CampaignMTA和增强MTA?**

不。 在实例升级后，只有增强的MTA才能用于您的电子邮件投放。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升级到增强的MTA

**升级到增强MTA需要什么？**

如果您在2018年9月之后设置了Campaign Classic实例，则不需要执行任何操作，因为您已经在使用增强的MTA。

对于所有其他托管或部分托管（混合）客户，Adobe Campaign团队将联系起来，协调迁移日期，并提供迁移所需适当步骤的详细信息。

>[!IMPORTANT]
>
>增强的MTA不适用于内部部署安装。

**将我的实例升级到增强MTA的过程是什么？**

托管实例的整个过程需要几分钟的停机时间。 Adobe将在最长24小时的升级后监控电子邮件吞吐量和交付能力，以评估对您的电子邮件投放的任何影响。

如果发现任何问题，Adobe可以快速并临时将您的实例还原到本机Adobe CampaignMTA。

目前，增强的MTA仅影响电子邮件渠道。 您的推送通知和SMS投放将继续使用本机活动MTA，并且不会因升级而受到任何影响。

**升级到增强的MTA后，是否需要再次经历IP变暖？**

不。 升级不需要切换到新IP，因此您可以继续使用现有的已热电子邮件IP。

**升级到增强的MTA会影响当前进行中的任何活动或投放吗？**

在实例升级为使用增强的MTA之前准备的任何投放都需要重新准备，才能正确使用新的MTA。

对于使用Adobe Campaign事务消息功能的客户，任何用于触发电子邮件的API调用都将在非常短的升级停机时间内排队，并在完成升级后尝试进行。

## 增强的MTA特性{#enhanced-mta-impacts}

### 增强的MTA标头

最新的Campaign Classic实例包括将所需的增强MTA头添加到每条消息的代码。 如果您使用的是Adobe Campaign 19.1（内部版本9032）或更高版本，并且不是这种情况，则必须将“useMomentum=true”参数添加到您的营销实例配置（在[serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)文件中）。

但是，如果您使用的是不包含此代码的旧实例，则必须将名为&#x200B;**[!UICONTROL Typology Rule for Enhanced MTAs]**的新类型规则添加到活动实例中的所有现有类型中。
此规则由作为升级到增强MTA的一部分安装的**[!UICONTROL Typology]**&#x200B;包添加。

>[!IMPORTANT]
>
>如果您在字体中看到此类型规则，请勿以任何方式删除或修改它。 否则，您的电子邮件投放可能会受到不利影响。

此&#x200B;**[!UICONTROL Typology]**&#x200B;包需要安装在Adobe Campaign营销实例中。

如果您是混合客户端，Adobe Campaign团队将向您提供有关如何在营销实例上安装&#x200B;**[!UICONTROL Typology]**&#x200B;包的说明，以作为升级到增强MTA的一部分。 请联系您的客户经理以获得完整说明。

>[!IMPORTANT]
>
>应仔细遵循Adobe Campaign小组提供的关于如何安装&#x200B;**[!UICONTROL Typology]**&#x200B;包的说明。 否则，您可能会遇到用于发送电子邮件的IP的重大问题。

有关类型的详细信息，请参阅[此部分](../../campaign/using/about-campaign-typologies.md)。

### 新的MX规则

不再使用MX管理投放吞吐量规则。 “增强的MTA”有其自己的MX规则，允许其根据您的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，按域自定义您的吞吐量。

有关MX配置的详细信息，请参阅[本节](../../installation/using/email-deliverability.md#mx-configuration)。

### 退出资格

活动&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表中的跳出资格不再用于&#x200B;**同步**&#x200B;投放失败错误消息。 增强的MTA可确定跳出类型和资格，并将该信息发回给活动。

>[!NOTE]
>
>增强的MTA可验证SMTP跳出，并以跳出代码的形式将该资格发送回活动，该跳出代码映射到活动跳出原因和资格。

有关跳出资格的详细信息，请参阅[本节](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)。

### 投放吞吐量

活动投放吞吐量图将不再向您的电子邮件收件人显示吞吐量。 该图现在将显示消息从活动到增强MTA的中继的吞吐量速度。

有关投放吞吐量的详细信息，请参阅[此部分](../../reporting/using/global-reports.md#delivery-throughput)。

### 有效期

仅当设置为&#x200B;**3.5天或更少**&#x200B;时，“增强的MTA”才会使用“活动”投放中的有效期设置。 如果您在活动中定义的值高于3.5天，则不会考虑该值。

例如，如果有效期设置为活动中的默认值5天，则软弹跳消息将进入“增强的MTA重试”队列，并仅在消息到达“增强的MTA”后重试3.5天。 在这种情况下，将不使用在活动中设置的值。

消息在 Enhanced MTA 队列中停留 3.5 天且投放失败后，该消息将超时，在投放日志中的状态将从 **[!UICONTROL Sent]** 更新为 **[!UICONTROL Failed]**。

有关有效期的详细信息，请参阅[此部分](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

### DKIM签名

DKIM(DomainKeys Indifed Mail)电子邮件身份验证签名由增强的MTA完成。 作为增强MTA升级的一部分，本机活动 MTA的DKIM签名将在域管理表中关闭。
有关DKIM的详细信息，请参阅[此部分](../../delivery/using/technical-recommendations.md#dkim)。

### 投放成功报告

在电子邮件投放[仪表板](../../delivery/using/delivery-dashboard.md)的&#x200B;**[!UICONTROL Summary]**&#x200B;视图中，**[!UICONTROL Success]**&#x200B;百分比开始以100%结束，然后在投放[有效期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)期间逐渐下降，因为软和硬弹回从增强MTA报告回活动。

事实上，所有消息在从活动成功中继到增强的MTA后立即在[发送日志](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)中显示为&#x200B;**[!UICONTROL Sent]**。 除非或直到将该消息的[弹回](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)从增强MTA传回活动，否则它们仍保持该状态。

当硬弹回消息从增强的MTA中报告回来时，其状态从&#x200B;**[!UICONTROL Sent]**&#x200B;变为&#x200B;**[!UICONTROL Failed]**，并且&#x200B;**[!UICONTROL Success]**&#x200B;百分比相应地降低。

当从增强的MTA中返回软弹跳消息时，它们仍显示为&#x200B;**[!UICONTROL Sent]**&#x200B;且&#x200B;**[!UICONTROL Success]**&#x200B;百分比尚未更新。 然后，在整个投放有效期内，软弹跳消息将[retried](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure):

* 如果在有效期结束前重试成功，则消息状态将保持为&#x200B;**[!UICONTROL Sent]**&#x200B;且&#x200B;**[!UICONTROL Success]**&#x200B;百分比将保持不变。

* 否则，状态变化为&#x200B;**[!UICONTROL Failed]**&#x200B;并相应地降低&#x200B;**[!UICONTROL Success]**&#x200B;百分比。

因此，您应等到有效期结束时再查看最终&#x200B;**[!UICONTROL Success]**&#x200B;百分比，以及实际&#x200B;**[!UICONTROL Sent]**&#x200B;和&#x200B;**[!UICONTROL Failed]**&#x200B;消息的最终数。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 电子邮件反馈服务（测试版）{#email-feedback-service}

利用电子邮件反馈服务(EFS)功能，可以准确报告每封电子邮件的状态，因为反馈会直接从增强的MTA（邮件传输代理）中捕获。

>[!IMPORTANT]
>
>电子邮件反馈服务目前提供测试版功能。
>
>如果您有兴趣参加此测试版项目，请填写[此表单](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)，我们会回到您。

启动投放后，当消息从活动成功中继到增强的MTA时，**[!UICONTROL Success]**&#x200B;百分比没有变化。

<!--![](assets/efs-sending.png)-->

投放日志显示每个目标地址的&#x200B;**[!UICONTROL Taken into account by the service provider]**&#x200B;状态。

<!--![](assets/efs-pending.png)-->

当消息实际传递到目标用户档案，并且从增强的MTA实时报告此信息后，投放日志将显示成功接收消息的每个地址的&#x200B;**[!UICONTROL Sent]**&#x200B;状态。 每次成功投放,**[!UICONTROL Success]**&#x200B;百分比都相应增加。

当硬弹回消息从增强的MTA报告回来时，其日志状态从&#x200B;**[!UICONTROL Taken into account by the service provider]**&#x200B;更改为&#x200B;**[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->。

当从增强的MTA中报告软弹回消息时，其日志状态保持不变(**[!UICONTROL Taken into account by the service provider]**):只更新[错误原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->。 **[!UICONTROL Success]**&#x200B;百分比保持不变。 然后，在投放[有效期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)中重试软弹跳消息：

* 如果在有效期结束前重试成功，则消息状态将变为&#x200B;**[!UICONTROL Sent]**&#x200B;并相应地增加&#x200B;**[!UICONTROL Success]**&#x200B;百分比。

* 否则，状态将更改为&#x200B;**[!UICONTROL Failed]**。 **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->百分比保持不变。

>[!NOTE]
>
>有关硬弹回和软弹回的详细信息，请参阅[此部分](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
>
>有关投放临时故障后重试的详细信息，请参阅[本节](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。


下表显示EFS功能引入的KPI和发送日志状态的更改。

**通过电子邮件反馈服务**

| 发送过程中的步骤 | KPI摘要 | 发送日志状态 |
|--- |--- |--- |
| 消息从活动成功中继到增强的MTA | **[!UICONTROL Success]** 百分比不显示(开始为0%) | 服务提供商 |
| 硬弹回消息从增强的MTA中返回报告 | **[!UICONTROL Success]**&#x200B;百分比没有变化 | 失败 |
| 从增强的MTA返回软弹跳消息报告 | **[!UICONTROL Success]**&#x200B;百分比没有变化 | 服务提供商 |
| 软弹回消息重试成功 | **[!UICONTROL Success]** 百分比相应增加 | 已发送 |
| 软弹回消息重试失败 | **[!UICONTROL Success]**&#x200B;百分比没有变化 | 失败 |

**无电子邮件反馈服务**

| 发送过程中的步骤 | KPI摘要 | 发送日志状态 |
|--- |--- |--- |
| 消息从活动成功中继到增强的MTA | **[!UICONTROL Success]** 100%的开始 | 已发送 |
| 硬弹回消息从增强的MTA中返回报告 | **[!UICONTROL Success]** 百分比相应减少 | 失败 |
| 从增强的MTA返回软弹跳消息报告 | **[!UICONTROL Success]**&#x200B;百分比没有变化 | 已发送 |
| 软弹回消息重试成功 | **[!UICONTROL Success]**&#x200B;百分比没有变化 | 已发送 | **[!UICONTROL Success]** 百分比相应增加 | 已发送 |
| 软弹回消息重试失败 | **[!UICONTROL Success]** 百分比相应减少 | 失败 |
