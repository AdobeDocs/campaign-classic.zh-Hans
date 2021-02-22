---
solution: Campaign Classic
product: campaign
title: 分叉
description: 进一步了解Fork工作流活动
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: e5f718908d0bb6893e54c51700865ecda09c80db
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---


# 分叉{#fork}

**[!UICONTROL Fork]**&#x200B;活动允许您创建多个出站过渡，以便在同一工作流中独立执行多个活动。

例如，您可以在查询后使用活动，以便并行执行两个操作：

* 将查询结果保存到受众中，
* 对结果执行分段以发送多个投放。

您还可以在内容创建和投放发送自动化的上下文中使用活动，以同时启动目标计算和内容创建。 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供了专用用例。

>[!IMPORTANT]
>
>在&#x200B;**[!UICONTROL Fork]**&#x200B;活动&#x200B;**后添加的出站过渡不会同时执行。**&#x200B;此行为会影响工作流的性能。 如果您需要独立执行多个活动，并且最终在执行其余工作流之前将它们连接在一起，请使用此活动。

要配置&#x200B;**[!UICONTROL Fork]**&#x200B;活动，请打开它以定义出站过渡的编号和标签。

![](assets/s_user_segmentation_fork.png)

然后，您可以配置每个出站过渡，然后根据需要使用[AND-join](../../workflow/using/and-join.md)活动将它们连接在一起。 这样，仅当&#x200B;**[!UICONTROL Fork]**&#x200B;活动的出站过渡完成后，工作流的其余部分才会执行。
