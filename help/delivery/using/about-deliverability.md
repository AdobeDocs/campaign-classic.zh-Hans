---
solution: Campaign Classic
product: campaign
title: 关于活动中的可交付性
description: 了解交付能力最佳实践
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 0420de856d1506ab92d8f0e0824bf439e0ac7dc7
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 5%

---


# 什么是可交付性{#about-deliverability}

可交付性允许您衡量活动到达收件人收件箱时的成功程度，而不会出现弹跳或标记为垃圾邮件。 [了解为何交付能力很重要](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters)。

更准确地说，电子邮件可发送性是指一系列特征，这些特征决定了邮件在短时间内通过个人电子邮件地址到达其目的地的能力，并在内容和格式方面达到预期的质量。

要更深入地了解哪些是可交付性，并了解关键可交付性术语、概念和方法的更多信息，请参阅[Adobe可交付性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)。

## 如何提高交付能力{#deliverability-key-points}

传送能力问题通常与互联网服务提供商和邮件服务器管理员实施的防垃圾邮件措施有关。

* 有关如何设计成功的电子邮件营销活动的一般建议，请参阅[可交付性战略和定义](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html)。

* 有关如何优化Adobe Campaign电子邮件的可交付性的更多具体建议，Adobe建议使用本节中列出的最佳实践。

>[!NOTE]
>
>由于ISP必须不断开发新的复杂过滤技术以保护其客户免受垃圾邮件发送者的攻击，因此电子邮件的发送能力的特点是不断变化的标准和规则。 请确保参阅定期更新的[Adobe交付能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)。

### 可交付率

交付能力率是点击收件人收件箱的邮件数与已传递的邮件数相比。 要提高交付能力，您可能会努力提高此比率。

对于Adobe Campaign，可交付率取决于许多因素，特别是：

* 正确配置实例：请联系您的Adobe代表以获得帮助。
* 合法网络配置：请参阅[本节](../../delivery/using/optimize-delivery.md#network-config)和[域设置和策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy)。
* 您的IP地址信誉：请参阅[ IP战略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy)。
* 目标地址的质量：请参阅[隔离管理](../../delivery/using/optimize-delivery.md#quarantine-management)。
* 低[投诉](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html)和[硬跳出率](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces)。
* 您的消息内容：请参阅[控制电子邮件内容](../../delivery/using/control-message-content.md)。
* 邮件身份验证(SPF、DKIM、DMARC):请参阅[此部分](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。
* 发件人声誉：要了解主ISP如何评估发送方的信誉，请参阅[本节](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html)。

## 活动交付工具{#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign提供多种工具来跟踪和改进您的平台的交付性能。 本页还强调了在使用活动时优化交付能力时应牢记的主要原则。

### 仔细构建您的信息

在配置、设计和测试消息时，请确保遵循以下部分中提到的最佳实践。 利用Adobe Campaign提供的所有功能可帮助您提高交付能力。

* [投放最佳实践](../../delivery/using/delivery-best-practices.md)
* [控制电子邮件内容](../../delivery/using/control-message-content.md)
* [收件箱呈现](../../delivery/using/inbox-rendering.md)
* [发送验证](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)

### 通过多次选择加入{#double-opt-in}验证同意

为了避免向无效地址发送消息、限制不当通信并改善发送者信誉，Adobe建议实施多次选择加入机制。 通过此方法，您可以确保收件人有意订阅。

有关详细信息，请参阅[使用多次 opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)创建订阅表单。

有关从客户收集数据时的最佳实践的更多信息，请参阅[《Adobe交付性最佳实践指南》](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene)。

### 利用隔离管理

Adobe Campaign管理一个列表，可以收集一致发生的垃圾邮件投诉、硬弹回和软弹回。

为保护您的可交付性，默认情况下，其地址位于该列表上的收件人将被排除在将来所有投放之外，因为发送到这些联系人可能会损害您的发送信誉。

如果无效地址率过高，某些互联网访问提供商会自动将电子邮件判断为垃圾邮件。因此，隔离可以使您避免被这阻止列表些提供商添加到。

有关此方面的详细信息，请参阅以下部分：

* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [了解隔离管理](../../delivery/using/understanding-quarantine-management.md)
* [隔离与阻止列表](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### 使用监视和报告工具

使用Adobe Campaign提供的功能监控您的交付能力。

Adobe Campaign允许您通过一套内置实时指标和报告检查投放的表现，以便更好地了解投放。

有关此方面的详细信息，请参阅以下部分：

* [监控投放能力](../../delivery/using/monitoring-deliverability.md)
* [关于投放监视](../../delivery/using/about-delivery-monitoring.md)
* [关于 Campaign 内置报告](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->
