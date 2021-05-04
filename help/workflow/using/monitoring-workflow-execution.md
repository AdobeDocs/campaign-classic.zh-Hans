---
solution: Campaign Classic
product: campaign
title: 监控工作流执行
description: 监控工作流执行
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: d589180b-8e1d-4149-9b16-3f541018a41f
translation-type: tm+mt
source-git-commit: d5579fa1928888a088fe99b685f4d12bf2bde25b
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# 监控工作流执行 {#monitoring-workflow-execution}

本节介绍如何监控工作流的执行。

[此部分](../../workflow/using/supervising-workflows.md#supervising-workflows)还提供了有关如何创建工作流以监视一组“已暂停”、“已停止”或“有错误”的工作流的状态的用例。

此外，实例的管理员可以使用&#x200B;**审核跟踪**&#x200B;检查活动和对工作流所做的最后修改，即工作流的状态。 有关详细信息，请参阅[专用部分](../../production/using/audit-trail.md)。

[本页](../../production/using/monitoring-guidelines.md)中提供了监控不同活动过程的其他方法。

## 显示进度{#displaying-progress}

您可以使用工具栏中相应的图标显示进度来监视执行情况。

通过&#x200B;**[!UICONTROL Display progress information]**&#x200B;图标，可在执行屏幕中显示状态和活动结果。

![](assets/s_user_segmentation_toolbar_progr.png)

选中此选项时，已执行的活动以蓝色显示，挂起的活动闪烁，警告以橙色显示，错误以红色显示。 此选项还显示活动在其出站过渡上的结果，后跟活动属性中定义的结果标签，以及作业持续时间（如果超过一秒）

![](assets/s_user_segmentation_results.png)

## 显示日志{#displaying-logs}

日志包含工作流的历史记录或审计跟踪。 它注册所有用户操作、执行的所有操作和遇到的错误。 您可以：

* 在详细信息中选择&#x200B;**[!UICONTROL Tracking]**&#x200B;选项卡。 此列表包含所有工作流消息。

   ![](assets/new-workflow-display-log-tab.png)

* 按活动过滤日志消息。 要执行此操作，请单击图上方工具栏上的&#x200B;**[!UICONTROL Display the tasks and the log]**，以便在图下方显示&#x200B;**[!UICONTROL Log]**&#x200B;和&#x200B;**[!UICONTROL Tasks]**&#x200B;选项卡。 选择活动以视图所有相关消息。 此列表包含未选择活动时的所有消息。

   ![](assets/new-workflow-display-log-activity.png)

   >[!NOTE]
   >
   >单击图背景以取消选择所有元素。

* 仅视图链接到给定任务的消息。 要执行此操作，请选择&#x200B;**[!UICONTROL Tasks]**&#x200B;选项卡，然后在图中选择活动以限制列表。 多次单击任务以显示信息；窗口中的最后一个选项卡包含日志。

   ![](assets/new-workflow-display-tasks-activity.png)

   通过&#x200B;**[!UICONTROL Details...]**&#x200B;按钮可显示有关活动执行的所有附加信息。 例如，您可以视图验证运算符，如果适用，还可以在审批过程中输入注释，如下例所示：

   ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>重新启动工作流时不会清除日志。 所有留言都保留。 如果要放弃上次执行中的消息，则必须清除历史记录。

该日志显示与定位工作流活动相关的执行消息的时间列表。

* 定位活动的日志

   执行定位活动后，单击&#x200B;**[!UICONTROL Tracking]**&#x200B;选项卡以视图执行跟踪。

   ![](assets/s_user_segmentation_journal.png)

   将显示所有活动消息：执行的活动以及警告或错误。

* 活动日志

   您还可以视图执行日志和每个活动的详细信息。 有两种方法可以实现：

   1. 选择目标活动，然后单击&#x200B;**[!UICONTROL Display the tasks and the log]**&#x200B;图标。

      ![](assets/s_user_segmentation_show_logs.png)

      图的下部显示两个选项卡：日志和任务。

      在图中选择的活动在日志和任务列表上充当过滤器。

      ![](assets/s_user_segmentation_logs.png)

   1. 右键单击目标活动，然后选择&#x200B;**[!UICONTROL Display logs]**。

      ![](assets/s_user_segmentation_logs_menu.png)

      日志显示在单独的窗口中。

## 清除日志{#purging-the-logs}

工作流历史记录不会自动清除：默认情况下，所有消息都保留。 可以通过&#x200B;**[!UICONTROL File > Actions]**&#x200B;菜单或单击列表上方工具栏中的&#x200B;**[!UICONTROL Actions]**&#x200B;按钮来清除历史记录。 选择 **[!UICONTROL Purge history]**。**[!UICONTROL Actions]**&#x200B;菜单中可用的选项在[“操作”工具栏](../../workflow/using/starting-a-workflow.md)部分有详细说明。

![](assets/purge_historique.png)

## 工作表和工作流模式{#worktables-and-workflow-schema}

该工作流传达了可通过某些活动操作的工作表。 Adobe Campaign使您能够通过数据管理活动修改、重命名和扩充工作流工作表的列，例如，根据客户的需要将这些列与术语对齐，以收集有关合同的共同受益人的其他信息，等等。

还可以在各种工作维之间创建链接并定义维更改。 例如，对于记录在数据库中的每个合同，向主持人地址，并在附加信息中使用共同持有人数据。

当工作流被钝化时，工作流的工作表会自动删除。 如果希望保留工作表，请通过&#x200B;**[!UICONTROL List update]**&#x200B;活动将其保存在列表中(请参阅[列表更新](../../workflow/using/list-update.md))。

## 管理错误{#managing-errors}

发生错误时，工作流暂停，当发生错误时正在执行的活动闪烁红色。 在工作流概述的&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡 — **[!UICONTROL Workflows]**&#x200B;链接下，您只能显示有错误的工作流，如下所示。

![](assets/wf-global-view_filter_only_errors.png)

在Adobe Campaign资源管理器中，默认情况下，工作流列表显示&#x200B;**[!UICONTROL Failed]**&#x200B;列。

![](assets/wf-explorer_errors_col.png)

当工作流出错时，只要其电子邮件地址列在其用户档案中，属于工作流监督组的操作员就会通过电子邮件通知。 此组在工作流属性的&#x200B;**[!UICONTROL Supervisor(s)]**&#x200B;字段中处于选中状态。

![](assets/wf-properties_select-supervisors.png)

通知内容在&#x200B;**[!UICONTROL Workflow manager notification]**&#x200B;默认模板中配置：此模板在工作流属性的&#x200B;**[!UICONTROL Execution]**&#x200B;选项卡中被选中。 通知显示错误工作流的名称和相关任务。

通知示例：

![](assets/wf-notification_error-msg.png)

通过该链接，您可以在Web模式下访问Adobe Campaign控制台，并在登录后使用错误工作流。

![](assets/wf-notification_error-console.png)

您可以配置工作流，以便它不会暂停并在出现错误时继续执行。 为此，请编辑工作流&#x200B;**[!UICONTROL Properties]**，并在&#x200B;**[!UICONTROL Error management]**&#x200B;部分的&#x200B;**[!UICONTROL In case of error]**&#x200B;字段中选择&#x200B;**[!UICONTROL Ignore]**&#x200B;选项。 然后，您可以指定在暂停进程之前可忽略的连续错误数。

在这种情况下，错误任务被中止。 此模式特别适用于设计为稍后重新尝试活动（定期操作）的工作流。

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>您可以对每个活动单独应用此配置。 要执行此操作，请编辑活动属性，并在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中选择错误管理模式。

有关工作流执行故障排除的详细信息，请参阅[专用部分](../../production/using/workflow-execution.md)。

## 处理错误{#processing-errors}

关于活动,**[!UICONTROL Process errors]**&#x200B;选项显示特定过渡，如果生成错误，将启用该选项。 在这种情况下，工作流不会进入错误模式并继续执行。

考虑到的错误是文件系统错误（无法移动文件、无法访问目录等）。

此选项不处理与活动配置相关的错误，即无效值。 与错误配置相关的错误将不启用此过渡（目录不存在等）。

如果暂停了工作流（手动或在出错后自动），**[!UICONTROL Start]**&#x200B;按钮将在停止工作流的位置重新启动工作流执行。 将重新执行错误活动(或暂停活动)。 不会重新执行以前的活动。

要重新执行所有工作流活动，请使用&#x200B;**[!UICONTROL Restart]**&#x200B;按钮。

如果修改已执行的活动，则在重新启动工作流执行时，不会考虑这些更改。

如果修改未执行的活动，则在重新启动工作流执行时，会考虑这些操作。

如果修改暂停的活动，则在重新启动工作流时无法正确考虑更改。

如果可能，我们建议在进行修改后完全重新启动工作流。

## 实例监视{#instance-supervision}

在&#x200B;**[!UICONTROL Instance supervision]**&#x200B;页面中，可以视图Adobe Campaign服务器活动，并显示出工作流和投放的列表，但有错误。

要访问此页，请转到&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL General view]**&#x200B;链接。

