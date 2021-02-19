---
solution: Campaign Classic
product: campaign
title: 更新聚合
description: 进一步了解更新聚合工作流活动
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 4%

---


# 更新聚合{#update-aggregate}

聚合在多维数据集级别定义以用于报告。 配置聚合时，**[!UICONTROL Workflow]**&#x200B;选项卡可用。

有关多维数据集和在Adobe Campaign中使用聚合的详细信息，请参阅专用的[部分](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)。

**[!UICONTROL Update aggregate]**&#x200B;活动允许您选择要应用的更新模式：完全或部分。

默认情况下，在每次计算期间都会执行完整更新。 要启用部分更新，请选择相关选项并定义更新条件。

![](assets/s_advuser_cube_agregate_05.png)

**良好做法**:可 **[!UICONTROL Scheduler]** 以使用活动指定计算更新的频率。

![](assets/s_advuser_cube_agregate_04.png)

