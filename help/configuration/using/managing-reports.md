---
product: campaign
title: 管理报告
description: 管理报告
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# 管理报告{#managing-reports}



必须重新开发基于特定于默认Adobe Campaign收件人（nm：recipient或链接架构）的架构的报告，以便考虑来自自定义表及其通过目标映射链接的表的数据(请参阅 [目标映射](../../configuration/using/target-mapping.md) 部分)。

要创建新报告，请参阅 [本节](../../reporting/using/about-reports-creation-in-campaign.md).

在某些情况下，还必须放置特定于这些表的新多维数据集。 有关多维数据集的详细信息，请参见 [本节](../../reporting/using/ac-cubes.md).

涉及以下报告：

* **[!UICONTROL Recent proposition tracking]** (recentPropositions)：实时建议跟踪。
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent)：根据用户软件划分的打开。
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities)：分析每个时间段的共享活动、打开次数和订阅。
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback)：跟踪移动应用程序上的投放指示器。
* **[!UICONTROL Offer analysis]** (offerAnalysis)：按日期和渠道进行优惠分析。
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution)：最新投放的反应率。
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution)：每个移动应用程序的活动订阅细分。
