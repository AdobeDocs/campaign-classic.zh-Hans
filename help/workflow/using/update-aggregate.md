---
product: campaign
title: 更新聚合
description: 了解有关更新聚合工作流活动的更多信息
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 4%

---

# 更新聚合{#update-aggregate}

![](../../assets/v7-only.svg)

聚合在多维数据集级别定义，用于报告。 A **[!UICONTROL Workflow]** 选项卡。

有关Adobe Campaign中多维数据集和使用聚合的更多信息，请参阅 [部分](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

的 **[!UICONTROL Update aggregate]** 活动允许您选择要应用的更新模式：完整或部分。

默认情况下，会在每次计算期间执行完整更新。 要启用部分更新，请选择相关选项并定义更新条件。

![](assets/s_advuser_cube_agregate_05.png)

**良好做法**:a **[!UICONTROL Scheduler]** 活动可用于指定计算更新的频率。

![](assets/s_advuser_cube_agregate_04.png)
