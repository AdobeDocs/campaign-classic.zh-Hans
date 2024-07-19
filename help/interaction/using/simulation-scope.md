---
product: campaign
title: 模拟范围
description: 模拟范围
feature: Interaction, Offers
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 2%

---

# 模拟范围{#simulation-scope}



## 范围的定义 {#definition-of-the-scope}

打开&#x200B;**[!UICONTROL Scope]**&#x200B;选项卡以选择您的设置。

以下项目为必备项：

* 环境或选件类别。
* 优惠空间。
* 联系日期。 在联系日期不符合条件的优惠不会考虑在内。
* 目标人群。

  如果您没有在目标上配置过滤器，则将考虑整个收件人表。

* 每个目标要模拟的建议数。

  收件人将收到这么多建议。 例如，如果您输入5，则每个收件人将收到最多5个优惠建议。

  ![](assets/offer_simulation_009.png)

要优化模拟要考虑的优惠，您可以添加一个或多个主题（在类别中预先指定）。

您还可以选择对所有选件或仅在线选件进行模拟。 某些筛选器允许您根据需要更改选择。

>[!NOTE]
>
>必须指定联系日期。 这使交互引擎可以对所选环境或类别中的优惠进行排序。 如果未配置日期，则模拟将引发错误。

## 添加报告轴 {#adding-reporting-axes}

您可以通过&#x200B;**[!UICONTROL Calculations]**&#x200B;选项卡在目标上添加报告轴或选件本身来增强模拟分析。

为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并选择相应的字段。 轴将用于计算模拟，并显示在分析报告中。 有关详细信息，请参阅[模拟跟踪](../../interaction/using/simulation-tracking.md)。

![](assets/offer_simulation_011.png)
