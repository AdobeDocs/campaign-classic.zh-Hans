---
product: campaign
title: 开始工作流
description: 了解如何启动工作流和发现工作流操作工具栏和右键单击菜单
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 1baf424138c95b16add37d9d556e3a2566a869c2
workflow-type: tm+mt
source-wordcount: '1115'
ht-degree: 2%

---

# 开始工作流 {#starting-a-workflow}



工作流始终以手动方式启动。 但是，在启动时，它可能会保持不活动状态，具体取决于通过调度程序指定的信息(请参阅 [计划程序](scheduler.md))或活动计划。

与定向工作流执行（启动、停止、暂停等）相关的操作 是 **异步** 进程：记录此顺序，一旦服务器可以应用此顺序后，此顺序即生效。

利用工具栏，您可以启动和跟踪工作流的执行情况。

中可用的选项列表 **[!UICONTROL Actions]** 菜单和右键单击菜单详见如下。

>[!IMPORTANT]
>
>请记住，当操作员对工作流执行操作（启动、停止、暂停等）时，该操作不是立即执行，而是放入队列中，以便由 [工作流模块](architecture.md).

## “操作”工具栏 {#actions-toolbar}

此页面详细介绍了工具栏按钮 [部分](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). 此 **[!UICONTROL Actions]** 按钮可让您访问用于对所选工作流执行操作的其他执行选项。 您也可以使用 **[!UICONTROL File > Actions]** 菜单，或右键单击工作流并选择 **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

  通过此操作，您可以开始执行工作流：此工作流具有以下特征： **已完成**， **正在编辑** 或 **已暂停** 将状态更改为 **已开始**. 然后，工作流引擎将处理此工作流的执行。 如果工作流已暂停，则会恢复该工作流，否则，将从头开始启动工作流并激活初始活动。

  启动是一个异步过程：工作流服务器会保存并尽快处理请求。

* **[!UICONTROL Pause]**

  此操作将工作流的状态设置为 **已暂停**. 在工作流恢复之前，不会激活任何活动；但不会暂停正在进行的操作。

* **[!UICONTROL Stop]**

  此操作停止当前正在执行的工作流。 实例的状态设置为 **已完成**. 如果可能，正在进行的操作将停止。 立即取消导入和SQL查询。

  >[!IMPORTANT]
  >
  >停止工作流是一个异步过程：请求已注册，然后工作流服务器或服务器取消正在进行的操作。 因此，停止工作流实例可能需要一些时间，尤其是当工作流在多台服务器上运行时，每台服务器都必须控制以取消正在进行的任务。 要避免出现任何问题，请等待停止操作完成，并且不要在同一工作流上执行多个停止请求。

* **[!UICONTROL Unconditional stop]**

  此选项会将工作流状态更改为 **[!UICONTROL Finished]**. 仅当正常停止过程在几分钟后失败时，才应将此操作作为最后的手段。 只有在您确定没有实际正在进行的工作流作业时，才使用无条件停止。

  >[!CAUTION]
  >
  >此选项为专家用户保留。

* **[!UICONTROL Restart]**

  此操作将停止，然后重新启动工作流。 在大多数情况下，它可以更快地重新启动。 当停止需要一定时间时，自动重新启动也很有用：这是因为在工作流停止时，“Stop”命令不可用。

  此 **[!UICONTROL Start / Pause / Stop / Restart]** 也可以通过工具栏中的执行图标执行操作。 有关更多信息，请参阅此](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)章节[。

* **[!UICONTROL Purge history]**

  通过此操作，您可以清除工作流历史记录。 有关详细信息，请参见 [清除日志](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

  使用此选项，您可以在模拟模式下而不是实际模式下启动工作流。 这意味着在启用此模式时，将只执行不影响数据库或文件系统的活动(例如， **[!UICONTROL Query]**， **[!UICONTROL Union]**， **[!UICONTROL Intersection]**、等)。 有影响的活动(例如 **[!UICONTROL Export]**， **[!UICONTROL Import]**、等) 以及执行它们之后的那些操作（在同一分支中）不会被执行。

* **[!UICONTROL Execute pending tasks now]**

  通过此操作，您可以尽快启动所有待处理任务。 要启动特定任务，请右键单击其活动并选择 **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Save as template]**

  此操作基于所选工作流创建新的工作流模板。 您需要指定保存该文件的文件夹(在 **[!UICONTROL Folder]** 字段)。

  此 **[!UICONTROL Mass update of selected lines]** 和 **[!UICONTROL Merge selected lines]** 选项是所有页面中提供的通用平台选项 **[!UICONTROL Actions]** 菜单。 有关更多信息，请参阅此](../../platform/using/updating-data.md)章节[。


## 工作流执行最佳实践 {#workflow-execution-best-practices}

**请勿将工作流计划为运行时间超过每15分钟** 因为它可能会影响整体系统性能，并在数据库中创建块。

**避免使工作流处于暂停状态**. 如果您创建临时工作流，请确保它能正确完成并且不会停留在 **[!UICONTROL paused]** 省/州。 如果暂停，则意味着您需要保留临时表，从而增加数据库的大小。 在“工作流属性”下分配工作流监督员，以便在工作流失败或系统暂停时发送警报。

要避免工作流处于暂停状态，请执行以下操作：

* 请定期检查您的工作流，以确保没有意外错误。
* 使您的工作流尽可能简单，例如，通过将大型工作流拆分到多个不同的工作流中。 您可以使用 **[!UICONTROL External signal]** 活动根据其他工作流的执行触发其执行。
* 避免在工作流中禁用流导致线程处于打开状态的活动，这样会导致出现许多临时表，占用大量空间。 不要保留活动 **[!UICONTROL Do not enable]** 或 **[!UICONTROL Enable but do not execute]** 工作流中的状态。

**停止未使用的工作流**. 保持运行的工作流保持与数据库的连接。

**仅在极少数情况下使用无条件停止**. 请勿定期使用此操作。 如果对工作流生成到数据库的连接不执行干净关闭，则会影响性能。

**不要在同一工作流上执行多个停止请求**. 停止工作流是一个异步过程：请求已注册，然后工作流服务器或服务器取消正在进行的操作。 因此，停止工作流实例可能需要一些时间，尤其是当工作流在多台服务器上运行时，每台服务器都必须控制以取消正在进行的任务。 要避免出现任何问题，请等待停止操作完成，避免多次停止工作流。

## 右键单击菜单 {#right-click-menu}

选择一个或多个工作流活动后，您可以右键单击以根据您的选择执行操作。

![](assets/contextual_menu.png)

右键单击菜单中提供了以下选项：

**[!UICONTROL Open]**：利用此选项可访问活动属性。

**[!UICONTROL Display logs:]** 使用此选项可以查看所选活动的任务执行日志。 请参阅 [显示日志](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** 此操作允许您尽快启动待处理任务。

**[!UICONTROL Workflow restart from a task:]** 利用此选项，您可以使用之前为此活动存储的结果重新启动工作流。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 这些选项允许您剪切、复制、粘贴和删除活动。

**[!UICONTROL Copy as bitmap:]** 利用此选项，可拍摄所有活动的屏幕快照。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 这些选项也可在 **[!UICONTROL Advanced]** 活动属性的选项卡。 有关详情，请参阅 [执行](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** 用于保存或取消对工作流所做的更改。

>[!NOTE]
>
>您可以选择一组活动，然后将其中一个命令应用于这些活动。

右键菜单也详见于此 [部分](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
