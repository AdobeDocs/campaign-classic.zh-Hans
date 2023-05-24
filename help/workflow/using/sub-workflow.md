---
product: campaign
title: 子工作流
description: 了解有关子工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 子工作流{#sub-workflow}



此 **[!UICONTROL Sub-workflow]** 利用活动，可触发另一个工作流的执行并恢复结果。 通过此活动，您可以在使用简化界面的同时使用复杂的工作流。

您可以在单个工作流中调用多个子工作流。 子工作流会同步执行。

在以下示例中，主工作流使用跳转调用子工作流。 有关跳转类型图形对象的详细信息，请参见 [本节](jump--start-point-and-end-point-.md).

1. 创建将用作另一个工作流中的子工作流的工作流。
1. 插入 **[!UICONTROL Jump (end point)]** 工作流开头优先级为1的活动。 如果您有多个“端点”类型跳转，Adobe Campaign将使用数字最小的“端点”跳转。
1. 插入 **[!UICONTROL Jump (start point)]** 工作流末尾优先级为2的活动。 如果您有多个“起点”类型跳转，Adobe Campaign将使用具有最高数字的“起点”跳转。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流活动引用了一个具有多个 **[!UICONTROL Jump]** 活动，子工作流在编号最低的“端点”类型跳转和编号最高的“起点”类型跳转之间执行。
   >
   >要使子工作流正确运行，必须只有一个编号最低的“终点”类型跳转，以及只能有一个编号最高的“起点”类型跳转。

1. 完成并保存此“子工作流”。
1. 创建主工作流。
1. 插入 **[!UICONTROL Sub-workflow]** 活动并打开它。
1. 从中选择要使用的工作流 **[!UICONTROL Workflow template]** 下拉列表。

   ![](assets/subworkflow_selection.png)

1. 您还可以添加配置脚本以更改引用的工作流。
1. 单击 **[!UICONTROL Ok]**。它会自动创建一个叫客过渡，其标签为 **[!UICONTROL Jump (start point)]** 活动。

   ![](assets/subworkflow_outbound.png)

1. 运行工作流。

运行后，作为子工作流调用的工作流将保留在 **[!UICONTROL Being edited]** 状态，表示以下内容：

* 无法右键单击过渡以显示目标。
* 无法显示中间群体的计数。
* 子工作流日志显示在主工作流中。

   ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>如果子工作流中出现任何错误，主工作流将暂停，并创建子工作流的副本。

## 输入参数（可选） {#input-parameters--optional-}

* 表名
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识查询所针对的群体。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms：recipient）和 **[!UICONTROL recCount]** 是表中的元素数。

* targetSchema：此值是工作表的架构。 此参数对于具有的所有过渡都有效 **[!UICONTROL tableName]** 和 **[!UICONTROL schema]**.
