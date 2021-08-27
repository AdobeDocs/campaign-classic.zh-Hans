---
product: campaign
title: 模拟范围
description: 模拟范围
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 2%

---

# 模拟范围{#simulation-scope}

![](../../assets/v7-only.svg)

## 范围的定义 {#definition-of-the-scope}

打开&#x200B;**[!UICONTROL Scope]**&#x200B;选项卡以选择您的设置。

以下项目是必填项：

* 环境或选件类别。
* 提供空间。
* 联系日期。 在联系日期不符合条件的选件将不被考虑在内。
* 目标群体。

   如果您未在目标上配置过滤器，则会考虑整个收件人表。

* 每个目标要模拟的命题数。

   收件人将收到这许多建议。 例如，如果您输入5，则每个收件人最多将收到5个优惠建议。

   ![](assets/offer_simulation_009.png)

要优化要考虑模拟的选件，您可以添加一个或多个主题（预先在类别中指定）。

您还可以选择对所有选件或仅对联机选件进行模拟。 有些过滤器允许您根据需要更改您的选择。

>[!NOTE]
>
>您必须指定联系日期。 这允许交互引擎对选定环境或类别中的选件进行排序。 如果未配置任何日期，则模拟将引发错误。

## 添加报表轴 {#adding-reporting-axes}

您可以通过&#x200B;**[!UICONTROL Calculations]**&#x200B;选项卡在目标或选件本身上添加报表轴来增强模拟分析。

为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并选择相应的字段。 轴将用于计算模拟，并显示在分析报告中。 有关更多信息，请参阅[模拟跟踪](../../interaction/using/simulation-tracking.md)。

![](assets/offer_simulation_011.png)
