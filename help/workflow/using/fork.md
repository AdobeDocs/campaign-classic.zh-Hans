---
product: campaign
title: 分叉
description: 进一步了解分支工作流活动
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---

# 分叉{#fork}

**[!UICONTROL Fork]**&#x200B;活动允许您创建多个叫客过渡，以便在同一工作流中独立地执行多个活动。

例如，您可以在查询后使用活动，以同时执行两个操作：

* 将查询结果保存到受众中，
* 对结果执行分段，以发送多个投放。

您还可以在内容创建和投放发送自动化的上下文中使用活动，以便同时启动目标计算和内容创建。 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供了专用用例。

>[!IMPORTANT]
>
>在&#x200B;**[!UICONTROL Fork]**&#x200B;活动&#x200B;**之后添加的叫客过渡不会同时执行**。 此行为可能会影响工作流的性能。 如果您需要独立执行多个活动，并最终在执行其余工作流之前将它们连接在一起，则可以使用此活动。

要配置&#x200B;**[!UICONTROL Fork]**&#x200B;活动，请打开该活动以定义叫客过渡的编号和标签。

![](assets/s_user_segmentation_fork.png)

然后，您可以配置每个叫客过渡，并根据需要使用[AND-join](../../workflow/using/and-join.md)活动将它们连接在一起。 这样，只有在&#x200B;**[!UICONTROL Fork]**&#x200B;活动的叫客过渡完成后，才会执行工作流的其余部分。
