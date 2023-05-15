---
product: campaign
title: 更新聚合
description: 了解有关更新聚合工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# 更新聚合{#update-aggregate}



聚合在多维数据集级别定义，用于报告。 A **[!UICONTROL Workflow]** 选项卡。

处理大量数据时，聚合非常有用。 系统会根据专用工作流框中定义的设置自动更新这些参数，以便将最近收集的数据集成到指标中

聚合在每个多维数据集的相关选项卡中定义。

![](assets/s_advuser_cube_agregate_01.png)


的 **[!UICONTROL Update aggregate]** 活动允许您选择要应用的更新模式：完整或部分。

默认情况下，会在每次计算期间执行完整更新。 要启用部分更新，请选择相关选项并定义更新条件。

![](assets/s_advuser_cube_agregate_05.png)

**良好做法**:a **[!UICONTROL Scheduler]** 活动可用于指定计算更新的频率。

![](assets/s_advuser_cube_agregate_04.png)
