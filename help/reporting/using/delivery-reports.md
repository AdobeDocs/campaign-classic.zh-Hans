---
title: 交付报告
seo-title: 交付报告
description: 交付报告
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b74ea9a6b079bbe88ed17a79e532bd8ce6ce13ae

---


# 交付报告 {#delivery-reports}

您可以通过从交付概述访问的各种报表跟踪交付的执行情况。 要显示报告，请应用以下过程：

1. 转到范围 **[!UICONTROL Campaigns]** 并单击链接以 **[!UICONTROL Delivery]** 显示提交的列表。
1. 单击要显示的交付的名称以显示其详细信息。

   ![](assets/s_ncs_user_detailled_report.png)

1. 选择选 **[!UICONTROL Summary]** 项卡并单击链 **[!UICONTROL Reports]** 接以访问特定于分发的报告。

   ![](assets/s_ncs_user_detailled_report2.png)

   默认情况下，以下报告可用：

   * **[!UICONTROL Delivery throughput]** :请参阅交 [付吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。
   * **[!UICONTROL Sharing to social networks]** :请参阅 [共享到社交网络](../../reporting/using/global-reports.md#sharing-to-social-networks)。
   * **[!UICONTROL Statistics on sharing activities]** :请参阅有 [关共享活动的统计信息](../../reporting/using/global-reports.md#statistics-on-sharing-activities)。
   * **[!UICONTROL Hot clicks]** :请参阅热 [点单击](#hot-clicks)。
   * **[!UICONTROL Tracking statistics]** :请参阅跟 [踪统计信息](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** :引用URL [并单击流](#urls-and-click-streams)。
   * **[!UICONTROL Tracking indicators]** :请参阅跟 [踪指示器](#tracking-indicators)。
   * **[!UICONTROL Non-deliverables and bounces]** :请参阅 [非可交付产品和弹回](../../reporting/using/global-reports.md#non-deliverables-and-bounces)。
   * **[!UICONTROL User activities]** :请参阅用 [户活动](../../reporting/using/global-reports.md#user-activities)。
   * **[!UICONTROL Delivery summary]** :请参阅 [交付摘要](#delivery-summary)。
   * **[!UICONTROL Subscription tracking]** :请参阅 [订阅跟踪](../../reporting/using/global-reports.md#subscription-tracking)。
   * **[!UICONTROL Delivery statistics]** :请参阅交 [付统计信息](../../reporting/using/global-reports.md#delivery-statistics)。
   * **[!UICONTROL Breakdown of opens]** :请参阅打 [开的细分](../../reporting/using/global-reports.md#breakdown-of-opens)。

## 跟踪指标 {#tracking-indicators}

此报告结合了用于跟踪收件人在收到分发时的行为的关键指示器。 它允许访问交付和接收统计数据、打开和点进率、生成的点击流、Web跟踪以及与社交网络共享活动。

>[!NOTE]
>
>根据消息打开次数计算的值始终是估计值，因为文本格式电子邮件链接的错误边距。 指 **[!UICONTROL Distinct opens/Sum of opens for the population reached]** 示符将此误差范围考虑在内。 有关跟踪打开的详细信息，请参阅 [跟踪打开](../../reporting/using/indicator-calculation.md#tracking-opens-)。

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** :在分发分析后要发送的消息总数。
* **[!UICONTROL Success]** :已成功处理的消息数。

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>相关百分比是根据成功转发的消息数计算的。

* **[!UICONTROL Distinct opens for the population reached]** :估计至少打开一次消息的目标接收者的数量。 取消订阅链接和镜像页面上的单击将被考虑在内。
* **[!UICONTROL Sum of opens for the population reached]** :目标收件人的打开总数估计。
* **[!UICONTROL Clicks on opt-out link]** :取消订阅链接的点击次数。
* **[!UICONTROL Clicks on the mirror page link]** :单击指向镜像页面的链接的次数。 要考虑到这一点，必须在传送向导（跟踪的URL）中将链接定义为。 Refer to this [page](../../delivery/using/monitoring-a-delivery.md).
* **[!UICONTROL Estimation of forwards]** :目标收件人转发的电子邮件数的估计。 此值通过减去不同人数和单击电子邮件的不同收件人人数来计算。

   >[!NOTE]
   >
   >有关不同人员与目标收件人之间差异的更多信息，请参阅 [目标人员／收件人](../../reporting/using/indicator-calculation.md#targeted-persons---recipients)。

**[!UICONTROL 3. Open and click-through rate]**

此表显示了每个Internet域的交付、打开、点击和原始反应性的细分。 使用以下指示符：

* **[!UICONTROL Sent]** :在此域上发送的消息总数。
* **[!UICONTROL Complaints]** :此域的消息数，收件人报告为不需要的消息数。 该速率是根据该域上发送的消息总数计算的。
* **[!UICONTROL Opens]** :此域中至少打开一次消息的不同目标收件人的数量。 该速率是根据该域上发送的消息总数计算的。
* **[!UICONTROL Clicks]** :点击同一分发中至少一次的不同目标收件人的数量。 该速率是根据该域上发送的消息总数计算的
* **[!UICONTROL Raw reactivity]** :至少点击一次分发的收件人数与至少打开一次分发的收件人数的百分比。

>[!NOTE]
>
>此报告中显示的域名在立方级别使用的项目列表中定义。 要更改、添加或删除默认域，请编辑分 **[!UICONTROL Domains]** 项列表并修改值和别名。 如需详细信息，请参阅[此部分](../../platform/using/managing-enumerations.md)。该类 **[!UICONTROL Others]** 别包括不属于项目列表任何值的域名。

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>相关百分比是根据成功转发的消息数计算的。

* **[!UICONTROL Distinct clicks for the population reached]** :已点击交付至少一次的不同人数。
* **[!UICONTROL Cumulated clicks]** :目标收件人的点击总数，不包括取消订阅链接和镜像页面。
* **[!UICONTROL Recipient clicks]** :点击同一分发中至少一次的不同目标收件人的数量。
* **[!UICONTROL Estimated recipient reactivity]** :在递送中点击至少一次的接收者数量与已打开递送至少一次的估计收件人数量的比率。 单击退出和镜像页面链接时不会考虑这些链接。

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** :接收消息后访问的网页数。
* **[!UICONTROL Transactions]** :消息接收后的购买数量。
* **[!UICONTROL Total amount]** :收到消息后的购买总量。
* **[!UICONTROL Average transaction amount]** :不同交付收件人的平均购买量。
* **[!UICONTROL Articles]** :交付收件人购买的文章数。
* **[!UICONTROL Average count of articles per transaction]** :不同收件人每次购买的平均项目数。
* **[!UICONTROL Average amount per message]** :每条消息生成的平均购买量。

   >[!NOTE]
   >
   >要考虑访问的页面、事务、金额或文章，必须在匹配的网页中插入Web跟踪标记。 本节介绍Web跟踪 [配置](../../configuration/using/about-web-tracking.md)。

**[!UICONTROL 6. Sharing activities to email and social networks]**

此部分显示每个社交网络上共享的消息数。 有关详细信息，请参阅 [共享到社交网络](../../reporting/using/global-reports.md#sharing-to-social-networks)。

## URL 和点击流 {#urls-and-click-streams}

此报告显示分发后访问的页面列表。

![](assets/s_ncs_user_url_report.png)

您可以通过选择以下选项来配置此报告的内容：要显示的得分图表、时间筛选器（自启动操作以来，在启动后的前6小时内，等等）以及数据显示模式（按标签、按URL、按类别），有关详细信息，请参阅 [本页](../../delivery/using/monitoring-a-delivery.md)。 单击 **[!UICONTROL Refresh]** 以确认您的选择。

报告的上半部分显示以下比率：

* **[!UICONTROL Reactivity]** :已点击递送的目标收件人数量与已打开递送的目标收件人的估计数量的比率。 单击退出链接时，不会考虑镜像页面上的点击。

   >[!NOTE]
   >
   >有关跟踪打开的详细信息，请参阅 [跟踪打开](../../reporting/using/indicator-calculation.md#tracking-opens-)。

* **[!UICONTROL Distinct clicks]** :在分发中至少单击一次（不包括取消订阅链接和镜像页面）的不同用户数。 根据成功传送的消息数计算显示的速率。
* **[!UICONTROL Cumulated clicks]** :目标收件人的点击总数（不包括取消订阅链接和镜像页面）。 根据成功转发的消息数计算显示的速率。

**[!UICONTROL Platform average]** :对于在过去六个月内发送的交付，将计算在每个率（反应性、不同的点击量和累积的点击量）下显示的该平均率。 仅考虑具有相同类型和相同渠道的交付。 排除校样。

中央表提供以下信息：

* **[!UICONTROL Clicks]** :每个链接的累积点击次数。
* **[!UICONTROL Clicks (in %)]** :每个链接的点击次数与累计点击总数相关的细分。

**[!UICONTROL Breakdown of clicks in time]**

此图表显示了每天累计点击量的细分。

## 投放摘要 {#delivery-summary}

此报告提供有关交付的所有主要信息。

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

本节包含两个指标：

* **[!UICONTROL Initial population]** :交付所针对的收件人总数。
* **[!UICONTROL Messages rejected by the rule]** :在应用类型学规则时在分析过程中忽略的地址数：地址缺失、隔离、黑名单等。 有关类型学规则的详细信息，请参阅本 [页](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)。

**[!UICONTROL Causes of exclusion]**

中间图表显示了在分析过程中拒绝的消息的每个规则细分。

**[!UICONTROL Delivery statistics]**

本节包括以下指示器：

* **[!UICONTROL Messages to be delivered]** :在分发分析后要发送的消息总数。
* **[!UICONTROL Success]** :成功处理的消息数。 关联速率是要传送的消息数的比率。
* **[!UICONTROL Errors]** :在提交和自动回弹处理过程中累积的错误总数。 关联速率是要传送的消息数的比率。
* **[!UICONTROL New quarantines]** :交付失败后隔离的地址数（用户未知，无效域）。 关联速率是要传送的消息数的比率。

## 热门点击 {#hot-clicks}

此报告显示消息内容（HTML和／或文本），每个链接上包含点击链接的百分比。 个性化区块取消订阅链接、镜像页面链接和选件链接在累计的总点击量中会被考虑在内，但不会显示在报告中。

>[!NOTE]
>
>如果您的交付包含选件（交互），则报表上方的部分中会显示一个框，其中显示了选件的点击率。

![](assets/s_ncs_user_clic_report.png)

## 跟踪统计数据 {#tracking-statistics}

此报告提供有关打开次数、点击次数和事务处理的统计信息。

![](assets/s_ncs_user_stat_report.png)

它可让您跟踪交付的营销影响。 您可以通过更改时间刻度（1小时、3小时或24小时视图等）来配置值的显示方式。 单击 **[!UICONTROL Refresh]** 以确认您的选择。

此报告提供值表和帕累托图，其中显示交付达到最高效率所需的时间。 使用以下指示符：

* **[!UICONTROL Opens]** :估计达到所打开消息总数的百分比所需的时间。 不考虑文本格式的电子邮件。 有关跟踪打开的详细信息，请参阅 [跟踪打开](../../reporting/using/indicator-calculation.md#tracking-opens-)。
* **[!UICONTROL Clicks]** :估计达到记录的点击总数百分比所需的时间。 单击退出链接后，将不考虑镜像页面。
* **[!UICONTROL Transactions]** :在收到消息后达到事务处理总数百分比所需的时间。 要考虑事务，必须将事务类型Web跟踪标记插入到匹配的网页中。 本节介绍Web跟踪 [配置](../../configuration/using/about-web-tracking.md)。
