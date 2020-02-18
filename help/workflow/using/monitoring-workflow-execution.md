---
title: 监视工作流执行
seo-title: 监视工作流执行
description: 监视工作流执行
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 202f571f5c348ca4ab617821cd1ec24cefa8c504

---


# 监视工作流执行 {#monitoring-workflow-execution}

本节介绍如何监控工作流的执行。

此部分还提供了有关如何创建工作流的用例，该工作流允许您监视“已暂停”、“已停止”或“有错误”的一组工作流的 [状态](../../workflow/using/supervising-workflows.md#supervising-workflows)。

此外，实例的管理员可以使用审核跟踪 **检查活动** ，以及对工作流所做的最后修改（工作流的状态）。 For more on this, refer to the [dedicated section](../../production/using/audit-trail.md).

本页介绍了其他监视不同营销活动流程 [的方法](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)。

## 显示进度 {#displaying-progress}

您可以使用工具栏中的相应图标显示进度，以监控执行情况。

通过 **[!UICONTROL Display progress information]** 该图标，您可以在执行屏幕中显示状态和活动结果。

![](assets/s_user_segmentation_toolbar_progr.png)

选择此选项后，执行的活动将以蓝色显示，待处理活动会闪烁，警告以橙色显示，错误以红色显示。 此选项还显示活动在其出站转移时的结果，后跟活动属性中定义的结果标签以及作业的持续时间（如果超过一秒）

![](assets/s_user_segmentation_results.png)

## 显示日志 {#displaying-logs}

日志包含工作流的历史记录或审核跟踪。 它注册所有用户操作、执行的所有操作和遇到的错误。 您可以：

* 在详细信 **[!UICONTROL Tracking]** 息中选择选项卡。 此列表包含所有工作流消息。

   ![](assets/new-workflow-display-log-tab.png)

* 按活动过滤日志消息。 为此，请单 **[!UICONTROL Display the tasks and the log]** 击图上方的工具栏，以显示图下方的 **[!UICONTROL Log]** 和 **[!UICONTROL Tasks]** 选项卡。 选择活动以查看所有相关消息。 当未选择任何活动时，此列表包含所有消息。

   ![](assets/new-workflow-display-log-activity.png)

   >[!NOTE]
   >
   >单击图背景以取消选择所有元素。

* 仅查看链接到给定任务的消息。 为此，请选择选 **[!UICONTROL Tasks]** 项卡，然后在图中选择活动以限制列表。 双击任务以显示信息；窗口中的最后一个选项卡包含日志。

   ![](assets/new-workflow-display-tasks-activity.png)

   通过 **[!UICONTROL Details...]** 该按钮可显示有关活动执行的所有其他信息。 例如，您可以查看验证运算符，以及在审批过程中输入的注释（如果适用），如下例所示：

   ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>重新启动工作流时，不会清除日志。 留言。 如果要放弃先前执行中的消息，则必须清除历史记录。

该日志显示与定位工作流活动相关的执行消息的时间顺序列表。

* 定位营销活动的日志

   执行定位营销活动后，单击该选 **[!UICONTROL Tracking]** 项卡以查看执行跟踪。

   ![](assets/s_user_segmentation_journal.png)

   将显示所有营销活动消息：执行的营销活动以及警告或错误。

* 活动日志

   您还可以查看执行日志和每个活动的详细信息。 有两种方法可以实现此目的：

   1. 选择目标活动，然后单击 **[!UICONTROL Display the tasks and the log]** 图标。

      ![](assets/s_user_segmentation_show_logs.png)

      图的下部显示两个选项卡：日志和任务。

      在图中选择的活动用作日志和任务列表上的过滤器。

      ![](assets/s_user_segmentation_logs.png)

   1. 右键单击目标活动并选择 **[!UICONTROL Display logs]**。

      ![](assets/s_user_segmentation_logs_menu.png)

      日志显示在单独的窗口中。

## 清除日志 {#purging-the-logs}

工作流历史记录不会自动清除：默认情况下，所有消息都会保留。 可以通过菜单或单击列 **[!UICONTROL File > Actions]** 表上方工具栏中的按 **[!UICONTROL Actions]** 钮来清除历史记录。 Select **[!UICONTROL Purge history]**. 菜单中的可用选 **[!UICONTROL Actions]** 项在“操作”工具栏部分 [中有详细说明](../../workflow/using/executing-a-workflow.md#actions-toolbar) 。

![](assets/purge_historique.png)

## 工作表和工作流架构 {#worktables-and-workflow-schema}

该工作流传达了可通过某些活动操作的工作表。 Adobe Campaign允许您通过数据管理活动修改、重命名和扩充工作流工作表的列，例如，根据客户的需要将这些列与术语对齐，以收集有关合同共同受益人的其他信息，等等。

还可以在各种工作维之间创建链接并定义维更改。 例如，对于记录在数据库中的每个合同，寻址主持有人并在附加信息中使用共同持有人数据。

当工作流被钝化时，工作流的工作表会自动删除。 如果要保留工作表，请通过活动将其保存在列表中(请 **[!UICONTROL List update]** 参阅列 [表更新](../../workflow/using/list-update.md))。

## 管理错误 {#managing-errors}

发生错误时，工作流暂停，发生错误时执行的活动闪烁红色。 在工作流概述(**[!UICONTROL Monitoring]** Universe > **[!UICONTROL Workflows]** link)中，您只能显示有错误的工作流，如下所示。

![](assets/wf-global-view_filter_only_errors.png)

在Adobe Campaign资源管理器中，默认情况下，工作流列表 **[!UICONTROL Failed]** 显示一列。

![](assets/wf-explorer_errors_col.png)

当工作流出错时，只要其电子邮件地址列在其配置文件中，属于工作流监督组的操作员就会通过电子邮件收到通知。 在工作流属性的字段 **[!UICONTROL Supervisor(s)]** 中选择此组。

![](assets/wf-properties_select-supervisors.png)

通知内容在默认模板 **[!UICONTROL Workflow manager notification]** 中配置：此模板在工作流属性 **[!UICONTROL Execution]** 的选项卡中被选中。 通知会显示错误工作流的名称和相关任务。

通知示例：

![](assets/wf-notification_error-msg.png)

通过该链接，您可以在Web模式下访问Adobe Campaign控制台，并在登录后继续处理错误工作流。

![](assets/wf-notification_error-console.png)

您可以配置工作流，以便它不会暂停并在出错时继续执行。 为此，请编辑工作 **[!UICONTROL Properties]** 流，并在部 **[!UICONTROL Error management]** 分中，选择 **[!UICONTROL Ignore]** 字段中的选 **[!UICONTROL In case of error]** 项。 然后，您可以指定在暂停进程之前可以忽略的连续错误数。

在这种情况下，将中止错误任务。 此模式特别适用于设计为稍后重新尝试营销活动（定期操作）的工作流。

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>您可以为每个活动单独应用此配置。 为此，请编辑活动属性，然后在选项卡中选择错误管理 **[!UICONTROL Advanced]** 模式。

有关工作流执行疑难解答的更多信息，请参阅专 [用部分](../../production/using/workflow-execution.md)。

## 处理错误 {#processing-errors}

关于活动，该选 **[!UICONTROL Process errors]** 项显示一个特定的过渡，如果生成错误，该过渡将被启用。 在这种情况下，工作流不会进入错误模式并继续执行。

考虑到的错误是文件系统错误（无法移动文件、无法访问目录等）。

此选项不处理与活动配置相关的错误，即无效值。 与错误配置相关的错误将不会启用此转换（目录不存在等）。

如果工作流暂停（手动或在出错后自动暂停），则按钮会在 **[!UICONTROL Start]** 停止工作流的位置重新开始执行。 将重新执行错误的活动（或暂停的活动）。 不会重新执行以前的活动。

要重新执行所有工作流活动，请使用按 **[!UICONTROL Restart]** 钮。

如果您修改了已执行的活动，则在重新启动工作流执行时，不会考虑这些更改。

如果修改未执行的活动，则在重新启动工作流执行时，会考虑这些活动。

如果修改暂停的活动，则在重新启动工作流时无法正确考虑所做的更改。

如果可能，我们建议在进行修改后完全重新启动工作流。

## 实例监督 {#instance-supervision}

通过 **[!UICONTROL Instance supervision]** 该页面，您可以查看Adobe Campaign服务器活动并显示包含错误的工作流和交付的列表。

要访问此页，请转到范 **[!UICONTROL Monitoring]** 围并单击链 **[!UICONTROL General view]** 接。

![](assets/wf-monitoring_from-homepage.png)

要显示所有工作流，请单击该 **[!UICONTROL Workflows]** 链接。 使用下拉列表根据工作流的状态显示平台中的工作流。

![](assets/wf-monitoring_edit-wf.png)

单击某个工作流中存在错误的链接，以打开并查看其日志。

![](assets/wf-monitoring_edit-task-wf.png)

## 防止同时执行多个执行 {#preventing-simultaneous-multiple-executions}

单个工作流可以同时运行多个执行。 在某些情况下，您应该防止这种情况发生。

例如，您可以让一个调度程序每小时触发工作流执行，但有时整个工作流的执行需要超过一小时。 如果工作流已在运行，您可能希望跳过执行。

如果工作流开始时有信号活动，则在工作流正在运行时，您可能希望跳过信号。

一般原则如下：

![](assets/workflow-reentrancy-protection-principle.png)

解决方案是使用实例变量。 实例变量由工作流的所有并行执行共享。

以下是一个简单的测试工作流：

![](assets/wkf_simultaneous_execution1.png)

每 **[!UICONTROL Scheduler]** 分钟都会触发一个事件。 以下 **[!UICONTROL Test]** 活动将测试 **isRunning** 实例变量，以决定是否继续执行：

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning是为此示例选择的变量名称。** 这不是内置变量。

紧靠“是”分支 **[!UICONTROL Test]** 中的 **活动** ，必须在其“初始化”脚本中设置 **实例变量**:

```
instance.vars.isRunning = true
```

“是”分支中的最后一个活 **动** ，必须将其初始化脚本中的变量还原 **为false**:

```
instance.vars.isRunning = false
```

请注意：

* 您可以通过工作流“属性”中的“变量”选项 **卡** ，检查实例变量的当 **前值**。
* 在重新启动工作流时，实例变量会重置。
* 在JavaScript中，未定义的值在测试中为false，允许在初始化实例变量之前测试该实例变量。
* 您可以通过向“no”结束的初始化脚本中添加记录指令来监视因此机制未处理的活动。

   ```
   logInfo("Workflow already running, parallel execution not allowed.");
   ```

本节介绍了一个用例：协调 [数据更新](../../workflow/using/coordinating-data-updates.md)。

## 数据库维护 {#database-maintenance}

工作流使用大量占用空间的工作表，如果不进行维护，最终会减慢整个平台的速度。 有关数据库维护的详细信息，请参阅此 [部分](../../production/using/tables-to-maintain.md) 。

通过 **“管理”** >“生产”>“技术工作流”节点可访问的“数据库清除”工作流程 **** ，允许您删除过时的数据以避免数据库呈指数级增长。 该工作流会自动触发，无需用户干预。 请参阅此 [部分](../../production/using/database-cleanup-workflow.md)。

您还可以创建特定的技术工作流来清除不必要的数据占用空间。 请参阅此 [部分](../../production/using/application-objects.md) 和本 [页](#purging-the-logs)。

## 处理暂停的工作流 {#handling-of-paused-workflows}

默认情况下，如果暂停了工作流，则不会清除其工作表。 从内部版本8880起，处于暂停状态的工作流将自动停止并清除其工作表。 此行为将触发如下：

* 自超过7天以来已暂停的工作流在监视功能板（和监视API）中显示为警告，并且会向主管组发送通知。
* 每周触发技术工作流时都 **[!UICONTROL cleanupPausedWorkflows]** 会发生同样的情况。 有关该工作流的更多详细信息，请参 [阅此部分](../../workflow/using/delivery.md)。
* 在4个通知（即默认处于暂停状态的一个月）之后，工作流将无条件停止。 停止工作流后，该工作流中会显示一个日志。 在下一个执行工作流中将清除表 **[!UICONTROL cleanup]** 格

可以通过NmsServer_PausedWorkflowPeriod选项配置这些时段。

将通知工作流主管。 还会通知修改工作流的创建者和最后一个用户。 管理员不会收到通知。

## 根据工作流的状态筛选工作流{#filtering-workflows-status}

“营销活动经典”界面允许您使用预定义视图监视实例上所有工作流的执行&#x200B;**状态**。 要访问这些视图，请打开&#x200B;**[!UICONTROL Administration]**/**[!UICONTROL Audit]**/**[!UICONTROL Workflows Status]**&#x200B;节点。

提供以下视图：

* **[!UICONTROL Running]**：列出所有正在运行的工作流。
* **[!UICONTROL Paused]**：列出所有已暂停的工作流。
* **[!UICONTROL Failed]**：列出所有失败的工作流。
* **[!UICONTROL Start Pending]**：列出正在等待operationMgt进程启动的所有工作流。 此视图仅对&#x200B;**Marketing campaigns包可用**(请参阅安装 [Campaign标准包](../../installation/using/installing-campaign-standard-packages.md))。

![](assets/workflow-monitoring-views.png)

默认情况下，这些视图可在文件夹中&#x200B;**[!UICONTROL Audit]**&#x200B;访问。 但是，您可以在文件夹树中选择的位置重新创建它们。 这样，无管理权的标准用户就可以使用它们。

为此，请执行以下操作：

1. 右键单击要添加视图的文件夹。
1. 在 **[!UICONTROL Add new folder]**/**[!UICONTROL Administration]**&#x200B;中，选择要添加的视图。
1. 将文件夹添加到树中后，请确保将其配置为视图，以便显示所有工作流，无论其源文件夹是什么。有关如何配置视图的详细信息，请参阅 [此部分](../../platform/using/access-management.md#adding-folders-and-creating-views)。

除了这些视图之外，您还可以设置过滤器文件夹，以便根据工作流的执行状态过滤工作流列表。 操作步骤：

1. 访问工作流类型文件夹，然后选择 **[!UICONTROL Filters]** /菜 **[!UICONTROL Advanced filter]** 单。
1. 配置过滤器，使工作流的字 **[!UICONTROL @status]** 段等于您选择的状态。
1. 保存过滤器并命名。 然后，过滤器列表中将直接提供该选项。

![](assets/workflow-monitoring-filter.png)

有关详细信息，请参阅以下各节：

* [创建高级过滤器](../../platform/using/creating-filters.md#creating-an-advanced-filter)
* [保存过滤器](../../platform/using/creating-filters.md#saving-a-filter)
