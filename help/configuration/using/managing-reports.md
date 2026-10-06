---
product: campaign
title: 管理报告
description: 管理报告
feature: Reporting, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
TQID: 'https://experienceleague.adobe.com/LA4v5oODC9n5K2Ttox9SF7lwcGQOU7IDEvL1P4Sls-4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%
---
# 管理报告{#managing-reports}



必须重新开发基于特定于默认Adobe Campaign收件人（nm:recipient或架构链接）的架构的报告，以便考虑来自自定义表及其通过目标映射链接的表的数据（请参阅[目标映射](../../configuration/using/target-mapping.md)部分）。

要创建新报告，请参阅[此章节](../../reporting/using/about-reports-creation-in-campaign.md)。

在某些情况下，还必须放置特定于这些表的新多维数据集。 [此部分](../../reporting/using/ac-cubes.md)中详细介绍了多维数据集。

涉及以下报告：

* **[!UICONTROL Recent proposition tracking]** (recentPropositions)：实时建议跟踪。
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent)：根据用户软件划分的打开。
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities)：分析每个时间段的共享活动、打开次数和订阅。
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback)：跟踪移动应用程序上的投放指示器。
* **[!UICONTROL Offer analysis]** (offerAnalysis)：按日期和渠道进行优惠分析。
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution)：最新投放的反应率。
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution)：每个移动应用程序的活动订阅细分。
