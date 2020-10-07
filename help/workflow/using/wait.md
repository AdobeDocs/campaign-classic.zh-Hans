---
title: 等待
seo-title: 等待
description: 等待
seo-description: null
page-status-flag: never-activated
uuid: 55e4f15d-8d69-45b1-b842-5ccdfdedf550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 41bcfe67-b5d6-4ee6-9f8a-6a7a208e2036
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 2%

---


# 等待{#wait}

等 **待活动** ，在时间延迟几秒到几个月后激活其过渡。 等待任务不会阻止执行其他任务;当此任务处于挂起状态时，工作流可以并行执行任务。

您可以使用编辑器输入标签和等待时间，如下例所示：

![](assets/edit_wait.png)

在字 **[!UICONTROL Duration]** 段中，值可以以您选择的单位表示：（根据运营商的区域设置）:

* 如果未指定区域设置： **s** , **m** ，分， **h** ,d, **d** , **y,** ,d,d,y。 在批准时，值会自动转换为最可读的单元。

   默认单位为日&#x200B;**(d**)。

* 但是，例如，如果区域设置设置为“Français”: **s** , **mn** ，分钟， **h,****小时，j,** j, **m** ，月 **** ,,，年。 在批准时，该值将自动转换为最可读的单元，如上面的示 **例中** ，已转 **换为1mn 30s**。

   默认单位为日&#x200B;**(d**)。

