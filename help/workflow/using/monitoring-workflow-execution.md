---
title: 监控工作流执行
seo-title: 监控工作流执行
description: 监控工作流执行
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '2001'
ht-degree: 0%

---


# 监控工作流执行 {#monitoring-workflow-execution}

本节介绍如何监控工作流的执行。

此部分还提供有关如何创建工作流的用例，该工作流允许您监视“已暂停”、“已停止”或“有错误”的工作流集的 [状态](../../workflow/using/supervising-workflows.md#supervising-workflows)。

此外，实例的管理员可以使用审 **核跟踪** ，检查活动和对工作流所做的最后修改，即工作流的状态。 For more on this, refer to the [dedicated section](../../production/using/audit-trail.md).

本页介绍了监视不同活动过程的其 [他方法](../../production/using/monitoring-guidelines.md)。

## 显示进度 {#displaying-progress}

您可以使用工具栏中相应的图标显示进度来监视执行情况。

通过 **[!UICONTROL Display progress information]** 该图标，可在执行屏幕中显示状态和活动结果。

![](assets/s_user_segmentation_toolbar_progr.png)

选择此选项后，已执行活动以蓝色显示，待处理活动闪烁，警告以橙色显示，错误以红色显示。 此选项还显示活动在其出站过渡上的结果，后跟活动属性中定义的结果标签，以及作业的持续时间（如果超过一秒）

![](assets/s_user_segmentation_results.png)

## 显示日志 {#displaying-logs}

日志包含工作流的历史记录或审计跟踪。 它注册所有用户操作、执行的所有操作和遇到的错误。 您可以：

* 在详细 **[!UICONTROL Tracking]** 信息中选择选项卡。 此列表包含所有工作流消息。

   ![](assets/new-workflow-display-log-tab.png)

* 按活动过滤日志消息。 为此，请单 **[!UICONTROL Display the tasks and the log]** 击图上方的工具栏，以显示图下 **[!UICONTROL Log]** 方 **[!UICONTROL Tasks]** 的选项卡和选项卡。 选择活动以视图所有相关消息。 未选择列表时，此活动包含所有消息。

   ![](assets/new-workflow-display-log-activity.png)

   >[!NOTE]
   >
   >单击图背景以取消选择所有元素。

* 仅视图链接到给定任务的消息。 为此，请选择选 **[!UICONTROL Tasks]** 项卡，然后在图中选择活动以限制列表。 多次单击任务以显示信息；窗口中的最后一个选项卡包含日志。

   ![](assets/new-workflow-display-tasks-activity.png)

   通过 **[!UICONTROL Details...]** 该按钮可显示有关活动执行的所有附加信息。 例如，您可以视图验证运算符，如果适用，还可以在审批过程中输入注释，如下例所示：

   ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>重新启动工作流时不会清除日志。 所有留言都保留。 如果要放弃先前执行中的消息，则必须清除历史记录。

日志显示与定位工作流列表相关的执行消息的时间顺序活动。

* 定位活动的日志

   执行定位活动后，单击选 **[!UICONTROL Tracking]** 项卡以视图执行跟踪。

   ![](assets/s_user_segmentation_journal.png)

   将显示所有活动消息：活动执行以及警告或错误。

* 活动日志

   您还可以视图执行日志和每个活动的详细信息。 有两种方法可以实现此目的：

   1. 选择目标活动并单击 **[!UICONTROL Display the tasks and the log]** 图标。

      ![](assets/s_user_segmentation_show_logs.png)

      图的下部显示两个选项卡：日志和任务。

      在图中选择的活动充当日志和任务列表上的过滤器。

      ![](assets/s_user_segmentation_logs.png)

   1. 右键单击目标活动并选择 **[!UICONTROL Display logs]**。

      ![](assets/s_user_segmentation_logs_menu.png)

      日志显示在单独的窗口中。

## 清除日志 {#purging-the-logs}

工作流历史记录不会自动清除：默认情况下，所有消息都保留。 可以通过菜单或单 **[!UICONTROL File > Actions]** 击列表上方工 **[!UICONTROL Actions]** 具栏中的按钮来清除历史记录。 选择 **[!UICONTROL Purge history]**。菜单中的可用选 **[!UICONTROL Actions]** 项在“操作”工具 [栏部分有详细](../../workflow/using/starting-a-workflow.md) 。

![](assets/purge_historique.png)

## 工作表和工作流模式 {#worktables-and-workflow-schema}

该工作流传达了可通过某些活动处理的工作表。 Adobe Campaign允许您通过数据管理活动修改、重命名和扩充工作流工作表的列，例如根据客户的需要使这些列与命名符对齐，以收集有关合同共同受益人的其他信息，等等。

还可以在各种工作维之间创建链接并定义维更改。 例如，对于记录在数据库中的每个合同，请向主持人寻址，并在附加信息中使用共同持有人数据。

当工作流被钝化时，工作流的工作表会被自动删除。 如果要保留工作表，请通过列表将其保存在活动 **[!UICONTROL List update]** 中(请参 [阅列表更新](../../workflow/using/list-update.md))。

## 管理错误 {#managing-errors}

出错时，工作流暂停，发生错误时执行的活动闪烁红色。 在工作流概述(**[!UICONTROL Monitoring]** Universe > **[!UICONTROL Workflows]** link)中，您只能显示有错误的工作流，如下所示。

![](assets/wf-global-view_filter_only_errors.png)

在Adobe Campaign资源管理器中，默认情况下，工作流列表 **[!UICONTROL Failed]** 显示一列。

![](assets/wf-explorer_errors_col.png)

当工作流出错时，只要其电子邮件地址列在其用户档案中，属于工作流监督组的操作员就会通过电子邮件通知。 此组会在工作流属 **[!UICONTROL Supervisor(s)]** 性的字段中选中。

![](assets/wf-properties_select-supervisors.png)

通知内容在默认模板 **[!UICONTROL Workflow manager notification]** 中配置：此模板会在工作流属 **[!UICONTROL Execution]** 性的选项卡中选中。 通知显示错误工作流的名称和相关任务。

通知示例：

![](assets/wf-notification_error-msg.png)

通过该链接，您可以在Web模式下访问Adobe Campaign控制台，并在登录后使用错误工作流。

![](assets/wf-notification_error-console.png)

您可以配置工作流，以便在出错时不暂停并继续执行。 为此，请编辑工 **[!UICONTROL Properties]** 作流，并在 **[!UICONTROL Error management]** 部分中 **[!UICONTROL Ignore]** 选择字段中的 **[!UICONTROL In case of error]** 选项。 然后，您可以指定在暂停进程之前可以忽略的连续错误数。

在这种情况下，错误任务被中止。 此模式特别适用于设计为稍后重新尝试活动（定期操作）的工作流。

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>您可以对每个活动单独应用此配置。 为此，请编辑活动属性，并在选项卡中选择错误管理 **[!UICONTROL Advanced]** 模式。

有关工作流执行故障排除的详细信息，请参 [阅专用部分](../../production/using/workflow-execution.md)。

## 处理错误 {#processing-errors}

关于活动, **[!UICONTROL Process errors]** 该选项显示在生成错误时将启用的特定过渡。 在这种情况下，工作流不会进入错误模式并继续执行。

考虑到的错误是文件系统错误（无法移动文件、无法访问目录等）。

此选项不处理与活动配置相关的错误，即无效值。 与错误配置相关的错误将不启用此过渡（目录不存在等）。

如果工作流已暂停（手动或在出错后自动），则按 **[!UICONTROL Start]** 钮将在停止工作流的位置重新启动该工作流执行。 将重新执行错误活动(或暂停的活动)。 以前的活动不会重新执行。

要重新执行所有工作流活动，请使用 **[!UICONTROL Restart]** 按钮。

如果修改已执行的活动，则在重新启动工作流执行时，不会考虑更改。

如果修改未执行的活动，则在重新启动工作流执行时会考虑这些数据。

如果修改已暂停的活动，则在重新启动工作流时无法正确考虑更改。

如果可能，我们建议在进行修改后完全重新启动工作流。

## 实例监督 {#instance-supervision}

通过 **[!UICONTROL Instance supervision]** 该页面可以视图Adobe Campaign服务器活动，并显示出工作流和投放的列表，但有错误。

要访问此页，请转到“ **[!UICONTROL Monitoring]** 宇宙”并单击 **[!UICONTROL General view]** 链接。

![](assets/wf-monitoring_from-homepage.png)

要显示所有工作流，请单击 **[!UICONTROL Workflows]** 链接。 使用下拉列表根据工作流的状态显示平台中的数据。

![](assets/wf-monitoring_edit-wf.png)

单击有错误的工作流上的链接，以打开并视图其日志。

![](assets/wf-monitoring_edit-task-wf.png)

## 防止同时执行多个执行 {#preventing-simultaneous-multiple-executions}

单个工作流可以同时运行多个执行。 在某些情况下，您应该防止这种情况发生。

例如，您可以让调度程序每小时触发工作流执行，但有时整个工作流的执行需要超过一小时。 如果工作流已在运行，您可能希望跳过执行。

如果您在工作流的开始处有信号活动，则在工作流正在运行时，您可能希望跳过该信号。

一般原则如下：

![](assets/workflow-reentrancy-protection-principle.png)

解决方案是使用实例变量。 实例变量由工作流的所有并行执行共享。

以下是一个简单的测试工作流：

![](assets/wkf_simultaneous_execution1.png)

每 **[!UICONTROL Scheduler]** 分钟都会触发事件。 以下 **[!UICONTROL Test]** 活动将测试 **isRunning实例** 变量，以决定是否继续执行：

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning是** 为此示例选择的变量名称。 这不是内置变量。

紧接在yes分支 **[!UICONTROL Test]** 后的 **活动** ，必须在其初始化脚本中设置 **实例变量**:

```
instance.vars.isRunning = true
```

yes分支中的最后一个 **活动** ，必须在其初始化脚本中将变量还 **原为false**:

```
instance.vars.isRunning = false
```

请注意：

* 您可以通过工作流属性中的变量选项卡 **检查实** 例变量的当 **前值**。
* 重新启动工作流时会重置实例变量。
* 在JavaScript中，未定义的值在测试中为false，允许在初始化实例变量之前测试该实例变量。
* 您可以通过向“no”结束的初始化脚本添加日志记录指令来监视因此机制未处理的活动。

   ```
   logInfo("Workflow already running, parallel execution not allowed.");
   ```

本节介绍了一个用例： [协调数据更新](../../workflow/using/coordinating-data-updates.md)。

## 数据库维护 {#database-maintenance}

工作流使用大量占用空间的工作表，如果不进行维护，最终会减慢整个平台的速度。 有关数据库维护的详细信息，请参 [阅本节](../../production/using/tables-to-maintain.md) 。

通过 **“管理** ”>“生产”>“技术工作流” **节点可访问的“清理”工作流** ，可删除过时的数据，以避免数据库呈指数级增长。 工作流会自动触发，无需用户干预。 Refer to this [section](../../production/using/database-cleanup-workflow.md).

您还可以创建特定技术工作流来清除不必要的数据占用空间。 请参阅本 [部分](../../production/using/application-objects.md) 和本 [页](#purging-the-logs)。

## 处理暂停的工作流 {#handling-of-paused-workflows}

默认情况下，如果工作流已暂停，则不会清除其工作表。 从内部版本8880起，处于暂停状态的工作流将自动停止并清除其工作表。 此行为按如下方式触发：

* 自7天以来已暂停的工作流在监视仪表板（和监视API）中显示为警告，并且会向主管组发送通知。
* 每周触发技术工作流时都 **[!UICONTROL cleanupPausedWorkflows]** 会发生同样的情况。 有关此工作流的详细信息，请参 [阅此部分](../../workflow/using/delivery.md)。
* 4个通知后（即默认处于暂停状态的一个月），工作流将无条件停止。 停止工作流后，该工作流中会显示日志。 在下一个执行工作流中将清除表 **[!UICONTROL cleanup]** 格

可通过NmsServer_PausedWorkflowPeriod选项配置这些句点。

将通知工作流监管者。 同时还会通知修改工作流的创建者和最后一个用户。 管理员不会收到通知。

## 根据工作流的状态过滤数据 {#filtering-workflows-status}

Campaign Classic界面允许您使用预定义的视图监视实例上所有工作流的执行&#x200B;**状态**。 要访问这些视图，请打&#x200B;**[!UICONTROL Administration]**&#x200B;开/**[!UICONTROL Audit]**/**[!UICONTROL Workflows Status]**&#x200B;节点。

提供以下视图:

* **[!UICONTROL Running]**:列表所有正在运行的工作流。
* **[!UICONTROL Paused]**:列表所有已暂停的工作流。
* **[!UICONTROL Failed]**:列表所有失败的工作流。
* **[!UICONTROL Start Pending]**:列表正在等待operationMgt进程启动的所有工作流。 此视图仅可用于&#x200B;**Marketing活动包**(请参阅 [安装活动标准包](../../installation/using/installing-campaign-standard-packages.md))。

![](assets/workflow-monitoring-views.png)

默认情况下，这些视图可在文件夹中&#x200B;**[!UICONTROL Audit]**&#x200B;访问。 但是，您可以在文件夹树中选择的位置重新创建它们。 这样，无管理权的标准用户就可以使用它们。

为此，请执行以下操作：

1. 右键单击要添加视图的文件夹。
1. 在 **[!UICONTROL Add new folder]**/**[!UICONTROL Administration]**&#x200B;中，选择要添加的视图。
1. 将文件夹添加到树后，请确保将其配置为视图，以便显示所有工作流(无论其来源文件夹是什么)。有关如何配置视图的详细信息，请参 [阅此部分](../../platform/using/access-management.md#adding-folders-and-creating-views)。

除了这些视图之外，您还可以设置过滤器文件夹，以便根据工作流的执行状态过滤列表。 操作步骤：

1. 访问工作流类型文件夹，然后选择 **[!UICONTROL Filters]** /菜 **[!UICONTROL Advanced filter]** 单。
1. 配置过滤器，使工作流的 **[!UICONTROL @status]** 字段等于您选择的状态。
1. 保存并命名过滤器。 然后，它将直接从过滤器列表访问。

![](assets/workflow-monitoring-filter.png)

有关详细信息，请参阅以下部分：

* [创建高级过滤器](../../platform/using/creating-filters.md#creating-an-advanced-filter)
* [保存过滤器](../../platform/using/creating-filters.md#saving-a-filter)
