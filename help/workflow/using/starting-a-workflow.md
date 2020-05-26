---
title: 启动工作流
description: 了解如何开始工作流并发现工作流操作工具栏和右键单击菜单。
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---


# 启动工作流 {#starting-a-workflow}

工作流始终手动启动。 但是，启动后，它可能会根据通过调度程序指定的信息(请参阅 [调度程序](../../workflow/using/scheduler.md))或活动计划保持非活动状态。

与定位工作流执行（启动、停止、暂停等）相关的操作 是异 **步进** 程： 订单将被记录下来，一旦服务器可以应用该订单，该订单将生效。

工具栏允许您开始和跟踪工作流的执行。

菜单和右键菜单中 **[!UICONTROL Actions]** 可用选项的列表在下面详细介绍。

## 操作工具栏 {#actions-toolbar}

此部分详细介绍了工具栏 [按钮](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。 通过 **[!UICONTROL Actions]** 该按钮，您可以访问其他执行选项，以对选定工作流执行操作。 您还可以使用 **[!UICONTROL File > Actions]** 菜单，或右键单击工作流并选择 **[!UICONTROL Actions]**。

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   通过此操作，您可以开始工作流的执行： 已完成、正在编 **辑或已**&#x200B;暂 **停的工作** 流将状 **态更改** 为“已 ****&#x200B;开始”。 工作流引擎随后将处理此工作流的执行。 如果工作流已暂停，则它将恢复，否则，工作流将从开始开始启动，并激活初始活动。

   启动是一个异步进程： 此请求将被保存并尽快由工作流服务器进行处理。

* **[!UICONTROL Pause]**

   此操作将工作流的状态设置为“已 **暂停**”。 在恢复工作流之前，不会激活活动; 但是，不会暂停正在进行的操作。

* **[!UICONTROL Stop]**

   此操作会停止当前正在执行的工作流。 实例的状态设置为“已 **完成**”。 如果可能，停止正在进行的操作。 导入和SQL查询将立即取消。

   停止是一个异步进程。 注册请求，然后工作流服务器或服务器取消正在进行的操作。 因此，停止工作流实例可能需要时间，尤其是当工作流正在多台服务器上运行时，每个服务器都必须控制以取消正在进行的任务。

* **[!UICONTROL Restart]**

   此操作停止，然后重新启动工作流。 在大多数情况下，它使得能够更快地重启。 在停止需要一定时间时自动重新启动也很有用： 这是因为在工作流停止时“停止”命令不可用。

   操 **[!UICONTROL Start / Pause / Stop / Restart]** 作也可通过工具栏中的执行图标使用。 For more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   通过此操作，您可以清除工作流历史记录。 有关此问题的详细信息，请 [参阅清除日志](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)。

* **[!UICONTROL Start in simulation mode]**

   通过此选项，您可以在开始模式下模拟工作流，而不是在实际模式下。 这意味着在启用此模式时，只会执行不影响活动库或文件系统的(例如， **[!UICONTROL Query]**、 **[!UICONTROL Union]**、 **[!UICONTROL Intersection]**&#x200B;等)。 具有影响的活动(例如， **[!UICONTROL Export]**、 **[!UICONTROL Import]**&#x200B;等) 以及之后（在同一分支中）的签名未执行。

* **[!UICONTROL Execute pending tasks now]**

   通过此操作，您可以尽快开始所有待处理的任务。 要开始特定任务，请右键单击其活动并选择 **[!UICONTROL Execute pending task(s) now]**。

* **[!UICONTROL Unconditional stop]**

   此选项将工作流状态更改为 **[!UICONTROL Finished]**。 仅当正常停止过程在几分钟后失败时，此操作才应用为最后手段。 仅当确定没有实际的工作流作业正在进行时，才使用无条件停止。

   >[!CAUTION]
   >
   >此选项为专家用户保留。

* **[!UICONTROL Save as template]**

   此操作会根据所选工作流创建新的工作流模板。 您需要指定保存该文件夹的文件夹(在字 **[!UICONTROL Folder]** 段中)。

   和选 **[!UICONTROL Mass update of selected lines]** 项 **[!UICONTROL Merge selected lines]** 是所有菜单中可用的通用平台 **[!UICONTROL Actions]** 选项。 For more on this, refer to this [section](../../platform/using/updating-data.md).

## 右键单击菜单 {#right-click-menu}

选择一个或多个工作流活动后，您可以右键单击以根据您的选择操作。

![](assets/contextual_menu.png)

右击菜单中提供以下选项：

**[!UICONTROL Open]**: 通过此选项，您可以访问活动属性。

**[!UICONTROL Display logs:]** 通过此选项，可以视图所选活动的任务执行日志。 请参阅显 [示日志](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)。

**[!UICONTROL Execute pending task(s) now:]** 通过此操作，您可以尽快开始待处理的任务。

**[!UICONTROL Workflow restart from a task:]** 通过此选项，您可以使用之前为此活动存储的结果重新启动工作流。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 通过这些选项，您可以剪切、复制、粘贴和删除活动。

**[!UICONTROL Copy as bitmap:]** 通过此选项，您可以拍摄所有活动的屏幕截图。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 这些选项也可在活动 **[!UICONTROL Advanced]** 属性的选项卡中使用。 执行中详细介绍 [了这些](../../workflow/using/advanced-parameters.md#execution)。

**[!UICONTROL Save / Cancel:]** 允许您保存或取消对工作流所做的更改。

>[!NOTE]
>
>您可以选择一组活动，并将这些命令之一应用到它们。

右击菜单也详见本 [节](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)。
