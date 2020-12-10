---
solution: Campaign Classic
product: campaign
title: 投放报告
description: 投放报告
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 2%

---


# 投放报告 {#delivery-reports}

您可以通过可从投放概述访问的各种报告跟踪投放的执行。 要显示报表，请应用以下过程：

1. 转到&#x200B;**[!UICONTROL Campaigns]**&#x200B;宇宙并单击&#x200B;**[!UICONTROL Delivery]**&#x200B;链接以显示投放的列表。
1. 单击要显示的投放的名称以显示其详细信息。

   ![](assets/s_ncs_user_detailled_report.png)

1. 选择&#x200B;**[!UICONTROL Summary]**&#x200B;选项卡并单击&#x200B;**[!UICONTROL Reports]**&#x200B;链接以访问特定于投放的报告。

   ![](assets/s_ncs_user_detailled_report2.png)

   默认情况下，以下报告可用：

   * **[!UICONTROL Delivery throughput]** :参考 [投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。
   * **[!UICONTROL Sharing to social networks]** :请参阅 [共享到社交网络](../../reporting/using/global-reports.md#sharing-to-social-networks)。
   * **[!UICONTROL Statistics on sharing activities]** :请参阅 [共享活动统计](../../reporting/using/global-reports.md#statistics-on-sharing-activities)。
   * **[!UICONTROL Hot clicks]** :请参阅热 [点单击](#hot-clicks)。
   * **[!UICONTROL Tracking statistics]** :请参阅跟 [踪统计信息](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** :请参阅 [URL并单击流](#urls-and-click-streams)。
   * **[!UICONTROL Tracking indicators]** :请参阅 [跟踪指示器](#tracking-indicators)。
   * **[!UICONTROL Non-deliverables and bounces]** :请参阅 [非交付件和弹回](../../reporting/using/global-reports.md#non-deliverables-and-bounces)。
   * **[!UICONTROL User activities]** :请参阅 [用户活动](../../reporting/using/global-reports.md#user-activities)。
   * **[!UICONTROL Delivery summary]** :请参阅 [投放摘要](#delivery-summary)。
   * **[!UICONTROL Subscription tracking]** :请参阅 [订阅跟踪](../../reporting/using/global-reports.md#subscription-tracking)。
   * **[!UICONTROL Delivery statistics]** :请参阅 [投放统计](../../reporting/using/global-reports.md#delivery-statistics)。
   * **[!UICONTROL Breakdown of opens]** :请参阅打 [开的细分](../../reporting/using/global-reports.md#breakdown-of-opens)。

## 跟踪指标 {#tracking-indicators}

此报告结合了在收到收件人时跟踪投放行为的关键指标。 它允许访问投放和接收统计、打开和点进率、生成的点击流、Web跟踪以及向社交网络共享活动。

>[!NOTE]
>
>根据消息打开次数计算的值始终是估计值，因为链接到文本格式电子邮件的错误边距。 **[!UICONTROL Distinct opens/Sum of opens for the population reached]**&#x200B;指示器会考虑此误差范围。 有关跟踪打开的详细信息，请参阅[跟踪打开](../../reporting/using/indicator-calculation.md#tracking-opens-)。

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** :投放分析后要传送的消息总数。
* **[!UICONTROL Success]** :已成功处理的邮件数。

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>相关百分比根据成功转发的消息数计算。

* **[!UICONTROL Distinct opens for the population reached]** :至少一次已打开消息的目标收件人数的估计。单击退订链接和镜像页面会被考虑在内。
* **[!UICONTROL Sum of opens for the population reached]** :目标收件人的打开总数估计。
* **[!UICONTROL Clicks on opt-out link]** :单击退订链接的次数。
* **[!UICONTROL Clicks on the mirror page link]** :点击指向镜像页面的链接的次数。为了考虑这些因素，必须在投放向导（跟踪的URL）中将链接定义为这样。 请参阅此[页面](../../delivery/using/about-delivery-monitoring.md)。
* **[!UICONTROL Estimation of forwards]** :目标收件人转发的电子邮件数的估计。此值通过减去单击电子邮件的不同人员数和不同收件人数来计算。

   >[!NOTE]
   >
   >有关不同人员和目标收件人之间差异的详细信息，请参阅[目标人员/收件人](../../reporting/using/indicator-calculation.md#targeted-persons---recipients)。

**[!UICONTROL 3. Open and click-through rate]**

此值表显示每个Internet域的投放、打开次数、点击次数和原始反应性的细分。 使用以下指示符：

* **[!UICONTROL Sent]** :此域上发送的消息总数。
* **[!UICONTROL Complaints]** :此域的消息数，该收件人报告为不需要的消息数。该速率根据在此域上发送的消息总数计算。
* **[!UICONTROL Opens]** :此域至少打开一次消息的不同目标收件人数。该速率根据在此域上发送的消息总数计算。
* **[!UICONTROL Clicks]** :点击同一收件人至少一次的不同目标投放数。该速率根据在此域上发送的消息总数计算
* **[!UICONTROL Raw reactivity]** :点击收件人至少一次的投放数与打开投放至少一次的收件人数的百分比。

>[!NOTE]
>
>此报告中显示的域名在多维数据集级别使用的分项列表中定义。 要更改、添加或删除默认域，请编辑&#x200B;**[!UICONTROL Domains]**&#x200B;明细列表并修改值和别名。 如需详细信息，请参阅[此部分](../../platform/using/managing-enumerations.md)。**[!UICONTROL Others]**&#x200B;类别包含不属于分项列表任何值的域名。

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>相关百分比根据成功转发的消息数计算。

* **[!UICONTROL Distinct clicks for the population reached]** :点击投放至少一次的不同人数。
* **[!UICONTROL Cumulated clicks]** :目标收件人(不包括退订链接和镜像页面)的总点击次数。
* **[!UICONTROL Recipient clicks]** :点击同一收件人至少一次的不同目标投放数。
* **[!UICONTROL Estimated recipient reactivity]** :在投放中点击至少一次的收件人数与已打开投放至少一次的收件人数的估计数之比。单击选择退出和镜像页面链接时，不会考虑这些链接。

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** :接收消息后访问的网页数。
* **[!UICONTROL Transactions]** :消息接收后的购买数。
* **[!UICONTROL Total amount]** :消息接收后的购买总量。
* **[!UICONTROL Average transaction amount]** :不同投放收件人的平均购买量。
* **[!UICONTROL Articles]** :投放收件人购买的文章数。
* **[!UICONTROL Average count of articles per transaction]** :不同收件人每次购买的平均项目数。
* **[!UICONTROL Average amount per message]** :每条消息生成的平均购买量。

   >[!NOTE]
   >
   >要考虑访问的页面、事务、金额或文章，必须将Web跟踪标记插入到匹配的网页中。 Web跟踪配置显示在[此部分](../../configuration/using/about-web-tracking.md)中。

**[!UICONTROL 6. Sharing activities to email and social networks]**

此部分显示在每个社交网络上共享的消息数。 有关详细信息，请参阅[共享到社交网络](../../reporting/using/global-reports.md#sharing-to-social-networks)。

## URL 和点击流 {#urls-and-click-streams}

此报告显示在投放后访问的页面的列表。

![](assets/s_ncs_user_url_report.png)

您可以通过选择以下项来配置此报告的内容：要显示的得分图表、时间筛选器（自启动操作以来，在启动后的前6小时内，等等） 以及数据显示模式(按标签、按URL、按类别)。 单击 **[!UICONTROL Refresh]** 以确认您的选择。

报表的上半部分显示以下比率：

* **[!UICONTROL Reactivity]** :点击投放的目标收件人数与已打开投放的估计目标收件人数之比。单击退出链接和镜像页面时不会考虑。

   >[!NOTE]
   >
   >有关跟踪打开的详细信息，请参阅[跟踪打开](../../reporting/using/indicator-calculation.md#tracking-opens-)。

* **[!UICONTROL Distinct clicks]** :在投放中点击至少一次(不包括退订链接和镜像页面)的不同人数。显示的速率根据成功传送的消息数计算。
* **[!UICONTROL Cumulated clicks]** :目标收件人(不包括退订链接和镜像页面)的点击总数。根据成功转发的消息数计算显示的速率。

**[!UICONTROL Platform average]** :此平均比率（反应性、不同点击量和累积点击量）是为过去六个月内发送的投放计算的。仅考虑具有相同类型和相同渠道的投放。 验证排除。

中心表提供以下信息：

* **[!UICONTROL Clicks]** :每个链接的累积点击次数。
* **[!UICONTROL Clicks (in %)]** :与累计点击总数相关的每个链接点击次数细分。

**[!UICONTROL Breakdown of clicks in time]**

此图表显示了每天累计点击量的细分。

## 投放摘要 {#delivery-summary}

此报告提供有关投放的所有主要信息。

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

本节包含两个指标：

* **[!UICONTROL Initial population]** :投放目标收件人总数。
* **[!UICONTROL Messages rejected by the rule]** :应用分析时在类型规则期间忽略的地址数：地址缺失、隔离阻止列表、等。有关类型规则的详细信息，请参阅此[页面](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)。

**[!UICONTROL Causes of exclusion]**

中间图表显示在分析期间拒绝的消息的每个规则细分。

**[!UICONTROL Delivery statistics]**

本节包括以下指标：

* **[!UICONTROL Messages to be delivered]** :投放分析后要传送的消息总数。
* **[!UICONTROL Success]** :已成功处理的邮件数。关联速率是要传递的消息数的比率。
* **[!UICONTROL Errors]** :在投放和自动回弹处理期间累积的错误总数。关联速率是要传递的消息数的比率。
* **[!UICONTROL New quarantines]** :失败投放后隔离的地址数(用户未知，无效域)。关联速率是要传递的消息数的比率。

## 热门点击 {#hot-clicks}

此报告显示每个链接上具有点击链接百分比的消息内容（HTML和／或文本）。 个性化块退订链接、镜像页面链接和优惠链接会计入累计的总点击量，但不会显示在报告中。

>[!NOTE]
>
>如果投放包含优惠（交互），则报表上方的部分会显示一个框，显示优惠的点击率。

![](assets/s_ncs_user_clic_report.png)

## 跟踪统计信息{#tracking-statistics}

此报告提供有关打开、点击和事务的统计信息。

![](assets/s_ncs_user_stat_report.png)

它可让您跟踪投放的营销影响。 您可以通过更改时间刻度(1小时、3小时或24小时视图等)来配置值的显示方式。 单击 **[!UICONTROL Refresh]** 以确认您的选择。

此报告提供值表和帕累托图，其中显示投放达到最高效率所需的时间。 使用以下指示符：

* **[!UICONTROL Opens]** :估计达到所打开邮件总数的百分比所需的时间。文本格式的电子邮件未予考虑。 有关跟踪打开的详细信息，请参阅[跟踪打开](../../reporting/using/indicator-calculation.md#tracking-opens-)。
* **[!UICONTROL Clicks]** :估计达到所记录点击总数的百分比所需的时间。单击退出链接后，不会考虑镜像页面。
* **[!UICONTROL Transactions]** :在收到消息后达到事务处理总数的百分比所需的时间。要考虑事务，必须将事务类型Web跟踪标记插入到匹配的网页中。 Web跟踪配置显示在[此部分](../../configuration/using/about-web-tracking.md)中。
