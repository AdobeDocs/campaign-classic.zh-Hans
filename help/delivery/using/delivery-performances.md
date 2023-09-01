---
product: campaign
title: 投放性能最佳实践
description: 了解有关投放性能和最佳实践的更多信息
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability
role: User, Data Engineer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 6%

---

# 投放性能最佳实践 {#delivery-performances}

我们建议遵循以下准则以确保您的交付正常运行，以及在遇到交付问题时对执行进行检查。

**相关主题：**

* [投放仪表板](delivery-dashboard.md)
* [投放疑难解答](delivery-troubleshooting.md)
* [关于可投放性](about-deliverability.md)

## 性能最佳实践 {#best-practices-performance}

* 请勿将投放置于实例上的失败状态，因为这样可维护临时表并影响性能。

* 删除不再需要的投放。

* 过去12个月内不活动的收件人，将从数据库中删除以保持地址质量。

* 不要试图一起安排大型投放。 在5至10分钟的时间间隔内，载荷均匀分布在系统上。 与团队的其他成员协调投放计划以确保最佳性能。 当营销服务器同时处理许多不同的任务时，可能会降低性能。

* 使您的电子邮件尽可能的小。 建议的最大电子邮件大小约为35KB。 电子邮件投放的大小会在发送服务器中生成一定数量的卷。

* 大型投放（如投放100多万收件人）在发送队列中需要空格。 这本身对于服务器来说并不是问题，但是当与同时发送的大量其他大型投放一起发送时，可能会造成发送延迟。

* 电子邮件中的个性化可为每个收件人从数据库中提取数据。 如果存在许多个性化元素，这会增加准备投放所需的数据量。

* 索引地址。 为了优化应用程序中使用的SQL查询的性能，可以从数据架构的主元素声明索引。

>[!NOTE]
>
>ISP会在一段时间不活动后将地址停用。 退回的消息将发送给发件人，以告知他们此新状态。

## 性能问题核对清单 {#performance-issues}

如果投放性能不佳，您可以检查：

* **投放的大小**：大型投放可能需要更长的时间才能完成。 MTA子级配置为处理默认的批次大小，这适用于大多数实例，但在投放速度持续缓慢时需要检查。
* **投放目标**：软退回错误会影响投放性能，根据重试配置可处理这些错误。 错误数越多，所需的重试次数就越多。
* **整个平台负载**：发送多个大型投放时，整个平台可能会受到影响。 您还可以检查IP信誉和投放问题。 有关详细信息，请参见 [本节](about-deliverability.md) 和 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans).

平台和数据库维护也会影响投放发送性能。 有关详细信息，请参见[此页面](../../production/using/database-performances.md)。