![](assets/wf-monitoring_from-homepage.png)

要显示所有工作流，请单击&#x200B;**[!UICONTROL Workflows]**&#x200B;链接。 使用下拉列表根据工作流的状态在平台中显示这些应用程序。

![](assets/wf-monitoring_edit-wf.png)

单击存在错误的工作流上的链接，以打开并视图其日志。

![](assets/wf-monitoring_edit-task-wf.png)

## 防止同时执行多个{#preventing-simultaneous-multiple-executions}

单个工作流可以同时运行多个执行。 在某些情况下，您应防止这种情况发生。

例如，您可以让调度程序每小时触发一次工作流执行，但有时整个工作流的执行需要超过一小时。 如果工作流已在运行，您可能希望跳过执行。

如果您在工作流的开始有信号活动，则在工作流正在运行时，您可能希望跳过该信号。

一般原则如下：

![](assets/workflow-reentrancy-protection-principle.png)

解决方案是使用实例变量。 实例变量由工作流的所有并行执行共享。

以下是一个简单的测试工作流程：

![](assets/wkf_simultaneous_execution1.png)

**[!UICONTROL Scheduler]**&#x200B;每分钟触发一个事件。 以下&#x200B;**[!UICONTROL Test]**&#x200B;活动将测试&#x200B;**isRunning**&#x200B;实例变量，以决定是否继续执行：

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning** 是为此示例选择的变量名称。这不是内置变量。

