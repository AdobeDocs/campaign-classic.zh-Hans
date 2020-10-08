---
title: 优惠引擎
seo-title: 优惠引擎
description: 优惠引擎
seo-description: null
page-status-flag: never-activated
uuid: a8f6056a-80e6-4f9f-81f5-563c98d11d28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 08987595-e80c-4197-ad1e-9aa7cfc7c3eb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 5%

---


# 优惠引擎{#offer-engine}

活动 **[!UICONTROL Offer engine]** 允许您在投放之前定义对优惠引擎的调用。

此活动与引擎调用的扩充活动工作原理相同，通过在投放之前用引擎计算的优惠来丰富入站人口数据。

![](assets/int_offerengine_activity2.png)

配置查询后(请参阅此 [部分](../../workflow/using/query.md)):

1. 添加和打开 **[!UICONTROL Offer engine]** 活动。
1. 填写各种可用字段以指定对优惠引擎参数(优惠空间、类别或主题、联系日期、要保留的优惠数)的调用。 引擎将根据这些参数自动计算要添加的优惠。

   >[!CAUTION]
   >
   >如果您使用此活动，则只存储投放中使用的优惠建议。

   ![](assets/int_offerengine_activity1.png)

1. 然后，配置与所选投放对应的活动渠道。 请参阅 [跨渠道投放](../../workflow/using/cross-channel-deliveries.md)。

