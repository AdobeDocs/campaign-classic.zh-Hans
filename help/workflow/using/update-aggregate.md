---
product: campaign
title: 更新聚合
description: 了解有关更新聚合工作流活动的更多信息
feature: Workflows
hide: true
hidefromtoc: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# 更新聚合{#update-aggregate}



聚合是在多维数据集级别定义的，以用于报表目的。 配置聚合时&#x200B;**[!UICONTROL Workflow]**&#x200B;选项卡可用。

在处理大量数据时，聚合很有用。 它们会根据专用工作流框中定义的设置自动更新，以将最近收集的数据集成到指标中

聚合在每个多维数据集的相关选项卡中定义。

![](assets/s_advuser_cube_agregate_01.png)


**[!UICONTROL Update aggregate]**&#x200B;活动允许您选择要应用的更新模式：全部或部分。

默认情况下，在每次计算期间都会执行完全更新。 要启用部分更新，请选择相关选项并定义更新条件。

![](assets/s_advuser_cube_agregate_05.png)

**良好做法**：可以使用&#x200B;**[!UICONTROL Scheduler]**&#x200B;活动指定计算更新的频率。

![](assets/s_advuser_cube_agregate_04.png)