紧接&#x200B;**yes**&#x200B;分支中&#x200B;**[!UICONTROL Test]**&#x200B;的活动必须在其&#x200B;**初始化脚本**&#x200B;中设置实例变量：

```
instance.vars.isRunning = true
```

**yes**&#x200B;分支中的最后一个活动必须在其&#x200B;**初始化脚本**&#x200B;中将变量还原为false:

```
instance.vars.isRunning = false
```

请注意：

* 您可以通过工作流&#x200B;**属性**&#x200B;中的&#x200B;**变量**&#x200B;选项卡检查实例变量的当前值。
* 重新启动工作流时会重置实例变量。
* 在JavaScript中，未定义的值在测试中为false，允许在初始化实例变量之前测试该实例变量。
* 您可以通过向“no”结尾的初始化脚本中添加日志记录指令来监视因此机制未处理的活动。

   ```
   logInfo("Workflow already running, parallel execution not allowed.");
   ```

本节介绍了一个用例：[协调数据更新](../../workflow/using/coordinating-data-updates.md)。

## 数据库维护 {#database-maintenance}

工作流使用大量工作表，占用空间，如果不进行维护，最终会减慢整个平台的速度。 有关数据库维护的详细信息，请参阅此[部分](../../production/using/tables-to-maintain.md)。

