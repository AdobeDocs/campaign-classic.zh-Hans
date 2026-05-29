---
product: campaign
title: AND-连接
description: AND-连接
feature: Workflows
hide: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
TQID: https://experienceleague.adobe.com/L6SmrK6xHkRqZI69OepbB4drLPfrX-cmvi6h6su3LYk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 195
ht-degree: 22%

---

# AND-连接{#and-join}



只有激活所有集客过渡时，即之前的所有活动都已完成时，联接才会触发其叫客过渡。 这使您可以在继续执行工作流之前确保某些活动已完成。

例如，您可以在内容创建和投放发送自动化的上下文中使用AND-join活动，以确保仅在完成目标查询和内容更新步骤后开始投放。 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供了专用用例

![](assets/and-join-usage.png)

>[!NOTE]
>
>请注意，使用不同定向维度配置的集客过渡不能使用&#x200B;**[!UICONTROL AND-join]**&#x200B;活动连接在一起。

活动的叫客已发送群体是通过在活动的集客过渡中选择主集来确定的。

叫客过渡只能包含集客过渡群体之一。 如果未配置活动，则叫客过渡将随机选择一个集客群体。

>[!CAUTION]
>
>对于&#x200B;**AND-join**&#x200B;类型的活动，将合并事件变量，但是如果同一变量定义了两次，则会发生冲突，且值仍未确定。 如需详细信息，请参阅[此小节](javascript-scripts-and-templates.md#event-variables)。
