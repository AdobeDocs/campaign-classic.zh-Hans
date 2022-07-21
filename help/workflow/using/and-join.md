---
product: campaign
title: AND-连接
description: AND-连接
feature: Workflows
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 5%

---

# AND-连接{#and-join}

![](../../assets/v7-only.svg)

仅当激活所有集客过渡（即，完成所有先前的活动）时，连接才会触发其叫客过渡。 这样，您就可以确保某些活动在继续执行工作流之前已完成。

例如，您可以在内容创建和投放发送自动化的上下文中使用“与”连接活动，以确保仅在完成目标查询和内容更新步骤后才启动投放。 在 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>请注意，配置了不同定向维度的集客过渡不能使用 **[!UICONTROL AND-join]** 活动。

活动的叫客已发送群体是通过在活动的集客过渡中选择一个主集来确定的。

叫客过渡只能包含一个集客过渡群体。 如果未配置活动，则叫客过渡将随机选择一个集客群体。

>[!CAUTION]
>
>对于 **AND — 连接** 类型活动时，会合并事件变量，但如果同一变量被定义两次，则会发生冲突，值仍不确定。 如需详细信息，请参阅[此部分](javascript-scripts-and-templates.md#event-variables)。
