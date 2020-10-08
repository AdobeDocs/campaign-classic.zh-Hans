---
title: 执行设置
seo-title: 执行设置
description: 执行设置
seo-description: null
page-status-flag: never-activated
uuid: a6549091-0c33-4fe1-adde-de3b285dd456
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: 52b5d5a9-10dc-4601-8fe4-962a2334322b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 5%

---


# 执行设置{#execution-settings}

创建模拟时，您可以根据需要指定执行设置。 这些设置允许您根据模拟的优先级在低活动期执行查询，或在日志中记录SQL。 此阶段是可选的。

这些设置稍后可在模拟窗 **[!UICONTROL General]** 口的选项卡中更改。

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** :允许您根据所选的优先级（低、平均或高）计划模拟，以优化Adobe Campaign性能。
* **[!UICONTROL Priority]** :这是应用于模拟以计划它的级别。 选中该 **[!UICONTROL Schedule execution for a time of low activity]** 选项后，活动处理工作流将选择活动时间较短的时间来开始活动。
* **[!UICONTROL Log SQL queries in the journal]** :此功能仅供专家用户使用。 它允许您向显示SQL查询的日志添加一个选项卡，以检测模拟在错误结束时可能出现的故障。

