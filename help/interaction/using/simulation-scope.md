---
product: campaign
title: 模拟范围
description: 模拟范围
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 5%

---

# 模拟范围{#simulation-scope}



## 范围的定义 {#definition-of-the-scope}

打开 **[!UICONTROL Scope]** 选项卡选择您的设置。

以下项目为必填项：

* 环境或优惠类别。
* 优惠空间.
* 联系日期. 在联系日期不符合条件的优惠不会考虑在内。
* 目标人群.

   如果您没有在目标上配置过滤器，则将考虑整个收件人表。

* 每个目标要模拟的建议数。

   收件人将收到这么多建议。 例如，如果输入5，则每个收件人将收到最多5个优惠建议。

   ![](assets/offer_simulation_009.png)

要优化要考虑进行模拟的优惠，您可以添加一个或多个主题（在类别中预先指定）。

您还可以选择对所有选件或仅在线选件执行模拟。 某些筛选器允许您根据需要更改选择。

>[!NOTE]
>
>必须指定联系日期。 这使交互引擎可以对所选环境或类别中的优惠进行排序。 如果未配置日期，则模拟将引发错误。

## 添加报告轴 {#adding-reporting-axes}

通过在目标上添加报告轴或选件本身，可以增强模拟分析。 **[!UICONTROL Calculations]** 选项卡。

要执行此操作，请单击 **[!UICONTROL Add]** 按钮并选择相应的字段。 轴将用于计算模拟，并显示在分析报告中。 有关更多信息，请参阅 [模拟跟踪](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)
