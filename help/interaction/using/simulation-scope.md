---
solution: Campaign Classic
product: campaign
title: 模拟范围
description: 模拟范围
audience: interaction
content-type: reference
topic-tags: simulating-offers
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 2%

---


# 模拟范围{#simulation-scope}

## 范围定义 {#definition-of-the-scope}

打开选 **[!UICONTROL Scope]** 项卡以选择设置。

以下项目是必填项：

* 环境或优惠类别。
* 优惠空间。
* 联系日期。 在联系日期不符合资格的优惠不会被考虑在内。
* 目标。

   如果未在目标上配置过滤器，则将考虑整个收件人表。

* 每个目标要模拟的命题数。

   收件人将接受这许多建议。 例如，如果输入5，则每个收件人最多将收到5个优惠建议。

   ![](assets/offer_simulation_009.png)

要细化要考虑优惠的模拟，您可以添加一个或多个主题(在类别中预先指定)。

您还可以选择对所有优惠或只对联机的执行模拟。 某些过滤器允许您根据需要更改选择。

>[!NOTE]
>
>必须指定联系日期。 这样交互引擎就可以对选定环境或类别中的优惠进行排序。 如果未配置日期，模拟将引发错误。

## 添加报告轴 {#adding-reporting-axes}

您可以通过在模拟上添加报告轴或通过选项卡在优惠本身上添加分析 **[!UICONTROL Calculations]** 轴来增强。

为此，请单击按 **[!UICONTROL Add]** 钮并选择相应的字段。 轴将用于计算模拟，并显示在分析报告中。 For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)

