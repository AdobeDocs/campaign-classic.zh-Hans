---
solution: Campaign Classic
product: campaign
title: 传递性能最佳实践
description: 进一步了解投放性能和最佳实践。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 5%

---


# 传递性能最佳实践 {#delivery-performances}

我们建议遵循以下准则，以确保您的投放运行良好，并在您遇到投放问题时检查性能。

**相关主题：**

* [传递仪表板](../../delivery/using/delivery-dashboard.md)
* [传递疑难解答](../../delivery/using/delivery-troubleshooting.md)
* [关于投放能力](../../delivery/using/about-deliverability.md)

## 性能{#best-practices-performance}的最佳实践

* 请勿在实例上将投放保留为失败状态，因为这会保留临时表并影响性能。

* 删除不再需要的投放。

* 过去12个月中将从数据库中删除的非活动收件人以保持地址质量。

* 切勿尝试将大投放计划在一起。 在系统上均匀分布负载需要5-10分钟的时间。 与团队其他成员协调投放的安排以确保最佳性能。 当营销服务器同时处理许多不同的任务时，会降低性能。

* 尽可能小地保持电子邮件的大小。 建议的最大电子邮件大小约为35KB。 电子邮件投放的大小会在发送服务器中生成一定数量的卷。

* 大型投放(如对超过100万个收件人的投放)需要在发送队列中有空间。 仅此一项对服务器来说不是问题，但是，当与数十个其他大型投放同时出现时，它会引入发送延迟。

* 电子邮件中的个性化会将每个收件人的数据从数据库中提取出来。 如果存在许多个性化元素，则会增加准备投放所需的数据量。

* 索引地址。 要优化应用程序中使用的SQL查询的性能，可以从数据模式的主元素中声明索引。

>[!NOTE]
>
>ISP会在一段时间不活动后停用地址。 退回的邮件将发送给发送方，以通知他们此新状态。

## 性能问题清单{#performance-issues}

如果投放性能不佳，您可以检查：

* **投放的大小**:大型投放可能需要更长时间才能完成。MTA子项配置为处理默认的批处理大小，该大小适用于大多数实例，但在投放速度持续较慢时，需要检查。
* **投放的目标**:投放性能禁止受软跳出错误影响，这些错误根据重试配置进行处理。错误数越多，需要的重试就越多。
* **平台总负载**:发送多个大型投放时，整个平台可能会受到影响。您还可以检查IP信誉和可交付性问题。 有关详细信息，请参阅[本节](../../delivery/using/about-deliverability.md)和[Adobe交付能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)。

平台和投放库维护也会影响数据发送性能。 有关详细信息，请参见[此页面](../../production/using/database-performances.md)。
