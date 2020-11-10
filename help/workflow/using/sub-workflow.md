---
title: 子工作流
description: 进一步了解子工作流活动
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---


# 子工作流{#sub-workflow}

该活动 **[!UICONTROL Sub-workflow]** 允许您触发另一个工作流的执行并恢复结果。 此活动允许您在使用简化界面时使用复杂工作流。

您可以在一个工作流中调用多个子工作流。 子工作流同步执行。

在以下示例中，主工作流使用跳转调用子工作流。 有关跳转类型图形对象的详细信息，请参 [阅此部分](../../workflow/using/jump--start-point-and-end-point-.md)。

1. 创建一个工作流，您将该工作流用作另一个工作流中的子工作流。
1. 在工 **[!UICONTROL Jump (end point)]** 作流开始处插入优先级为1的活动。 如果您有多个“端点”类型跳转，Adobe Campaign将使用“端点”跳转的最小数。
1. 在工 **[!UICONTROL Jump (start point)]** 作流结束时插入优先级为2的活动。 如果您有多个“开始点”类型跳转，Adobe Campaign将使用数字最高的“开始点”跳转。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流活动引用了具有多个 **[!UICONTROL Jump]** 活动的工作流，则子工作流将在“结束点”类型跳转（具有最低数字）和“开始点”类型跳转（具有最高数字）之间执行。
   >
   >要正确运行子工作流，您只有一个“结束点”类型跳转（编号最小），而只有一个“开始点”类型跳转（编号最大）。

1. 完成并保存此“子工作流”。
1. 创建主工作流。
1. 插入 **[!UICONTROL Sub-workflow]** 活动并打开。
1. 从下拉列表中选择要使用 **[!UICONTROL Workflow template]** 的工作流。

   ![](assets/subworkflow_selection.png)

1. 您还可以添加配置脚本以更改引用的工作流。
1. 单击 **[!UICONTROL Ok]**。它将自动创建一个出站过渡，其标签为 **[!UICONTROL Jump (start point)]** 所选工作流中的活动。

   ![](assets/subworkflow_outbound.png)

1. 运行工作流。

运行后，作为子工作流调用的工作流将保 **[!UICONTROL Being edited]** 持状态，这意味着：

* 您无法右键单击过渡以显示目标。
* 无法显示中间群体的计数。
* 子工作流日志显示在主工作流中。

   ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>如果子工作流中发生任何错误，则主工作流将暂停并创建子工作流的副本。

## 输入参数（可选） {#input-parameters--optional-}

* tableName
* 模式

每个入站事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这三组值标识查询所针对的人群。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通常是nms:收件人 **[!UICONTROL recCount]** )，是表中元素的数量。

* targetSchema:此值是工作表的模式。 此参数对于包含和的所有过渡 **[!UICONTROL tableName]** 都有 **[!UICONTROL schema]**&#x200B;效。
