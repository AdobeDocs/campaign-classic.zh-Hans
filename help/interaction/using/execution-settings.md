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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 执行设置{#execution-settings}

创建模拟时，您可以根据需要指定执行设置。 这些设置允许您根据活动的优先级在活动较少的时间执行模拟，或在日志中记录SQL查询。 此阶段是可选的。

这些设置稍后可在模拟窗口的 **[!UICONTROL General]** 选项卡中进行更改。

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** :允许您根据所选的优先级（低、平均或高）计划模拟，以优化Adobe Campaign的性能。
* **[!UICONTROL Priority]** :这是模拟所应用的级别，用于计划它。 选中该 **[!UICONTROL Schedule execution for a time of low activity]** 选项后，营销活动处理工作流将选择活动时间较短的时间来启动营销活动。
* **[!UICONTROL Log SQL queries in the journal]** :此功能仅适用于专家用户。 它允许您向显示SQL查询的日志添加一个选项卡，以检测在模拟完成时出错的可能故障。

