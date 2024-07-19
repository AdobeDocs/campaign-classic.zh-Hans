---
product: campaign
title: 执行设置
description: 执行设置
feature: Interaction, Offers
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 执行设置{#execution-settings}



创建模拟时，您可以根据需要指定执行设置。 利用这些设置，可在活动较少时执行模拟（取决于其优先级），或在日志中记录SQL查询。 此阶段是可选的。

这些设置稍后可以在模拟窗口的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中更改。

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** ：允许您根据选定的优先级（低、平均或高）计划模拟，以优化Adobe Campaign性能。
* **[!UICONTROL Priority]** ：这是应用于模拟以计划它的级别。 选中&#x200B;**[!UICONTROL Schedule execution for a time of low activity]**&#x200B;选项后，营销活动处理工作流会选择低活动时间来启动营销活动。
* **[!UICONTROL Log SQL queries in the journal]** ：此功能仅供专家用户使用。 它允许您向日志添加一个显示SQL查询的选项卡，以便在模拟完成时出现错误时检测可能的故障。
