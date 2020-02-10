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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 等待{#wait}

等待 **活动** ，在几秒到几个月之间的任意时间延迟后激活其过渡。 等待任务不会阻止执行其他任务；当此任务处于挂起状态时，该工作流可以并行执行任务。

您可以使用编辑器输入标签和等待时间，如下例所示：

![](assets/edit_wait.png)

在字 **[!UICONTROL Duration]** 段中，值可以以您选择的单位表示：（根据运营商的区域设置）:

* 如果未指定区域设置： **s,** m，分 **钟，** h **,** , **h,****** d, d数年。 在批准时，该值会自动转换为最可读单元。

   默认单位为日(**d**)。

* 但是，例如，如果区域设置设置为“Français”:s **s,** mn，分钟 **,** h **,** h, **mn,** seconds, ******** min, mS, mS, mS, mS，数年。 在批准时，该值自动转换为最可读单元，如上面的示例 **90s** 被转换 **为1mn 30s**。

   默认单位为日(**d**)。

