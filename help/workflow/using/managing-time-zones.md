---
title: 管理时区
seo-title: 管理时区
description: 管理时区
seo-description: null
page-status-flag: never-activated
uuid: a253861a-fc15-406d-969d-33cfb4169839
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 8bcbcd23-9251-412a-ae72-11f15db74112
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 4%

---


# 管理时区{#managing-time-zones}

Adobe Campaign允许您管理同一实例所涉及的不同国家之间的时差。 在实例创建过程中配置所应用的配置。

有关在Adobe Campaign中配置时区的详细信息，请参阅此 [部分](../../installation/using/time-zone-management.md)。

在工作流中，您可以调整活动执行计划，并将特定时区链接到活动或整个工作流。 此配置在导入文件时或在投放计划框架中非常有用。

## 执行计划 {#execution-scheduling}

您可以使用计划调度程序执行任务(请参阅 [调度程序](../../workflow/using/scheduler.md))。 您还可以在优惠此功能的活动中使用可用的计划选项。 这些活动优惠 **[!UICONTROL Schedule]** 标签： **[!UICONTROL File collector]**、 **[!UICONTROL File transfer]**、 **[!UICONTROL Web download]****[!UICONTROL Email reception]** 和 **[!UICONTROL SMS]**&#x200B;等。

对于所有计划任务(即具有计划选项的所有活动)，您可以选择要应用的时区。 通过相关活动的选 **[!UICONTROL Advanced]** 项卡选择时区：

![](assets/wf-timezone-in-a-box.png)

可能的值有：

* 服务器时区

   使用Adobe Campaign应用程序服务器的时区。

* 用户时区

   使用执行工作流的Adobe Campaign运算符的时区。

* 数据库时区

   使用所使用的数据库服务器的时区。

* 特定时区

   使用所选时区。

如果选 **[!UICONTROL By default]** 择该值，则应用工作流的时区，或应用服务器的时区。

## 将时区链接到活动 {#linking-a-time-zone-to-an-activity}

使用 **[!UICONTROL Advanced]** 工作流活动的选项卡可以选择其时区。 尽管大多数时间，工作流的时区已足够，但是对于特定活动（如数据导入），可能需要时不时地过载，以便将日期链接到其正确的时区。
