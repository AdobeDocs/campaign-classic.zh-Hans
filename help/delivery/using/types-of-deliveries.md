---
title: 交付类型
seo-title: 交付类型
description: 交付类型
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# 交付类型{#types-of-deliveries}

Campaign中有三种类型的交付对象：

## 单次交付 {#single-delivery}

交付 **是执行** 一次的独立交付对象。 它可以重复、重新准备，但只要它处于最终状态（取消、停止、完成），它就不能被重复使用。

可以从分发列表中或通过“分发”活动在工作流中创建 [分发](../../workflow/using/delivery.md) 。

工作流还根据您要使用的渠道类型提供特定的交付活动。 For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

## 重复交付 {#recurring-delivery}

重复 **的交付** ，使您能够在每次执行活动时创建新的交付。 这样，您就不必为重复任务创建新的交付。

例如，如果每月运行一次此类活动，则一年后最终会有12次提交。

循环提交是通过循环提交活动在工作流 [中创建的](../../workflow/using/recurring-delivery.md)。 本节介绍了使用此活动的示例：在定 [位工作流中创建循环提交](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

## 持续交付 {#continuous-delivery}

连续 **分发** ，您可以向现有分发添加新收件人，这样不必在每次执行分发时创建新分发。

如果分发中的信息（内容、名称等）发生更改，则在分发执行时创建新的分发对象。 如果未更改任何信息，则重复使用相同的传送对象，并将传送和跟踪日志添加到同一对象中。

例如，如果您每月运行一次此类活动，则一年后将有单个交付（前提是您未对交付进行任何更改）。

在工作流中通过连续交付活动创建 [连续的交付](../../workflow/using/continuous-delivery.md)。
