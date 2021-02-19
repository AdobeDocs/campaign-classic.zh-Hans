---
solution: Campaign Classic
product: campaign
title: 启动工作流
description: 了解如何开始工作流并发现工作流操作工具栏和右键单击菜单
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 2%

---


# 启动工作流 {#starting-a-workflow}

工作流始终手动启动。 但是，启动时，它可能会根据通过调度程序指定的信息(请参阅[调度程序](../../workflow/using/scheduler.md))或活动计划来保持非活动状态。

与定位工作流执行（启动、停止、暂停等）相关的操作 是&#x200B;**异步**&#x200B;进程：订单将记录下来，并在服务器可用时生效。

工具栏允许您开始和跟踪工作流的执行。

**[!UICONTROL Actions]**&#x200B;菜单和右键单击菜单中可用选项的列表详见下文。

>[!IMPORTANT]
>
>请记住，当操作员对工作流(开始、停止、暂停等)执行操作时，不会立即执行该操作，而是将其置于队列中，以便由[工作流模块](../../workflow/using/architecture.md)处理。

## 操作工具栏{#actions-toolbar}

此[部分](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)中详细介绍了工具栏按钮。 通过&#x200B;**[!UICONTROL Actions]**&#x200B;按钮，您可以访问其他执行选项以对选定工作流执行操作。 您还可以使用&#x200B;**[!UICONTROL File > Actions]**&#x200B;菜单，或右键单击工作流并选择&#x200B;**[!UICONTROL Actions]**。

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   通过此操作，您可以开始工作流的执行：**已完成的**、**正在编辑的**&#x200B;或&#x200B;**暂停的**&#x200B;工作流将状态更改为&#x200B;**已启动的**。 然后，工作流引擎将处理此工作流的执行。 如果暂停了工作流，则它会继续，否则，工作流会从开始开始启动，并激活初始活动。

   启动是一个异步进程：将保存请求，并尽快由工作流服务器进行处理。

* **[!UICONTROL Pause]**

   此操作将工作流的状态设置为&#x200B;**Paused**。 在恢复工作流之前，不会激活任何活动;但是，不会暂停正在执行的操作。

* **[!UICONTROL Stop]**

   此操作会停止当前正在执行的工作流。 实例的状态设置为&#x200B;**已完成**。 如果可能，停止正在进行的操作。 导入和SQL查询将立即取消。

   停止是一个异步进程。 注册请求，然后工作流服务器或服务器取消正在进行的操作。 因此，停止工作流实例可能需要时间，尤其是当工作流在多个服务器上运行时，每个服务器都必须控制以取消正在进行的任务时。

* **[!UICONTROL Restart]**

   此操作会停止，然后重新启动工作流。 在大多数情况下，它使重新启动更快。 在停止需要一定时间时自动重新启动也很有用：这是因为在工作流停止时“停止”命令不可用。

   **[!UICONTROL Start / Pause / Stop / Restart]**&#x200B;操作也可通过工具栏中的执行图标使用。 有关更多信息，请参阅此](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)章节[。

* **[!UICONTROL Purge history]**

   通过此操作，您可以清除工作流历史记录。 有关详细信息，请参阅[清除日志](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)。

* **[!UICONTROL Start in simulation mode]**

   通过此选项，您可以在模拟模式下开始工作流，而不是实际模式。 这意味着在启用此模式时，只执行不影响数据库或文件系统的活动(例如，**[!UICONTROL Query]**、**[!UICONTROL Union]**、**[!UICONTROL Intersection]**&#x200B;等。) 具有影响的活动(例如&#x200B;**[!UICONTROL Export]**、**[!UICONTROL Import]**&#x200B;等) 以及之后（在同一分支中）的不执行。

* **[!UICONTROL Execute pending tasks now]**

   通过此操作，您可以尽快开始所有待处理任务。 要开始特定任务，请右键单击其活动，然后选择&#x200B;**[!UICONTROL Execute pending task(s) now]**。

* **[!UICONTROL Unconditional stop]**

   此选项将工作流状态更改为&#x200B;**[!UICONTROL Finished]**。 仅当正常停止过程在几分钟后失败时，此操作才应作为最后手段。 如果您确定没有实际的工作流作业正在进行，请仅使用无条件停止。

   >[!CAUTION]
   >
   >此选项为专家用户保留。

* **[!UICONTROL Save as template]**

   此操作将基于选定的工作流创建新的工作流模板。 您需要指定保存该文件夹的文件夹（在&#x200B;**[!UICONTROL Folder]**&#x200B;字段中）。

   **[!UICONTROL Mass update of selected lines]**&#x200B;和&#x200B;**[!UICONTROL Merge selected lines]**&#x200B;选项是所有&#x200B;**[!UICONTROL Actions]**&#x200B;菜单中可用的通用平台选项。 有关更多信息，请参阅此](../../platform/using/updating-data.md)章节[。

## 右键单击菜单{#right-click-menu}

选择一个或多个工作流活动后，您可以右键单击以对所选内容执行操作。

![](assets/contextual_menu.png)

右键单击菜单中提供了以下选项：

**[!UICONTROL Open]**:此选项允许您访问活动属性。

**[!UICONTROL Display logs:]** 通过此选项，可以视图所选活动的任务执行日志。请参阅[显示日志](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)。

**[!UICONTROL Execute pending task(s) now:]** 通过此操作，您可以尽快开始待处理的任务。

**[!UICONTROL Workflow restart from a task:]** 此选项允许您使用之前为此活动存储的结果重新启动工作流。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 通过这些选项，您可以剪切、复制、粘贴和删除活动。

**[!UICONTROL Copy as bitmap:]** 通过此选项，您可以拍摄所有活动的屏幕截图。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 这些选项也可在“活动” **[!UICONTROL Advanced]** 属性的选项卡中使用。详见[执行](../../workflow/using/advanced-parameters.md#execution)。

**[!UICONTROL Save / Cancel:]** 允许您保存或取消对工作流所做的更改。

>[!NOTE]
>
>您可以选择一组活动，并将这些命令之一应用到它们。

右键单击菜单也详见此[部分](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)。
