---
solution: Campaign Classic
product: campaign
title: AND-连接
description: AND-连接
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 6%

---


# AND-连接{#and-join}

仅当激活所有入站过渡(即完成所有先前活动)时，连接才会触发其出站过渡。 这样，您就可以确保在继续执行工作流之前，某些活动已完成。

例如，您可以在内容创建和投放发送自动化的上下文中使用AND-join活动，以确保只有在目标查询和内容更新步骤完成后才启动投放。 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供专用用例

![](assets/and-join-usage.png)

通过在活动的入站过渡中选择主集合来确定活动的出站发送群体。

出站过渡只能包含一个入站过渡群。 如果未配置活动，则出站过渡将随机选择一个入站群。

>[!CAUTION]
>
>对于&#x200B;**AND-join**&#x200B;类型活动,事件变量将合并，但如果同一变量定义两次，则存在冲突，且值仍未确定。 如需详细信息，请参阅[此部分](../../workflow/using/javascript-scripts-and-templates.md#event-variables)。
