---
product: campaign
title: 投放性能最佳实践
description: 了解有关投放性能和最佳实践的更多信息。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 6%

---

# 投放性能最佳实践 {#delivery-performances}

我们建议遵循以下准则，以确保投放性能良好，并检查在遇到投放问题时执行的操作。

**相关主题：**

* [投放仪表板](../../delivery/using/delivery-dashboard.md)
* [投放疑难解答](../../delivery/using/delivery-troubleshooting.md)
* [关于投放能力](../../delivery/using/about-deliverability.md)

## 性能最佳实践{#best-practices-performance}

* 请勿在实例上将投放保持为失败状态，因为这会维护临时表并影响性能。

* 删除不再需要的投放。

* 过去12个月内不活动的收件人将从数据库中删除以保持地址质量。

* 请勿尝试同时计划大型投放。 在系统上均匀分布负载需要5-10分钟的时间。 与团队的其他成员协调投放计划以确保获得最佳性能。 当营销服务器同时处理多个不同的任务时，可能会降低性能。

* 尽量保持电子邮件的大小。 建议的电子邮件最大大小约为35KB。 电子邮件投放的大小会在发送服务器中生成一定数量的卷。

* 大型投放（如向超过百万个收件人的投放）需要在发送队列中留出空间。 单单这一点对服务器来说不是问题，但是，如果与大量其他大型投放同时发出，则可能会引发发送延迟。

* 电子邮件中的个性化会从数据库中提取每个收件人的数据。 如果存在多个个性化元素，则会增加准备投放所需的数据量。

* 索引地址。 要优化应用程序中使用的SQL查询的性能，可以从数据模式的主元素中声明索引。

>[!NOTE]
>
>ISP会在地址处于不活动状态一段时间后停用地址。 退回邮件将发送给发件人，以告知他们此新状态。

## 性能问题检查列表{#performance-issues}

如果投放性能不佳，您可以检查：

* **投放的大小**:完成大型投放可能需要较长时间。MTA子项配置为处理默认的批处理大小，该大小适用于大多数情况，但在投放速度持续缓慢时需要选中该大小。
* **投放的目标**:投放性能禁止受软退件错误的影响，软退件错误将根据重试配置进行处理。错误数越多，重试的次数就越多。
* **平台总负载**:发送多个大型投放时，整体平台可能会受到影响。您还可以检查IP信誉和可投放性问题。 有关更多信息，请参阅[此部分](../../delivery/using/about-deliverability.md)和[Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans)。

平台和数据库维护也会影响投放发送性能。 有关详细信息，请参见[此页面](../../production/using/database-performances.md)。
