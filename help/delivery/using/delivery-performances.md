---
solution: Campaign Classic
product: campaign
title: 投放性能最佳实践
description: 进一步了解投放性能和最佳实践。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 5b43412286762977c416665d296908a9bfc9b20a
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 2%

---


# 投放性能最佳实践{#delivery-performances}

我们建议遵循以下准则，确保您的投放表现良好，并检查您遇到投放问题时的表现。

**相关主题：**

* [投放仪表板](../../delivery/using/delivery-dashboard.md)
* [投放疑难解答](../../delivery/using/delivery-troubleshooting.md)
* [关于投放能力](../../delivery/using/about-deliverability.md)

## 性能最佳实践{#best-practices-performance}

* 请勿在实例上使投放处于失败状态，因为这会维护临时表并影响性能。

* 删除不再需要的投放。

* 过去12个月中将从数据库中删除的非活动收件人，以保持地址质量。

* 不要试着计划大投放。 有5-10分钟的时间间隔，可将负载均匀地分布在系统上。 与团队中的其他成员协调投放安排以确保最佳性能。 当营销服务器同时处理许多不同的任务时，它会降低性能。

* 尽可能减少电子邮件的大小。 建议的电子邮件最大大小约为35KB。 电子邮件投放的大小会在发送服务器中生成一定数量的卷。

* 大型投放(如100多万收件人的投放)需要在发送队列中留出空间。 单单这一点对服务器来说并不是问题，但是，如果与其他许多大型投放一起同时出现，就会引起发送延迟。

* 电子邮件中的个性化会为每个收件人从数据库中提取数据。 如果存在许多个性化元素，则会增加准备投放所需的数据量。

* 索引地址。 要优化应用程序中使用的SQL查询的性能，可以从数据模式的主元素中声明索引。

>[!NOTE]
>
>ISP会在非活动状态持续一段时间后禁用地址。 退回邮件会发送给发送方，以告知他们此新状态。

## 性能问题清单{#performance-issues}

如果投放性能不佳，您可以检查：

* **投放的大小**:大型投放可能需要更长的时间才能完成。MTA子项配置为处理默认的批大小，这适用于大多数情况，但当投放速度持续变慢时，需要检查该大小。
* **投放的目标**:投放性能禁止受软跳出错误影响，软跳出错误根据重试配置进行处理。错误数越多，需要的重试就越多。
* **整个平台负载**:当发送多个大型投放时，整个平台可能会受到影响。您还可以检查IP信誉和可交付性问题。 有关详细信息，请参阅Adobe Campaign[可交付性最佳实践指南](../../delivery/using/deliverability-key-points.md)和本页](../../delivery/using/about-deliverability.md)。[

平台和投放库维护也会影响数据发送性能。 有关详细信息，请参见[此页面](../../production/using/database-performances.md)。
