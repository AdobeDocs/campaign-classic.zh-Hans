---
title: 关于工作流
seo-title: 关于工作流
description: 关于工作流
seo-description: null
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
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 关于工作流{#about-workflows}

Adobe Campaign包括一个工作流模块，它使您能够跨应用程序服务器的不同模块精心安排各种流程和任务。 您可以利用这个全面的图形环境设计各式流程，包括部分划分、活动执行、文件处理、人员参与等。工作流引擎会执行并跟踪这些流程。

例如，您可以使用某个工作流从服务器下载文件、解压缩，然后将其中包含的记录导入 Adobe Campaign 数据库。

此外，一个工作流也可能涉及到要通知一个或多个操作员，或者是可以作出决策和批准流程的相关人员。这样就可以创建一次投放行动，将内容相关任务指派给一位或多位操作员，指定目标并在开始投放前获得批准。

工作流在营销活动管理流程的不同上下文和阶段中进行。

Adobe Campaign使用工作流来：

* 开展定位营销活动。 For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* 构建营销活动：对于每个营销活动， **[!UICONTROL Workflow]** 您都可以通过选项卡构建目标并创建分发。 For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* 执行技术流程：清除、收集跟踪信息或临时计算。 For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

工作流可以指进程定义（工作流模型，它是应发生事件的表示）和此进程的实例（工作流实例，它是实际发生事件的表示）。

工作流模板描述要执行的各种任务以及它们如何链接在一起。 任务模板称为活动，由图标表示。 它们通过过渡连接在一起。

![](assets/example1.png)

每个工作流都包含：

* **[!UICONTROL Activities]**

   活动描述任务模板。 图中用图标表示各种可用活动。 每种类型都有通用属性和特定属性。 例如，尽管所有活动都有名称和标签，但只有活 **[!UICONTROL Approval]** 动有分配。

   在工作流图中，特定活动可以生成多个任务，特别是当存在循环或重复（周期）操作时。

   此部分列出了所有工作流 [活动](../../workflow/using/about-activities.md)，包括用例和示例。

* **[!UICONTROL Transitions]**

   过渡可让您链接活动并定义其顺序。 过渡将源活动链接到目标活动。 有几种过渡，具体取决于源活动。 某些过渡具有其他参数，如持续时间、条件或过滤器。

   未链接到目标活动的过渡为橙色，箭头显示为菱形。

   >[!NOTE]
   >
   >仍然可以执行包含未结束过渡的工作流：将生成一条警告消息，工作流到达过渡后将暂停，但不会生成错误。 因此，可以在不完成的情况下启动工作流，并在继续时向其添加。

   有关如何构建工作流的详细信息，请参阅 [此部分](../../workflow/using/building-a-workflow.md)。

* **[!UICONTROL Worktables]**

   工作台包含转换所携带的所有信息。 每个工作流都使用多个工作表。 只要不清除，这些表中传送的数据就可以在工作流的整个生命周期中加速和使用。 事实上，每次钝化工作流时都会清除不需要的表，并且可能在执行最大的工作流时会清除这些表，以避免服务器过载。

   在本节中进一步了解工作流数据 [和表](../../workflow/using/how-to-use-workflow-data.md)。