通过&#x200B;**“管理”>“生产”>“技术工作流”**&#x200B;节点可访问&#x200B;**“数据库清理”**&#x200B;工作流，可删除过时的数据以避免数据库的指数级增长。 工作流会自动触发，无需用户干预。 请参阅此[部分](../../production/using/database-cleanup-workflow.md)。

您还可以创建特定技术工作流来清除不必要的数据占用空间。 请参阅此[部分](../../production/using/application-objects.md)和此[页面](#purging-the-logs)。

## 处理暂停的工作流{#handling-of-paused-workflows}

默认情况下，如果暂停工作流，则从不清除其工作表。 从内部版本8880起，处于暂停状态太长的工作流将自动停止并清除其工作表。 此行为将触发如下：

* 自7天以来已暂停的工作流在监视仪表板（和监视API）中显示为警告，并且会向主管组发送通知。
* 每周触发&#x200B;**[!UICONTROL cleanupPausedWorkflows]**&#x200B;技术工作流时都会发生同样的情况。 有关该工作流的详细信息，请参阅[此部分](../../workflow/using/delivery.md)。
* 在4个通知后（即默认情况下处于暂停状态的一个月），将无条件停止工作流。 日志停止后，将在工作流中显示它。 在下次执行&#x200B;**[!UICONTROL cleanup]**&#x200B;工作流时，将清除这些表

可以通过NmsServer_PausedWorkflowPeriod选项配置这些句点。

将通知工作流监管者。 同时还会通知修改工作流的创建者和最后一个用户。 管理员不会收到通知。

## 根据工作流的状态{#filtering-workflows-status}筛选

Campaign Classic接口允许您使用预定义的&#x200B;**视图**&#x200B;监视实例上所有工作流的执行状态。 要访问这些视图，请打开&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Audit]** / **[!UICONTROL Workflows Status]**&#x200B;节点。

提供以下视图:

* **[!UICONTROL Running]**:列表所有正在运行的工作流。
* **[!UICONTROL Paused]**:列表所有已暂停的工作流。
* **[!UICONTROL Failed]**:列表所有失败的工作流。
* **[!UICONTROL Start Pending]**:列表等待operationMgt进程启动的所有工作流。此视图仅适用于&#x200B;**营销活动**&#x200B;包(请参阅[安装活动内置包](../../installation/using/installing-campaign-standard-packages.md))。

![](assets/workflow-monitoring-views.png)

默认情况下，可在&#x200B;**[!UICONTROL Audit]**&#x200B;文件夹中访问这些视图。 但是，您可以在文件夹树中选择的位置重新创建它们。 这样，无管理权的标准用户就可以使用它们。

要执行此操作：

1. 右键单击要添加视图的文件夹。
1. 在&#x200B;**[!UICONTROL Add new folder]** / **[!UICONTROL Administration]**&#x200B;中，选择要添加的视图。
1. 将文件夹添加到树后，请确保将其配置为视图，以便显示所有工作流(无论其来源文件夹是什么)。有关如何配置视图的详细信息，请参阅[此部分](../../platform/using/access-management-folders.md)。

除了这些视图之外，您还可以设置过滤器文件夹，以允许您根据工作流的执行状态来筛选的列表。 操作步骤：

1. 访问工作流类型文件夹，然后选择&#x200B;**[!UICONTROL Filters]** / **[!UICONTROL Advanced filter]**&#x200B;菜单。
1. 配置过滤器，使工作流的&#x200B;**[!UICONTROL @status]**&#x200B;字段等于您选择的状态。
1. 保存过滤器并命名。 然后，它将直接从过滤器列表可用。

![](assets/workflow-monitoring-filter.png)

有关详细信息，请参阅以下部分：

* [创建高级过滤器](../../platform/using/creating-filters.md#creating-an-advanced-filter)
* [保存过滤器](../../platform/using/creating-filters.md#saving-a-filter)
