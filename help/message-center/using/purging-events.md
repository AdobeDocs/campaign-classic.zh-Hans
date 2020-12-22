---
solution: Campaign Classic
product: campaign
title: 清除事件
description: 清除事件
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 6%

---


# 清除事件{#purging-events}

您可以使用[部署向导](../../production/using/database-cleanup-workflow.md#deployment-wizard)配置数据在数据库中存储的时间。

事件清除由[数据库清除工作流](../../production/using/database-cleanup-workflow.md)自动执行。 此工作流会清除在控制实例上归档的执行实例和事件上接收和存储的事件。

根据需要使用箭头更改清除设置。

事件清除控制实例设置：

![](assets/messagecenter_delete_events_001.png)

事件清除执行实例设置：

![](assets/messagecenter_delete_events_002.png)

有关数据库清理工作流程的详细信息，请参阅[此部分](../../production/using/database-cleanup-workflow.md)。
