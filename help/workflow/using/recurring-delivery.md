---
product: campaign
title: 定期投放
description: 了解有关定期投放工作流活动的更多信息
feature: Workflows
hide: true
hidefromtoc: true
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 11%

---

# 定期投放{#recurring-delivery}

**[!UICONTROL Recurring delivery]**&#x200B;活动允许您配置特定于营销活动的投放模板发生次数。

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#recurring-delivery-video)

此活动只能通过营销策划中的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡进行。

操作步骤：

1. 选择活动将基于的投放模板。

   ![](assets/recurring_delivery_001.png)

1. 配置投放模板。

此活动的配置过程与根据可用选项创建投放模板的过程类似。 有关更多信息，请参阅此[&#128279;](../../delivery/using/about-templates.md)章节。

>[!CAUTION]
>
>定期投放不支持预览内容或发送包含[目标数据](../../workflow/using/data-life-cycle.md#target-data)个性化元素的校样。

有关正在使用的此活动的示例，请参阅此[部分](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

## 如何设置循环投放 {#set-up-recurring-delivery}

每次执行&#x200B;**循环投放**&#x200B;时，都会创建一个新的投放实例。 例如，如果工作流计划每周运行一次，那么一年后将产生52次投放。 这也意味着广义日志和跟踪日志将按每个投放实例进行分隔。

![循环投放](assets/delivery_recurring.jpg)

如果要停止运行定期投放，则应完全取消活动或停止执行活动的工作流。 从Campaign仪表板停止投放只会停止投放发生：每次执行工作流时，将继续创建定期投放的下一个实例。

>[!NOTE]
>
>无法从&#x200B;**[!UICONTROL Recurring delivery]**&#x200B;类型活动发送验证。
> 
>要通过营销活动工作流直接创建投放，请使用预配置的渠道特定活动（例如&#x200B;**[!UICONTROL Recurring delivery]**）。

## 教程视频 {#recurring-delivery-video}

此视频介绍如何配置循环投放和调度程序活动。

>[!VIDEO](https://video.tv.adobe.com/v/27510?quality=12&captions=chi_hans)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他 Campaign Classic 操作方法视频。
