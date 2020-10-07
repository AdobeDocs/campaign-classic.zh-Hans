---
title: 循环投放
seo-title: 循环投放
description: 循环投放
seo-description: null
page-status-flag: never-activated
uuid: 715855df-fe29-46e8-a7ab-d534f010a26e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 185d3256-a21e-47d7-bee7-7b91762ca1e2
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 9%

---


# 循环投放{#recurring-delivery}

活动 **[!UICONTROL Recurring delivery]** 允许您配置特定于活动的投放模板事件。

此活动仅在活动中 **[!UICONTROL Targeting and workflows]** 的选项卡中可用。

操作步骤：

1. 选择投放模板将基于的活动。

   ![](assets/recurring_delivery_001.png)

1. 配置投放模板。

此活动的配置过程与根据可用选项创建投放模板的过程类似。 有关更多信息，请参阅此](../../delivery/using/about-templates.md)章节[。

有关此活动的示例，请参阅此 [部分](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

## 如何设置重复投放

循环 **投放** ，每次执行时都将创建一个新的投放实例。 例如，如果该工作流计划每周运行一次，则一年后将产生52个投放。 这也意味着宽日志和跟踪日志将由每个投放实例分隔。

![循环投放](assets/delivery_recurring.jpg)

此视频介绍如何配置重复投放和调度程序活动。

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>无法从类型验证发送 **[!UICONTROL Recurring delivery]** 活动。\
>要直接通过活动工作流创建投放，请使用预配置的渠道特定活动(例如， **[!UICONTROL Email delivery]**)。
