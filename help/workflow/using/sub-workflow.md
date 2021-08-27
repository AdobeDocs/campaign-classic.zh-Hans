---
product: campaign
title: 子工作流
description: 进一步了解子工作流活动
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 子工作流{#sub-workflow}

![](../../assets/common.svg)

**[!UICONTROL Sub-workflow]**&#x200B;活动允许您触发另一个工作流的执行并恢复结果。 此活动可让您在使用简化界面时使用复杂的工作流。

您可以在一个工作流中调用多个子工作流。 子工作流同步执行。

在以下示例中，主工作流使用跳转调用子工作流。 有关跳转类型图形对象的更多信息，请参阅[此部分](jump--start-point-and-end-point-.md)。

1. 创建一个工作流，以将其用作另一个工作流中的子工作流。
1. 在工作流的开头插入优先级为1的&#x200B;**[!UICONTROL Jump (end point)]**&#x200B;活动。 如果您有多个“端点”类型跳转，则Adobe Campaign将使用数字最少的“端点”跳转。
1. 在工作流结束时插入优先级为2的&#x200B;**[!UICONTROL Jump (start point)]**&#x200B;活动。 如果您有多个“起始点”类型跳转，则Adobe Campaign将使用数字最大的“起始点”跳转。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流活动引用具有多个&#x200B;**[!UICONTROL Jump]**&#x200B;活动的工作流，则子工作流将在数字最小的“结束点”类型跳转和数字最大的“开始点”类型跳转之间执行。
   >
   >要正确运行子工作流，您只能有一个数字最低的“结束点”类型跳转，而只有一个数字最高的“开始点”类型跳转。

1. 完成并保存此“子工作流”。
1. 创建主工作流。
1. 插入&#x200B;**[!UICONTROL Sub-workflow]**&#x200B;活动并将其打开。
1. 从&#x200B;**[!UICONTROL Workflow template]**&#x200B;下拉列表中选择要使用的工作流。

   ![](assets/subworkflow_selection.png)

1. 您还可以添加配置脚本以更改引用的工作流。
1. 单击 **[!UICONTROL Ok]**。它将从选定的工作流自动创建带有&#x200B;**[!UICONTROL Jump (start point)]**&#x200B;活动标签的叫客过渡。

   ![](assets/subworkflow_outbound.png)

1. 运行工作流。

运行后，作为子工作流调用的工作流将保持&#x200B;**[!UICONTROL Being edited]**&#x200B;状态，这意味着：

* 您无法右键单击过渡以显示目标。
* 无法显示中间群体的计数。
* 子工作流日志显示在主工作流中。

   ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>如果子工作流中发生任何错误，则主工作流将暂停，并创建子工作流的副本。

## 输入参数（可选） {#input-parameters--optional-}

* tableName
* 模式

每个集客事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这组值由三个值组成，用于标识查询所定向的群体。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms:recipient）， **[!UICONTROL recCount]** 是表中元素的数量。

* targetSchema:此值是工作表的架构。 此参数适用于具有&#x200B;**[!UICONTROL tableName]**&#x200B;和&#x200B;**[!UICONTROL schema]**&#x200B;的所有过渡。
