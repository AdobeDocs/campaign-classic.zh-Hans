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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 优惠引擎{#offer-engine}

通过 **[!UICONTROL Offer engine]** 此活动，您可以在交付之前定义对选件引擎的调用。

通过在交付之前使用引擎计算的优惠来丰富入站人口数据，该活动与使用引擎调用的富集活动遵循相同的原则。

![](assets/int_offerengine_activity2.png)

配置查询后(请参阅此 [部分](../../workflow/using/query.md)):

1. 添加和打开活 **[!UICONTROL Offer engine]** 动。
1. 填写各种可用字段以指定对选件引擎参数（选件空间、类别或主题、联系日期、要保留的选件数量）的调用。 引擎将根据这些参数自动计算要添加的选件。

   >[!CAUTION]
   >
   >如果您使用此活动，则仅存储交付中使用的选件建议。

   ![](assets/int_offerengine_activity1.png)

1. 然后，配置与所选渠道对应的交付活动。 请参阅 [跨渠道交付](../../workflow/using/cross-channel-deliveries.md)。

