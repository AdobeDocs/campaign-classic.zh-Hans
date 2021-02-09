---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign Classic用增强的MTA发送
description: 了解使用Adobe Campaign增强的MTA发送电子邮件的范围和特性。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 72fdac4afba6c786cfbd31f4a916b0539ad833e3
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 2%

---


# 使用增强的MTA{#sending-with-enhanced-mta}发送

**Adobe Campaign增强MTA**（邮件传输代理）提供升级的发送基础结构，允许改进发送能力、信誉、吞吐量、报告、弹回处理、IP加速和连接设置管理。

它的实施旨在提高可伸缩性、提高投放吞吐量并帮助更快地发送更多电子邮件。 这是通过新的自适应投放技术实现的，这些技术根据来自因特网服务提供商的反馈实时更改电子邮件发送设置。

>[!IMPORTANT]
>
>Adobe Campaign增强MTA仅适用于Campaign Classic托管或混合客户。 Campaign Classic本地安装无法升级为使用增强的MTA。

如果您在2018年9月后设置了Campaign Classic实例，则您正在使用增强的MTA。 对于所有其他Campaign Classic客户，请参阅下面的[常见问题解答](#enhanced-mta-faq)。

增强的MTA实施可能会影响一些现有的活动功能。 有关详细信息，请参阅[增强的MTA特性](#enhanced-mta-impacts)。

## 常见问题 {#enhanced-mta-faq}

### 使用和优势

**什么是增强的MTA?**

Adobe Campaign现在可升级为使用新的MTA（邮件传输代理），该代理运行SparkPost的名为&#x200B;**Momentum**&#x200B;的商业电子邮件MTA。

Momentum代表创新的高性能MTA技术，包括更智能的弹回处理和自动投放能力优化功能，可帮助发送方实现并保持最佳收件箱投放率。<!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**有什么好处？**

* 使用增强MTA的Adobe Campaign客户端的总吞吐量速度大幅提高<!--300%-->，软边界显着降低<!--90%+-->。
* 增强的MTA使用最新的MTA技术为您的电子邮件投放提供最佳吞吐量速度。
* 通过即时、自动地适应收到的反馈，它还确保了利用实时投放数据进行更准确、智能的电子邮件投放。

**我是否可以同时使用本机Adobe CampaignMTA和增强MTA?**

不。 在实例升级后，只有增强的MTA才能用于电子邮件投放。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升级到增强的MTA

**升级到增强MTA需要什么？**

如果您在2018年9月后设置了Campaign Classic实例，则无需执行任何操作，因为您已在使用增强的MTA。

对于所有其他托管或部分托管（混合）客户，Adobe Campaign团队将联系协调迁移日期，并提供迁移所需的适当步骤的详细信息。

>[!IMPORTANT]
>
>增强的MTA不适用于本地安装。

**将我的实例升级到增强的MTA的过程是什么？**

托管实例的整个过程需要几分钟的停机时间。 Adobe将在最长24小时的升级后监控电子邮件吞吐量和交付能力，以评估对您的电子邮件投放的任何影响。

如果发现任何问题，Adobe可以快速临时将实例还原回原生Adobe CampaignMTA。

目前，增强的MTA仅影响电子邮件渠道。 您的推送通知和SMS投放将继续使用本机活动MTA，并且不会因升级而受到任何影响。

**升级到增强的MTA后，是否需要再次经历IP变暖？**

不。 升级不需要切换到新IP，因此您可以继续使用现有的热电子邮件IP。

**升级到增强型MTA是否会影响任何当前进行中的活动或投放?**

在实例升级为使用增强MTA之前准备的任何投放都需要重新准备，才能正确使用新MTA。

对于使用Adobe Campaign事务消息功能的客户，任何触发电子邮件的API调用都将在非常短的升级停机时间排队，并在升级完成后尝试进行。

## 增强的MTA特性{#enhanced-mta-impacts}

### 增强的MTA头

最新Campaign Classic实例包括将所需的增强MTA头添加到每条消息的代码。 如果您使用的是Adobe Campaign19.1（内部版本9032）或更高版本，并且不是这种情况，则必须在您的营销实例配置中添加“useMomentum=true”参数（在[serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)文件中）。

但是，如果您使用的旧实例不包含此代码，则必须向活动实例中的所有现有类型添加一个名为&#x200B;**[!UICONTROL Typology Rule for Enhanced MTAs]**的新类型规则。
此规则由作为升级到增强MTA的一部分安装的**[!UICONTROL Typology]**&#x200B;软件包添加。

>[!IMPORTANT]
>
>如果您在字体中看到此类型规则，请勿以任何方式删除或修改它。 否则，您的电子邮件投放可能会受到不利影响。

此&#x200B;**[!UICONTROL Typology]**&#x200B;包需要安装在Adobe Campaign营销实例上。

如果您是混合客户端，Adobe Campaign团队将向您提供有关如何在营销实例上安装&#x200B;**[!UICONTROL Typology]**&#x200B;包的说明，以作为升级到增强MTA的一部分。 请联系您的客户经理以获取完整说明。

>[!IMPORTANT]
>
>Adobe Campaign小组提供的关于如何安装&#x200B;**[!UICONTROL Typology]**&#x200B;软件包的说明应当得到仔细遵循。 否则，您可能会遇到用于发送电子邮件的IP的主要问题。

有关类型的详细信息，请参阅[此部分](../../campaign/using/about-campaign-typologies.md)。

### 新的MX规则

不再使用MX管理投放吞吐量规则。 增强的MTA有其自己的MX规则，允许它根据您自己的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，按域自定义您的吞吐量。

有关MX配置的详细信息，请参见[本节](../../installation/using/email-deliverability.md#mx-configuration)。

### 退回资格

活动&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表中的弹回资格不再用于&#x200B;**同步**&#x200B;投放故障错误消息。 增强的MTA可确定退回类型和资格，并将该信息发回给活动。

>[!NOTE]
>
>增强的MTA可以验证SMTP退回的资格，并将该资格以弹回代码的形式发送回活动，该代码映射为活动退回原因和资格。

有关退回资格的详细信息，请参阅[此部分](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)。

### 具有增强的MTA的已发送状态

在电子邮件投放[仪表板](../../delivery/using/delivery-dashboard.md)的&#x200B;**[!UICONTROL Summary]**&#x200B;视图中，**[!UICONTROL Success]**&#x200B;百分比开始以100%的比例释放，然后在投放[有效期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)中逐渐下降，因为软和硬弹回从增强的MTA报告回活动。

事实上，一旦成功从活动中继到增强的MTA，所有消息在[发送日志](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)中都显示为&#x200B;**[!UICONTROL Sent]**。 除非或直到消息的[弹回](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)从增强的MTA传回到活动，否则它们将保持该状态。

当硬弹回消息从增强的MTA报告回来时，其状态从&#x200B;**[!UICONTROL Sent]**&#x200B;变为&#x200B;**[!UICONTROL Failed]**，并且&#x200B;**[!UICONTROL Success]**&#x200B;百分比相应降低。

当从增强的MTA返回软弹跳消息时，它们仍显示为&#x200B;**[!UICONTROL Sent]**，且&#x200B;**[!UICONTROL Success]**&#x200B;百分比尚未更新。 然后，在投放有效期内，软弹跳消息将[重试](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure):

* 如果在有效期结束前重试成功，则消息状态将保持为&#x200B;**[!UICONTROL Sent]**，而&#x200B;**[!UICONTROL Success]**&#x200B;百分比将保持不变。

* 否则，状态变化为&#x200B;**[!UICONTROL Failed]**，而&#x200B;**[!UICONTROL Success]**&#x200B;百分比会相应降低。

因此，您应等到有效期结束时才能看到最终&#x200B;**[!UICONTROL Success]**&#x200B;百分比以及实际&#x200B;**[!UICONTROL Sent]**&#x200B;和&#x200B;**[!UICONTROL Failed]**&#x200B;消息的最终数。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

## 投放吞吐量

活动投放吞吐量图将不再显示电子邮件收件人的吞吐量。 该图现在将显示消息从活动到增强MTA的中继的吞吐量速度。

有关投放吞吐量的详细信息，请参见[此部分](../../reporting/using/global-reports.md#delivery-throughput)。

### 有效期

仅当设置为&#x200B;**3.5天或更少**&#x200B;时，活动投放中的有效期设置才会由增强的MTA使用。 如果您在活动中定义的值高于3.5天，则不会将其考虑在内。

例如，如果有效期在活动中设置为默认值5天，则软弹跳消息将进入增强MTA重试队列，并在消息到达增强MTA后最多重试3.5天。 在这种情况下，将不使用在活动中设置的值。

消息在 Enhanced MTA 队列中停留 3.5 天且投放失败后，该消息将超时，在投放日志中的状态将从 **[!UICONTROL Sent]** 更新为 **[!UICONTROL Failed]**。

有关有效期的详细信息，请参阅[此部分](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

## DKIM签名

DKIM(DomainKeys Inded Mail)电子邮件身份验证签名由增强的MTA完成。 作为增强的MTA升级的一部分，本机活动MTA的DKIM签名将在域管理表中关闭。
有关DKIM的详细信息，请参阅[此部分](../../delivery/using/technical-recommendations.md#dkim)。