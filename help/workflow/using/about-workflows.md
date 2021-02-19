---
solution: Campaign Classic
product: campaign
title: 关于工作流
description: 利用工作流实现流程自动化、管理数据和受众、发送消息等。
audience: workflow
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: bb7e3ce726e2c589c033686cf3ab2960de140d91
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 20%

---


# 工作流入门{#gs-workflows}

## 关于工作流{#about-workflows}

Adobe Campaign包括一个工作流模块，它允许您跨应用程序服务器的不同模块协调所有流程和任务。 您可以利用这个全面的图形环境设计各式流程，包括部分划分、活动执行、文件处理、人员参与等。工作流引擎会执行并跟踪这些流程。

例如，您可以使用某个工作流从服务器下载文件、解压缩，然后将其中包含的记录导入 Adobe Campaign 数据库。

此外，一个工作流也可能涉及到要通知一个或多个操作员，或者是可以作出决策和批准流程的相关人员。这样就可以创建一次投放行动，将内容相关任务指派给一位或多位操作员，指定目标并在开始投放前获得批准。

工作流发生在活动管理过程的不同上下文和阶段。

Adobe Campaign使用工作流:

* 执行定位活动。 [了解详情](../../workflow/using/building-a-workflow.md#implementation-steps-)
* 构建活动:对于每个活动,**[!UICONTROL Workflow]**&#x200B;选项卡允许您构建目标并创建投放。 [了解详情](../../workflow/using/building-a-workflow.md#campaign-workflows)
* 执行技术流程：清理、收集跟踪信息或临时计算。 [了解详情](../../workflow/using/building-a-workflow.md#technical-workflows)

工作流可以表示流程定义（工作流模型，它表示应发生的事件）和此流程的实例（工作流实例，它表示实际发生的事件）。

工作流模板描述要执行的各种任务以及它们如何链接在一起。 任务模板称为活动，由图标表示。 它们被过渡联系在一起。

![](assets/example1.png)

每个工作流都包含：

* **[!UICONTROL Activities]**

   活动描述任务模板。 图中用图标表示各种可用活动。 每种类型都有通用属性和特定属性。 例如，尽管所有活动都有名称和标签，但只有&#x200B;**[!UICONTROL Approval]**&#x200B;活动有分配。

   在工作流图中，给定的活动可以生成多个任务，尤其是当存在循环或重复（周期）操作时。

   所有工作流活动列在[本节](../../workflow/using/about-activities.md)中，包括用例和示例。

* **[!UICONTROL Transitions]**

   过渡允许您链接活动并定义其序列。 过渡将源活动链接到目标活动。 有几种过渡，它们取决于源活动。 某些过渡具有其他参数，如持续时间、条件或过滤器。

   未链接到目标活动的过渡为橙色，箭头显示为菱形。

   >[!NOTE]
   >
   >仍可以执行包含未结束过渡的工作流：将生成一条警告消息，工作流在到达过渡后将暂停，但不会生成错误。 因此，可以在不完成的情况下开始工作流，并在您继续的同时添加工作流。

   有关如何构建工作流的详细信息，请参阅[本节](../../workflow/using/building-a-workflow.md)。

* **[!UICONTROL Worktables]**

   工作台包含过渡携带的所有信息。 每个工作流都使用多个工作表。 在工作流的整个生命周期中，只要不清除，这些表中传送的数据就可以被加速和使用。 事实上，每次工作流被钝化时，都会清除不需要的表，并且可能在执行最大工作流时会清除这些表，以避免服务器过载。

   了解有关[本节](../../workflow/using/how-to-use-workflow-data.md)中工作流数据和表的详细信息。

## 主要原则和最佳做法{#principles-workflows}

请参阅以下部分，以查找使用工作流自动处理流程的指南和最佳实践：

* 了解有关[此页](../../workflow/using/how-to-use-workflow-data.md)中工作流活动的更多信息。
* 了解如何在[本节](../../workflow/using/building-a-workflow.md)中构建工作流。
* 了解如何使用工作流在[此部分](../../platform/using/import-export-workflows.md)中的活动中导入数据。
* 工作流最佳实践详见[本页](../../workflow/using/workflow-best-practices.md)。
* 在[本节](../../workflow/using/starting-a-workflow.md)中查找有关工作流执行的指导。
* 了解如何在[此页](../../workflow/using/monitoring-workflow-execution.md)中监视工作流。
* 了解如何授予用户在[此页面](../../workflow/using/managing-rights.md)中使用工作流的权限。
