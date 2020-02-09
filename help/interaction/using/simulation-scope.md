---
title: 模拟范围
seo-title: 模拟范围
description: 模拟范围
seo-description: null
page-status-flag: never-activated
uuid: d3145926-0a7e-455f-9b93-55be1b2a0518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: ef658468-e20b-45d9-a714-c152e55c1c79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 模拟范围{#simulation-scope}

## 范围的定义 {#definition-of-the-scope}

打开选 **[!UICONTROL Scope]** 项卡以选择设置。

以下项目是必填项：

* 环境或选件类别。
* 提供空间。
* 联系日期。 在联系日期不符合条件的选件不会被考虑在内。
* 目标人群。

   如果未在目标上配置过滤器，则会考虑整个收件人表。

* 每个目标要模拟的命题数。

   接收方将收到这许多建议。 例如，如果输入5，则每个收件人最多将收到5个优惠建议。

   ![](assets/offer_simulation_009.png)

要调整要考虑模拟的选件，您可以添加一个或多个主题（在类别中预先指定）。

您还可以选择对所有选件或仅对联机选件进行模拟。 某些过滤器允许您根据需要更改选择。

>[!NOTE]
>
>您必须指定联系日期。 这样，交互引擎就可以对选定环境或类别中的选件进行排序。 如果未配置日期，则模拟将引发错误。

## 添加报表轴 {#adding-reporting-axes}

您可以通过在目标或选件本身上添加报告轴来增强模拟分 **[!UICONTROL Calculations]** 析。

要执行此操作，请单击按 **[!UICONTROL Add]** 钮并选择相应的字段。 轴将用于计算模拟，并显示在分析报告中。 For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)

