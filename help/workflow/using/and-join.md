---
solution: Campaign Classic
product: campaign
title: AND-连接
description: AND-连接
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 3eecc16442a11849c12819cf83392f60c5b82a13
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 5%

---


# AND-连接{#and-join}

仅当激活所有入站过渡(即完成所有先前活动)时，连接才会触发其出站过渡。 这样，您就可以确保在继续执行工作流之前，某些活动已完成。

例如，您可以在内容创建和投放发送自动化的上下文中使用AND-join活动，以确保只有在目标查询和内容更新步骤完成后才启动投放。 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供专用用例

![](assets/and-join-usage.png)

>[!NOTE]
>
>请注意，配置了不同过渡的入站定位维度不能使用&#x200B;**[!UICONTROL AND-join]**&#x200B;活动连接在一起。

通过在活动的入站过渡中选择主集来确定活动的出站发送人口。

出站过渡只能包含一个入站过渡群。 如果未配置活动，则出站过渡将随机选择一个入站群体。

>[!CAUTION]
>
>对于&#x200B;**AND-join**&#x200B;类型活动，将合并事件变量，但如果同一变量定义两次，则存在冲突，且值仍未确定。 如需详细信息，请参阅[此部分](../../workflow/using/javascript-scripts-and-templates.md#event-variables)。
