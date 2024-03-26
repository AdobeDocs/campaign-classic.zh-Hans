---
product: campaign
title: 关于工作流
description: 利用工作流实现流程自动化、管理数据和受众、发送消息等
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Data Management
exl-id: 51be6b90-2a7a-4757-9754-d16c540a87ff
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 38%

---

# 工作流入门{#gs-workflows}



## 关于工作流{#about-workflows}

Adobe Campaign 包含一个工作流模块，允许您在应用程序服务器的不同模块之间编排所有流程和任务。您可以利用这个全面的图形环境设计各式流程，包括部分划分、活动执行、文件处理、人员参与等。工作流引擎会执行并跟踪这些流程。

例如，您可以使用某个工作流从服务器下载文件、解压缩，然后将其中包含的记录导入 Adobe Campaign 数据库。

此外，一个工作流也可能涉及到要通知一个或多个操作员，或者是可以作出决策和批准流程的相关人员。这样就可以创建一次投放行动，将内容相关任务指派给一位或多位操作员，指定目标并在开始投放前获得批准。

工作流在营销活动管理流程的不同上下文和阶段中出现。

Adobe Campaign使用工作流执行以下操作：

* 开展定位活动。 [了解详情](building-a-workflow.md#implementation-steps-)
* 构建营销活动：对于每个营销活动， **[!UICONTROL Workflow]** 选项卡允许您构建目标和创建投放。 [了解详情](building-a-workflow.md#campaign-workflows)
* 执行技术流程：清理、收集跟踪信息或临时计算。 [了解详情](building-a-workflow.md#technical-workflows)

工作流可以是指流程定义（工作流模型，用于表示应该发生的情况）以及此流程的实例（工作流实例，用于表示实际发生的情况）。

工作流模板描述了要执行的各种任务及其关联方式。任务模板称作活动并由图标表示。它们通过过渡关联起来。

![](assets/example1.png)

每个工作流包含：

* **[!UICONTROL Activities]**

  活动描述了任务模板。 可用的各种活动在图中由图标表示。每种类型都有通用属性和特定属性。 例如，虽然所有活动都有名称和标签，但只有 **[!UICONTROL Approval]** 活动具有分配。

  在工作流图中，给定活动可以生成多个任务，尤其是当存在循环或循环（定期）操作时。

  中列出了所有工作流活动 [本节](about-activities.md)，包括用例和示例。

* **[!UICONTROL Transitions]**

  利用过渡，可链接活动并定义其顺序。 过渡会将源活动链接到目标活动。 有多种类型的过渡，这取决于源活动。 某些过渡具有其他参数，如持续时间、条件或过滤器。

  未链接到目标活动的过渡为橙色，并且箭头头显示为菱形。

  >[!NOTE]
  >
  >包含未终止过渡的工作流仍可以执行：将生成警告消息，工作流在到达过渡后将暂停，但不会生成错误。 因此，可以在不完成工作流的情况下启动该工作流，并在工作流中添加工作流。

  有关如何构建工作流的更多信息，请参阅 [本节](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  工作台包含由过渡承载的所有信息。 每个工作流均使用多个工作表。只要不清除这些表中的数据，就可以在整个工作流的生命周期中加速和使用这些数据。 实际上，每次工作流被钝化时以及可能在执行最大工作流期间，都会清除不需要的表，以避免服务器过载。

  在中了解有关工作流数据和表的更多信息 [本节](how-to-use-workflow-data.md).

## 主要原则和最佳实践{#principles-workflows}

请参阅以下部分，查找使用工作流自动化流程的指导和最佳实践：

* 在中了解有关工作流活动的更多信息 [此页面](how-to-use-workflow-data.md).
* 了解如何在中构建工作流 [本节](building-a-workflow.md).
* 在中了解如何使用工作流导入Campaign中的数据 [本节](../../platform/using/import-export-workflows.md).
* 有关工作流最佳实践的详情，请参阅 [此页面](workflow-best-practices.md).
* 在中查找有关工作流执行的指导 [本节](starting-a-workflow.md).
* 了解如何在中监测工作流 [此页面](monitoring-workflow-execution.md).
* 了解如何向用户授予访问权限，以在中使用工作流 [此页面](managing-rights.md).
