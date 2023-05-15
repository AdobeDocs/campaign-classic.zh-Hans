---
product: campaign
title: 子工作流
description: 进一步了解子工作流活动
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 子工作流{#sub-workflow}



的 **[!UICONTROL Sub-workflow]** 活动允许您触发另一个工作流的执行并恢复结果。 此活动可让您在使用简化界面时使用复杂的工作流。

您可以在一个工作流中调用多个子工作流。 子工作流同步执行。

在以下示例中，主工作流使用跳转调用子工作流。 有关跳转类型图形对象的更多信息，请参阅 [此部分](jump--start-point-and-end-point-.md).

1. 创建一个工作流，以将其用作另一个工作流中的子工作流。
1. 插入 **[!UICONTROL Jump (end point)]** 活动，其优先级为1。 如果您有多个“端点”类型跳转，则Adobe Campaign将使用数字最少的“端点”跳转。
1. 插入 **[!UICONTROL Jump (start point)]** 活动，其优先级为2。 如果您有多个“起始点”类型跳转，则Adobe Campaign将使用数字最大的“起始点”跳转。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流活动引用具有多个 **[!UICONTROL Jump]** 活动时，子工作流会在数量最低的“结束点”类型跳转和数量最高的“开始点”类型跳转之间执行。
   >
   >要正确运行子工作流，您只能有一个数字最低的“端点”类型跳转，而只有一个数字最高的“起始点”类型跳转。

1. 完成并保存此“子工作流”。
1. 创建主工作流。
1. 插入 **[!UICONTROL Sub-workflow]** 活动并将其打开。
1. 从 **[!UICONTROL Workflow template]** 下拉列表。

   ![](assets/subworkflow_selection.png)

1. 您还可以添加配置脚本以更改引用的工作流。
1. 单击 **[!UICONTROL Ok]**。它将自动创建标签为 **[!UICONTROL Jump (start point)]** 活动。

   ![](assets/subworkflow_outbound.png)

1. 运行工作流。

运行后，称为子工作流的工作流将保留在 **[!UICONTROL Being edited]** 状态，这表示：

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

这组值由三个值组成，用于标识查询所定向的群体。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体模式（通常为nms:recipient）和 **[!UICONTROL recCount]** 是表中的元素数。

* targetSchema:此值是工作表的架构。 此参数适用于具有 **[!UICONTROL tableName]** 和 **[!UICONTROL schema]**.
