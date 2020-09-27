---
title: 关于工作流
description: 利用工作流实现流程自动化、管理数据和受众、发送消息等。
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 546c8f14006e333bb81aa52a008e9f1dfa79f03b
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 16%

---


# 开始使用工作流{#gs-workflows}

## 关于工作流{#about-workflows}

Adobe Campaign包括一个工作流模块，它允许您跨应用程序服务器的不同模块精心安排各种流程和任务。 您可以利用这个全面的图形环境设计各式流程，包括部分划分、活动执行、文件处理、人员参与等。工作流引擎会执行并跟踪这些流程。

例如，您可以使用某个工作流从服务器下载文件、解压缩，然后将其中包含的记录导入 Adobe Campaign 数据库。

此外，一个工作流也可能涉及到要通知一个或多个操作员，或者是可以作出决策和批准流程的相关人员。这样就可以创建一次投放行动，将内容相关任务指派给一位或多位操作员，指定目标并在开始投放前获得批准。

工作流发生在活动管理过程的各个上下文和阶段。

Adobe Campaign使用工作流来：

* 进行定位活动。 For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* 构建活动:对于每个活动, **[!UICONTROL Workflow]** 选项卡允许您构建目标并创建投放。 For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* 执行技术流程：清除、收集跟踪信息或临时计算。 For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

工作流可以指进程定义（工作流模型，它是应发生的内容的表示）和此进程的实例（工作流实例，它是实际发生的内容的表示）。

工作流模板描述要执行的各种任务以及它们如何链接在一起。 任务模板称为活动，由图标表示。 它们被过渡连接在一起。

![](assets/example1.png)

每个工作流都包含：

* **[!UICONTROL Activities]**

   活动描述任务模板。 图中用图标表示各种可用活动。 每种类型都有通用属性和特定属性。 例如，尽管所有活动都有名称和标签，但只有活动 **[!UICONTROL Approval]** 有分配。

   在工作流图中，给定活动可以生成多个任务，尤其是当存在循环或重复（周期）操作时。

   此部分列出了所有工作 [流活动](../../workflow/using/about-activities.md)，包括用例和示例。

* **[!UICONTROL Transitions]**

   过渡允许您链接活动并定义其顺序。 过渡将源活动链接到目标活动。 有几种过渡，它们取决于源活动。 某些过渡具有其他参数，如持续时间、条件或筛选器。

   未链接到目标过渡的活动为橙色，箭头显示为菱形。

   >[!NOTE]
   >
   >仍可以执行包含未结束过渡的工作流：将生成一条警告消息，工作流在到达过渡后将暂停，但不会生成错误。 因此，可以在不完成的情况下开始工作流，并随时添加工作流。

   有关如何构建工作流的详细信息，请参 [阅此部分](../../workflow/using/building-a-workflow.md)。

* **[!UICONTROL Worktables]**

   工作台包含过渡携带的所有信息。 每个工作流都使用多个工作表。 在工作流的整个生命周期中，只要不清除这些表中传送的数据，就可以加速并使用它们。 事实上，每次钝化工作流时，都会清除不需要的表，并且可能在执行最大工作流时会清除这些表，以避免服务器过载。

   在本节中进一步了解工作流数 [据和表](../../workflow/using/how-to-use-workflow-data.md)。

## 主要原则和最佳做法{#principles-workflows}

请参阅这些部分，找到指导和最佳实践，让工作流实现流程自动化：

* 了解有关本页中工作流活动 [的更多信息](../../workflow/using/how-to-use-workflow-data.md)。
* 在本节中了解如何构建工 [作流](../../workflow/using/building-a-workflow.md)。
* 了解如何在本节的工作流中使用 [导入活动](../../workflow/using/importing-data.md)。
* 本页详细介绍了工作流 [程最佳实践](../../workflow/using/workflow-best-practices.md)。
* 在本节中查找有关工作流执 [行的指导](../../workflow/using/starting-a-workflow.md)。
* 了解如何在本页中监 [视工作流](../../workflow/using/monitoring-workflow-execution.md)。
* 了解如何授予用户在本页中使用工作流 [的权限](../../workflow/using/managing-rights.md)。
