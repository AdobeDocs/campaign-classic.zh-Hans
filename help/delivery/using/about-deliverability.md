---
product: campaign
title: Campaign中的可投放性入门
description: 了解可投放性最佳实践
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 9%

---

# 什么是可投放性{#about-deliverability}

通过可投放性，您可以衡量营销活动在到达收件人的收件箱时成功与否，而不会出现退回或标记为垃圾邮件的情况。 [了解可投放性很重要的原因](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

更准确地说，电子邮件可投放性指一组特征，这些特征决定消息在短时间内通过个人电子邮件地址到达其目的地的能力，以及在内容和格式方面达到预期质量。

要更深入地了解什么是可投放性，并详细了解可投放性的关键术语、概念和方法，请参阅 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans).

## 如何提高可投放性 {#deliverability-key-points}

可投放性问题通常与Internet服务提供商和邮件服务器管理员实施的垃圾邮件防护措施有关。

* 有关如何设计成功的电子邮件营销活动的一般建议，请参阅 [可投放性策略和定义](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* 有关如何优化Adobe Campaign电子邮件投放能力的更具体建议，Adobe建议使用本节中列出的最佳实践。

>[!NOTE]
>
>由于ISP有义务不断开发新的复杂过滤技术来保护其客户免受垃圾邮件发送者的攻击，因此电子邮件可投放性具有不断变化的标准和规则的特点。 请确保您参考 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans) 并定期更新。

### 可投放性比率

可投放性比率是点击收件人收件箱的消息数量与已投放的消息数量之比。 为了提高可投放性，您可以努力提高此比率。

使用Adobe Campaign时，可投放性比率取决于多种因素，特别是：

* 实例的正确配置：请联系您的Adobe代表寻求帮助。
* 合法的网络配置：请参阅 [本节](optimize-delivery.md#network-config) 和 [域设置和策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* 您的IP地址信誉：请参阅 [IP策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* 目标地址的质量：请参阅 [隔离管理](optimize-delivery.md#quarantine-management).
* 低 [投诉](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) 和 [硬退回](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) 费率。
* 您的消息内容：请参阅 [控制电子邮件内容](control-message-content.md).
* 消息身份验证(SPF、DKIM、DMARC)：请参阅 [本节](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* 发件人信誉：要了解主要ISP如何评估发件人信誉，请参阅 [本节](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Campaign投放工具 {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign提供了多种工具来跟踪和改进平台的可投放性性能。 本页还重点说明了在使用Campaign时优化投放能力应遵循的主要原则。

### 仔细构建您的消息

配置、设计和测试消息时，请确保遵循以下部分中提到的最佳实践。 利用Adobe Campaign提供的所有功能可帮助您提高可投放性。

* [投放最佳实践](delivery-best-practices.md)
* [控制电子邮件内容](control-message-content.md)
* [收件箱呈现](inbox-rendering.md)
* [发送验证](steps-validating-the-delivery.md#sending-a-proof)

### 通过双重选择加入验证同意 {#double-opt-in}

为避免将消息发送到无效地址、限制不当通信并提高发件人信誉，Adobe建议实施双重选择加入机制。 此方法使您能够确保收件人有意订阅。

有关此内容的更多信息，请参阅[使用双重选择加入创建订阅表单](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。

有关从客户那里收集数据时的最佳实践的更多信息，请参阅 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### 利用隔离管理

Adobe Campaign管理着收集垃圾邮件投诉、硬退回和一致发生的软退回的列表。

为了保护您的可投放性，默认情况下，该列表中地址包含的收件人将从所有未来投放中排除，因为发送给这些联系人可能会损害您的发送信誉。

如果无效地址率过高，某些互联网访问提供商会自动将电子邮件判断为垃圾邮件。因此，隔离可让您避免被这些提供商添加到阻止列表。

有关更多信息，请参阅以下章节：

* [了解投放失败](understanding-delivery-failures.md)
* [了解隔离管理](understanding-quarantine-management.md)
* [隔离与阻止列表](understanding-quarantine-management.md#quarantine-vs-denylist)

### 使用监控和报告工具

使用Adobe Campaign提供的功能监控您的可投放性。

Adobe Campaign允许您通过一组内置的实时指标和报表检查投放的执行情况，从而更好地了解投放情况。

有关更多信息，请参阅以下章节：

* [监测投放能力](monitoring-deliverability.md)
* [投放监测入门](about-delivery-monitoring.md)
* [Campaign内置报告入门](../../reporting/using/about-campaign-built-in-reports.md)
