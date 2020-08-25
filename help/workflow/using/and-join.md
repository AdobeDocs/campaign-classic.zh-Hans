---
title: AND-连接
seo-title: AND-连接
description: AND-连接
seo-description: null
page-status-flag: never-activated
uuid: 8234d6cd-0e9b-4187-9ddf-9e1f86aa1b9a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 075206aa-ff7b-4fa8-a05d-14a29fb119ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 5%

---


# AND-连接{#and-join}

仅当激活所有入站过渡(即完成所有先前活动)时，连接才会触发其出站过渡。 这样，您就可以确保在继续执行工作流之前，某些活动已完成。

例如，您可以在内容创建和投放发送自动化的上下文中使用AND-join活动，以确保只有在目标查询和内容更新步骤完成后才启动投放。 本节提供专用 [用例](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

通过在活动的入站过渡中选择主集合来确定活动的出站发送群体。

出站过渡只能包含一个入站过渡群。 如果未配置活动，则出站过渡将随机选择一个入站群。

>[!CAUTION]
>
>对于AND-join **类型活动** ,事件变量会合并，但如果同一变量定义了两次，则存在冲突，且值仍未确定。 有关详细信息，请参见 [](../../workflow/using/javascript-scripts-and-templates.md#event-variables)。
