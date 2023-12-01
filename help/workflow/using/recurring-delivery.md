---
product: campaign
title: 循环投放
description: 了解有关定期投放工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: cfc38df8184a8f59d49ce27eb7875783e8941611
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 12%

---

# 循环投放{#recurring-delivery}

A **[!UICONTROL Recurring delivery]** 利用活动，可配置特定于营销活动的投放模板发生次数。

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#recurring-delivery-video)

此活动只能从 **[!UICONTROL Targeting and workflows]** 在营销活动中找到的选项卡。

操作步骤：

1. 选择活动将基于的投放模板。

   ![](assets/recurring_delivery_001.png)

1. 配置投放模板。

此活动的配置过程与根据可用选项创建投放模板的过程类似。 有关更多信息，请参阅此](../../delivery/using/about-templates.md)章节[。

>[!CAUTION]
>
>定期投放不支持预览内容或发送校样，包括 [目标数据](../../workflow/using/data-life-cycle.md#target-data) 个性化元素。

有关正在使用的此活动的示例，请参阅此 [部分](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## 如何设置循环投放 {#set-up-recurring-delivery}

A **循环投放** 每次执行时都会创建一个新的投放实例。 例如，如果工作流计划每周运行一次，那么一年后将产生52次投放。 这也意味着广义日志和跟踪日志将按每个投放实例进行分隔。

![循环投放](assets/delivery_recurring.jpg)

如果要停止运行定期投放，则应完全取消活动或停止执行活动的工作流。 从Campaign仪表板停止投放只会停止投放发生：每次执行工作流时，将继续创建定期投放的下一个实例。

>[!NOTE]
>
>无法发送来自 **[!UICONTROL Recurring delivery]** 键入activity。
> 
>要通过活动工作流直接创建投放，请使用预配置的渠道特定活动(例如， **[!UICONTROL Recurring delivery]**)。

## 教程视频 {#recurring-delivery-video}

此视频介绍如何配置循环投放和调度程序活动。

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
