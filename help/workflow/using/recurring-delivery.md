---
solution: Campaign Classic
product: campaign
title: 循环投放
description: 进一步了解重复投放工作流活动
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 11%

---


# 循环投放{#recurring-delivery}

**[!UICONTROL Recurring delivery]**&#x200B;活动允许您配置特定于活动的投放模板事件。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#recurring-delivery-video)

此活动仅在活动中的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中可用。

操作步骤：

1. 选择活动将基于的投放模板。

   ![](assets/recurring_delivery_001.png)

1. 配置投放模板。

此活动的配置过程与在可用选项方面创建投放模板的过程类似。 有关更多信息，请参阅此](../../delivery/using/about-templates.md)章节[。

有关此活动的示例，请参阅此[部分](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

## 如何设置循环投放

每次执行&#x200B;**循环投放**&#x200B;时，都将创建一个新投放实例。 例如，如果该工作流计划每周运行一次，则一年后将产生52个投放。 这也意味着，广义日志和跟踪日志将由每个投放实例分隔。

![循环投放](assets/delivery_recurring.jpg)

>[!NOTE]
>
>无法从&#x200B;**[!UICONTROL Recurring delivery]**&#x200B;类型验证发送活动。\
>要通过活动工作流直接创建投放，请使用预配置的渠道特定活动(例如，**[!UICONTROL Email delivery]**)。

## 教程视频(#recurring-投放-video)

此视频介绍如何配置循环投放和调度程序活动。

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

其他Campaign Classic操作视频[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)可用。

