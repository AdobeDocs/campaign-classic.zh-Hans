---
title: 子工作流
seo-title: 子工作流
description: 子工作流
seo-description: null
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 子工作流{#sub-workflow}

通过 **[!UICONTROL Sub-workflow]** 该活动，您可以触发另一个工作流的执行并恢复结果。 通过本练习，您可以在使用简化界面的同时使用复杂的工作流。

您可以在一个工作流中调用多个子工作流。 子工作流是同步执行的。

>[!NOTE]
>
>要正确运行子工作流，您只能有一个“到达”类型跳转（编号最小），而只有一个“开始”类型跳转（编号最大）。 例如，如果“开始”类型跳转的优先级为1、2和3，则只应跳转一个“开始”类型，其优先级为3。

1. 创建一个工作流，您将该工作流用作另一个工作流中的子工作流。
1. 在工 **[!UICONTROL Jump (end point)]** 作流开始处插入优先级为1的活动。 如果您有多个“到达”类型跳转，Adobe Campaign将使用“到达”跳转，且该跳转的数量最低。

   在工 **[!UICONTROL Jump (start point)]** 作流结束时插入优先级为2的活动。 如果您有多个“开始”类型跳转，Adobe Campaign将使用最大数量的“开始”跳转。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流活动引用了具有多个活动的工作流，则子工作流将在“到达”类型跳转与“开始”类型跳转之间执行，该类型跳转与最大数量的“到达”类型跳转之间执行。 **[!UICONTROL Jump]**

1. 完成并保存此“子工作流”。
1. 创建“主”工作流。
1. 插入活 **[!UICONTROL Sub-workflow]** 动并将其打开。
1. 从下拉列表中选择要使用 **[!UICONTROL Workflow template]** 的工作流。

   ![](assets/subworkflow_selection.png)

1. 您还可以添加配置脚本以更改引用的工作流。
1. 单击 **[!UICONTROL Ok]**. 它将自动创建一个出站转移，其中带有选定工作 **[!UICONTROL Jump (start point)]** 流中活动的标签。

   ![](assets/subworkflow_outbound.png)

1. 运行工作流。

运行后，作为子工作流调用的工作流仍处于状 **[!UICONTROL Being edited]** 态，这意味着：

* 无法右键单击过渡以显示目标。
* 无法显示中间人群的计数。
* 日志在“主”工作流中汇总，并且只标记为“子工作流”。

事实上，此工作流只是一个模板。 从“主”工作流调用时，将创建基于此模板的新子工作流。

## 输入参数（可选） {#input-parameters--optional-}

* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这三个值集标识查询所定位的人群。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口（通常nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素数。

* targetSchema

此值是工作表的架构。 此参数适用于包含和的所有过 **[!UICONTROL tableName]** 渡 **[!UICONTROL schema]**。
