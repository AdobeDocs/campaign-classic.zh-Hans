---
product: campaign
title: Campaign中的投放能力入门
description: 了解投放能力最佳实践
feature: Deliverability
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 8%

---

# 什么是可投放性{#about-deliverability}

![](../../assets/common.svg)

投放能力允许您衡量活动是否成功到达收件人的收件箱，而不会出现弹回或标记为垃圾邮件。 [了解投放能力为何重要](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

更准确地说，电子邮件投放能力是指一组特征，这些特征决定了消息在短时间内通过个人电子邮件地址到达其目标的能力，并在内容和格式方面具有预期质量。

要更深入地了解什么是可投放性，并了解有关关键可投放性术语、概念和方法的更多信息，请参阅 [Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans).

## 如何提高投放能力 {#deliverability-key-points}

投放能力问题通常与互联网服务提供商和邮件服务器管理员实施的针对垃圾邮件的保护措施有关。

* 有关如何设计成功的电子邮件营销活动的一般建议，请参阅 [投放能力策略和定义](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* 有关如何优化Adobe Campaign电子邮件的投放能力的更多具体建议，Adobe建议使用此部分中列出的最佳实践。

>[!NOTE]
>
>由于ISP必须不断开发新的复杂过滤技术来保护其客户免受垃圾邮件发送者的攻击，因此电子邮件投放能力的特点是标准和规则不断变化。 请确保您参考 [Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) 定期更新。

### 投放能力率

投放能力率是指点击收件人收件箱的消息数量与投放的消息数量之比。 要提高投放能力，您可能会努力提高此投放率。

对于Adobe Campaign，投放能力率取决于多种因素，特别是：

* 正确配置实例：请联系您的Adobe代表以获取帮助。
* 合法的网络配置：请参阅 [此部分](optimize-delivery.md#network-config) 和 [域设置和策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* 您的IP地址信誉：请参阅 [IP策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* 目标地址的质量：请参阅 [隔离管理](optimize-delivery.md#quarantine-management).
* 低 [投诉](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) 和 [硬退回](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) 比率。
* 您的消息内容：请参阅 [控制电子邮件内容](control-message-content.md).
* 报文验证(SPF、DKIM、DMARC):请参阅 [此部分](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* 发件人声誉：要了解主ISP如何评估发件人的信誉，请参阅 [此部分](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Campaign投放能力工具 {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign提供了多种工具来跟踪和改进平台的投放能力性能。 本页还重点介绍了在使用Campaign时，您应当牢记的主要原则，以优化投放能力。

### 仔细构建消息

配置、设计和测试消息时，请确保遵循下面所列部分中提到的最佳实践。 利用Adobe Campaign提供的所有功能，可帮助您提高投放能力。

* [投放最佳实践](delivery-best-practices.md)
* [控制电子邮件内容](control-message-content.md)
* [收件箱呈现](inbox-rendering.md)
* [发送验证](steps-validating-the-delivery.md#sending-a-proof)

### 通过双重选择加入验证同意 {#double-opt-in}

为避免向无效地址发送消息、限制不当通信并提高发件人信誉，Adobe建议实施双重选择加入机制。 通过此方法，您可以确保收件人有意订阅。

有关此内容的更多信息，请参阅[使用双重选择加入创建订阅表单](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。

有关从客户收集数据时的最佳实践的更多信息，请参阅 [Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### 利用隔离管理

Adobe Campaign会管理一个列表，以收集持续发生的垃圾邮件投诉、硬退回和软退回。

为了保护您的投放能力，默认情况下，该列表中包含地址的收件人将被排除在所有未来投放之外，因为发送给这些联系人可能会损害您的发送声誉。

如果无效地址率过高，某些互联网访问提供商会自动将电子邮件判断为垃圾邮件。因此，隔离可让您避免被这些提阻止列表供商添加到。

有关更多信息，请参阅以下章节：

* [了解投放失败](understanding-delivery-failures.md)
* [了解隔离管理](understanding-quarantine-management.md)
* [隔离与阻止列表](understanding-quarantine-management.md#quarantine-vs-denylist)

### 使用监控和报告工具

使用Adobe Campaign提供的功能监控您的投放能力。

Adobe Campaign允许您通过一组内置的实时指示器和报表来检查投放的执行情况，以便更好地分析投放。

有关更多信息，请参阅以下章节：

* [监控投放能力](monitoring-deliverability.md)
* [投放监测入门](about-delivery-monitoring.md)
* [Campaign内置报告入门](../../reporting/using/about-campaign-built-in-reports.md)
