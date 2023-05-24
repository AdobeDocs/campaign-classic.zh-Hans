---
product: campaign
title: 开始工作流
description: 了解如何启动工作流和发现工作流操作工具栏和右键单击菜单
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# 开始工作流 {#starting-a-workflow}



工作流始终手动启动。 但是，在启动时，它可能会保持不活动状态，具体取决于通过调度程序指定的信息(请参阅 [调度程序](scheduler.md))或活动计划。

与定向工作流执行相关的操作（启动、停止、暂停等） 是 **异步** 进程：订单已记录下来，一旦服务器可以应用它就会生效。

利用工具栏，可启动和跟踪工作流的执行。

中可用的选项列表 **[!UICONTROL Actions]** 菜单和右键单击菜单详见下文。

>[!IMPORTANT]
>
>请记住，当操作员对工作流执行操作（启动、停止、暂停等）时，该操作不是立即执行，而是放入队列中以便 [工作流模块](architecture.md).

## “操作”工具栏 {#actions-toolbar}

此处详细介绍了工具栏按钮 [部分](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). 此 **[!UICONTROL Actions]** 按钮可让您访问用于对所选工作流执行操作的其他执行选项。 您还可以使用 **[!UICONTROL File > Actions]** 菜单，或右键单击工作流并选择 **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   通过此操作，您可以开始执行工作流：此工作流具有以下特点： **已完成**， **正在编辑** 或 **已暂停** 将状态更改为 **已开始**. 然后，工作流引擎处理此工作流的执行。 如果工作流已暂停，则会恢复它，否则工作流将从头开始启动，并激活初始活动。

   启动是一个异步过程：工作流服务器会保存并尽快处理请求。

* **[!UICONTROL Pause]**

   此操作将工作流的状态设置为 **已暂停**. 在工作流恢复之前，不会激活任何活动；但不会暂停正在进行的操作。

* **[!UICONTROL Stop]**

   此操作停止当前正在执行的工作流。 实例的状态设置为 **已完成**. 如果可能，正在进行的操作将停止。 立即取消导入和SQL查询。

   >[!IMPORTANT]
   >
   >停止工作流是一个异步过程：请求已注册，然后工作流服务器或服务器取消正在进行的操作。 因此，停止工作流实例可能需要一些时间，尤其是当工作流在多台服务器上运行时，每台服务器都必须控制以取消正在进行的任务。 为避免出现任何问题，请等待停止操作完成，并且不要在同一工作流上执行多个停止请求。

* **[!UICONTROL Restart]**

   此操作将停止，然后重新启动工作流。 在大多数情况下，它可以更快地重新启动。 在停止需要一定时间后自动重新启动也很有用：这是因为在停止工作流时，“Stop”命令不可用。

   此 **[!UICONTROL Start / Pause / Stop / Restart]** 也可以通过工具栏中的执行图标执行操作。 有关更多信息，请参阅此](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)章节[。

* **[!UICONTROL Purge history]**

   通过此操作，您可以清除工作流历史记录。 有关更多信息，请参阅 [清除日志](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   利用此选项，您可以在模拟模式而不是实际模式下启动工作流。 这意味着在启用此模式时，只会执行不影响数据库或文件系统的活动(例如 **[!UICONTROL Query]**， **[!UICONTROL Union]**， **[!UICONTROL Intersection]**、等)。 有影响的活动(例如 **[!UICONTROL Export]**， **[!UICONTROL Import]**、等) 以及执行它们之后的项目（在同一分支中）不会被执行。

* **[!UICONTROL Execute pending tasks now]**

   通过此操作，您可以尽快启动所有待处理任务。 要启动特定任务，请右键单击其活动并选择 **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   此选项会将工作流状态更改为 **[!UICONTROL Finished]**. 仅当正常停止过程在几分钟后失败时，才应将此操作用作最后的手段。 只有在您确定没有正在执行的实际工作流作业时，才使用无条件停止。

   >[!CAUTION]
   >
   >此选项为专家用户保留。

* **[!UICONTROL Save as template]**

   此操作基于所选工作流创建新的工作流模板。 您需要指定保存该文件的文件夹(在 **[!UICONTROL Folder]** 字段)。

   此 **[!UICONTROL Mass update of selected lines]** 和 **[!UICONTROL Merge selected lines]** 选项是所有中提供的通用平台选项 **[!UICONTROL Actions]** 菜单。 有关更多信息，请参阅此](../../platform/using/updating-data.md)章节[。

## 右键单击菜单 {#right-click-menu}

选择一个或多个工作流活动后，您可以右键单击以根据您的选择执行操作。

![](assets/contextual_menu.png)

右键单击菜单中提供了以下选项：

**[!UICONTROL Open]**：利用此选项可访问活动属性。

**[!UICONTROL Display logs:]** 通过此选项，可以查看所选活动的任务执行日志。 请参阅 [显示日志](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** 通过此操作，您可以尽快启动待处理任务。

**[!UICONTROL Workflow restart from a task:]** 利用此选项，您可以使用之前为此活动存储的结果重新启动工作流。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 这些选项允许您剪切、复制、粘贴和删除活动。

**[!UICONTROL Copy as bitmap:]** 利用此选项，可拍摄所有活动的屏幕快照。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 这些选项也可在以下位置找到： **[!UICONTROL Advanced]** 选项卡中。 有关详情，请参阅 [执行](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** 用于保存或取消对工作流所做的更改。

>[!NOTE]
>
>您可以选择一组活动，然后将其中一个命令应用于这些活动。

右键菜单也详见以下内容 [部分](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
