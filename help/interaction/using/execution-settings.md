---
product: campaign
title: 执行设置
description: 执行设置
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---

# 执行设置{#execution-settings}



创建模拟时，您可以根据需要指定执行设置。 这些设置允许您在活动较少期间根据其优先级执行模拟，或者在日志中记录SQL查询。 此阶段是可选的。

这些设置稍后可以在 **[!UICONTROL General]** “模拟”窗口的“标签”。

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** ：可让您根据所选的优先级（低、平均或高）计划模拟，以优化Adobe Campaign性能。
* **[!UICONTROL Priority]** ：这是应用于模拟以安排它的级别。 当 **[!UICONTROL Schedule execution for a time of low activity]** 选中选项后，促销活动处理工作流会选择一个活动较少的时间来启动促销活动。
* **[!UICONTROL Log SQL queries in the journal]** ：此功能仅供专家用户使用。 它允许您向显示SQL查询的日志中添加一个选项卡，以便在模拟完成时出现错误时检测可能的故障。
