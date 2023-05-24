---
product: campaign
title: 投放报告
description: 投放报告
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: 74feb13f-0994-4a6a-ae4f-2538b07cc9c0
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 7%

---

# 投放报告 {#delivery-reports}



您可以通过可从投放概述访问的各种报告来跟踪投放的执行情况。 要显示报告，请按照以下步骤操作：

1. 转到 **[!UICONTROL Campaigns]** 选项卡，然后单击 **[!UICONTROL Delivery]** 用于显示投放列表的链接。
1. 单击要显示的投放名称以显示其详细信息。

   ![](assets/s_ncs_user_detailled_report.png)

1. 选择 **[!UICONTROL Summary]** 选项卡，然后单击 **[!UICONTROL Reports]** 用于访问特定于投放的报告的链接。

   ![](assets/s_ncs_user_detailled_report2.png)

   默认情况下，可以使用以下报表：

   * **[!UICONTROL Delivery throughput]** ：请参阅 [投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput).
   * **[!UICONTROL Sharing to social networks]** ：请参阅 [分享到社交网络](../../reporting/using/global-reports.md#sharing-to-social-networks).
   * **[!UICONTROL Statistics on sharing activities]** ：请参阅 [共享活动的统计数据](../../reporting/using/global-reports.md#statistics-on-sharing-activities).
   * **[!UICONTROL Hot clicks]** ：请参阅 [热门点击](#hot-clicks).
   * **[!UICONTROL Tracking statistics]** ：请参阅 [跟踪统计数据](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** ：请参阅 [URL和点击流](#urls-and-click-streams).
   * **[!UICONTROL Tracking indicators]** ：请参阅 [跟踪指标](#tracking-indicators).
   * **[!UICONTROL Non-deliverables and bounces]** ：请参阅 [无法投放项和退回](../../reporting/using/global-reports.md#non-deliverables-and-bounces).
   * **[!UICONTROL User activities]** ：请参阅 [用户活动](../../reporting/using/global-reports.md#user-activities).
   * **[!UICONTROL Delivery summary]** ：请参阅 [投放摘要](#delivery-summary).
   * **[!UICONTROL Subscription tracking]** ：请参阅 [订阅跟踪](../../reporting/using/global-reports.md#subscription-tracking).
   * **[!UICONTROL Delivery statistics]** ：请参阅 [投放统计数据](../../reporting/using/global-reports.md#delivery-statistics).
   * **[!UICONTROL Breakdown of opens]** ：请参阅 [打开的细分](../../reporting/using/global-reports.md#breakdown-of-opens).

## 跟踪指标 {#tracking-indicators}

此报表将用于在接收投放时跟踪收件人行为的关键指标组合在一起。 它提供了对投放和接收统计数据、打开率和点进率、生成的点击流、Web 跟踪以及与社交网络共享的活动的访问权限。

>[!NOTE]
>
>根据消息打开次数计算的值始终是估计值，这是因为以文本格式链接到电子邮件的错误边距。 此 **[!UICONTROL Distinct opens/Sum of opens for the population reached]** 指示器会将此误差范围考虑在内。 有关跟踪打开的详细信息，请参阅 [跟踪打开次数](../../reporting/using/indicator-calculation.md#tracking-opens-).

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** ：投放分析后要投放的消息总数。
* **[!UICONTROL Success]** : 成功处理的消息数.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>相关百分比是根据成功转发的邮件数计算的。

* **[!UICONTROL Distinct opens for the population reached]** ：估计至少已打开消息一次的目标收件人的数量。 由于必须打开电子邮件才能点击链接，因此会考虑对跟踪URL的点击量。
* **[!UICONTROL Sum of opens for the population reached]** ：目标收件人打开总数的估计。
* **[!UICONTROL Clicks on opt-out link]** ：取消订阅链接的点击次数。
* **[!UICONTROL Clicks on the mirror page link]** ：单击指向镜像页面的链接的次数。 为了便于考虑，必须在投放向导（跟踪的URL）中定义链接。 请参阅此 [页面](../../delivery/using/about-delivery-monitoring.md).
* **[!UICONTROL Estimation of forwards]** ：目标收件人转发的电子邮件数量的估计。 此值计算方式为减去不同联系人数和单击了电子邮件的不同收件人数量。

   >[!NOTE]
   >
   >有关不同用户与目标收件人之间差异的更多信息，请参阅 [目标人员/收件人](../../reporting/using/indicator-calculation.md#targeted-persons---recipients).

**[!UICONTROL 3. Open and click-through rate]**

此值表显示每个Internet域的投放、打开次数、点击次数和原始反应性的细分。 使用以下指标：

* **[!UICONTROL Sent]** ：在此域上发送的消息总数。
* **[!UICONTROL Complaints]** ：此域被收件人报告为不受欢迎的消息数。 费率是根据此域上发送的消息总数来计算的。
* **[!UICONTROL Opens]** ：此域中至少打开过一次邮件的不同定向收件人的数量。 费率是根据此域上发送的消息总数来计算的。
* **[!UICONTROL Clicks]** ：在同一个投放中至少点击一次的不同目标收件人的数量。 费率是根据此域上发送的消息总数计算的
* **[!UICONTROL Raw reactivity]** ：与至少打开一次投放的收件人人数相比，至少点击一次投放的收件人人数的百分比。

>[!NOTE]
>
>此报告中显示的域名在多维数据集级别使用的明细列表中定义。 要更改、添加或删除默认域，请编辑 **[!UICONTROL Domains]** 逐项列出并修改值和别名。 如需详细信息，请参阅[此部分](../../platform/using/managing-enumerations.md)。此 **[!UICONTROL Others]** 类别包括不属于明细列表任何值的域名。

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>相关百分比是根据成功转发的邮件数计算的。

* **[!UICONTROL Distinct clicks for the population reached]** ：在投放中至少单击一次的不同人数。
* **[!UICONTROL Cumulated clicks]** ：目标收件人的总点击次数，不包括退订链接和镜像页面。
* **[!UICONTROL Recipient clicks]** ：在同一个投放中至少点击一次的不同目标收件人的数量。
* **[!UICONTROL Estimated recipient reactivity]** ：投放中点击至少一次的收件人数量与至少打开投放一次的预计收件人数量的比率。 对选择退出和镜像页面链接的点击次数不会考虑在内。

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** ：收到消息后访问的网页数。
* **[!UICONTROL Transactions]** ：消息接收后的购买次数。
* **[!UICONTROL Total amount]** ：消息接收后的购买总数。
* **[!UICONTROL Average transaction amount]** ：不同投放收件人进行的平均购买。
* **[!UICONTROL Articles]** ：投放收件人购买的文章数。
* **[!UICONTROL Average count of articles per transaction]** ：不同收件人每次购买的平均项目数。
* **[!UICONTROL Average amount per message]** ：每条消息生成的平均购买量。

   >[!NOTE]
   >
   >为了考虑访问的页面、交易、金额或文章，必须在匹配的网页中插入Web跟踪标记。 Webtracking配置在中介绍 [本节](../../configuration/using/about-web-tracking.md).

**[!UICONTROL 6. Sharing activities to email and social networks]**

此部分显示在每个社交网络上共享的邮件数。 有关更多信息，请参阅 [分享到社交网络](../../reporting/using/global-reports.md#sharing-to-social-networks).

## URL 和点击流 {#urls-and-click-streams}

此报表显示投放后访问的页面列表。

![](assets/s_ncs_user_url_report.png)

您可以通过选择：要显示的分数图、时间过滤器（自操作启动以来、启动后的前6小时等）来配置此报告的内容 以及数据的显示模式（按标签、按URL、按类别）。 单击 **[!UICONTROL Refresh]** 以确认您的选择。

以下比率显示在报表的上半部分：

* **[!UICONTROL Reactivity]** ：已单击投放的目标收件人数量与已打开投放的目标收件人估计数量的比率。 选择退出链接和镜像页面上的点击次数不会考虑在内。

   >[!NOTE]
   >
   >有关跟踪打开的详细信息，请参阅 [跟踪打开次数](../../reporting/using/indicator-calculation.md#tracking-opens-).

* **[!UICONTROL Distinct clicks]** ：在投放中至少单击一次的不同人员的数量（不包括退订链接和镜像页面）。 显示的速率是根据成功投放的消息数计算的。
* **[!UICONTROL Cumulated clicks]** ：目标收件人的点击总数（不包括退订链接和镜像页面）。 显示的速率是根据成功转发的消息数计算的。

**[!UICONTROL Platform average]** ：此平均速率显示在每个速率（反应性、非重复点击和累计点击）下，针对过去6个月内发送的投放进行计算。 只考虑具有相同类型和相同渠道的投放。 排除验证。

中心表提供以下信息：

* **[!UICONTROL Clicks]** ：每个链接的累计点击次数。
* **[!UICONTROL Clicks (in %)]** ：根据累计点击总数划分每个链接的点击次数。

**[!UICONTROL Breakdown of clicks in time]**

此图表显示每天累计点击量的细目。

## 投放摘要 {#delivery-summary}

此报表提供有关投放的所有主要信息。

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

此部分包含两个指标：

* **[!UICONTROL Initial population]** ：投放所定向的收件人总数。
* **[!UICONTROL Messages rejected by the rule]** ：应用分类规则时在分析期间忽略的地址数：地址缺失、隔离、阻止列表时等。 有关分类规则的更多信息，请参阅此 [页面](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

**[!UICONTROL Causes of exclusion]**

中间图表显示分析期间拒绝的消息按规则细分。

**[!UICONTROL Delivery statistics]**

本节包括以下指标：

* **[!UICONTROL Messages to be delivered]** ：投放分析后要投放的消息总数。
* **[!UICONTROL Success]** ：成功处理的消息数。 关联速率是指与要投放的消息数量之比。
* **[!UICONTROL Errors]** ：投放和自动回弹处理期间累计的错误总数。 关联速率是指与要投放的消息数量之比。
* **[!UICONTROL New quarantines]** ：投放失败（用户未知，域无效）后隔离的地址数。 关联速率是指与要投放的消息数量之比。

## 热门点击 {#hot-clicks}

此报告显示邮件内容（HTML 和/或文本）以及每个链接的点击百分比。个性化块退订链接、镜像页面链接和优惠链接将计入总累计点击次数，但不会显示在报告中。

>[!NOTE]
>
>如果您的投放包含选件（交互），则报表上方的部分中将出现一个框，显示对选件的点击百分比。

![](assets/s_ncs_user_clic_report.png)

## 跟踪统计信息 {#tracking-statistics}

此报表提供有关打开、点击和交易的统计数据。

![](assets/s_ncs_user_stat_report.png)

通过它，您可以跟踪投放对营销的影响。 您可以通过更改时间刻度（1小时、3小时或24小时视图等）来配置值的显示方式。 单击 **[!UICONTROL Refresh]** 以确认您的选择。

此报告提供了一个值表和一个排列图，其中显示投放达到最大效率所需的时间。 使用以下指标：

* **[!UICONTROL Opens]** ：估算达到打开消息总数百分比所需的时间。 不考虑文本格式的电子邮件。 有关跟踪打开的详细信息，请参阅 [跟踪打开次数](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** ：估算达到记录的总点击数的百分比所需的时间。 对选择退出链接和镜像页面的点击次数不会考虑在内。
* **[!UICONTROL Transactions]** ：达到邮件接收后交易总数百分比所需的时间。 为了考虑事务，必须在匹配的网页中插入事务类型Web跟踪标记。 Webtracking配置在中介绍 [本节](../../configuration/using/about-web-tracking.md).
