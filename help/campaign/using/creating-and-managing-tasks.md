---
title: 创建和管理任务
seo-title: 创建和管理任务
description: 创建和管理任务
seo-description: null
page-status-flag: never-activated
uuid: 1d219ae4-1ca9-42cb-a49e-2b647520bda0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: d71e5ff7-1e81-4c49-9673-c6fae890029b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 创建和管理任务{#creating-and-managing-tasks}

## 关于任务 {#about-tasks}

Adobe Campaign允许您直接在应用程序中创建任务并管理其整个生命周期。 计划和营销活动实施可分为分配给Adobe Campaign运营商或外部服务提供商的任务。 通过此操作模式，您可以创建一个包括所有计划参加者和外部参加者的开放式协作环境。

可以从任务列表或营销活动功能板中创建、查看和监视任务。 还可以在营销计划、计划和营销活动的计划中查看和跟踪它们。

任务会附加到营销活动，并且可以具有相关性，即关联任务。 每个任务都有状态、优先级、估计负载和相关成本。

所有任务都分组在可通过“营销活动”范围访问的 **列表中** 。 For more on this, refer to [Accessing tasks](#accessing-tasks).

它们可以显示在它们所属的程序的计划中。

![](assets/d_ncs_user_tasks_in_planning.png)

## 访问任务 {#accessing-tasks}

### 显示任务 {#displaying-tasks}

任务显示在可通过范围访问的任务列表 **[!UICONTROL Campaigns]** 中。

![](assets/s_ncs_user_task_edit_view.png)

您可以在此处查看连接的操作员的所有任务。

有关详细信息，请参阅任 [务的执行状态和任](#execution-status-of-a-task) 务的进度状态 [](#progress-status-of-a-task)。

### 筛选任务 {#filtering-tasks}

当您显示此视图时，会自动过滤该视图，以便仅显示 **[!UICONTROL operator tasks]**。 您还可以使用窗口上部分的字段过滤任务。

![](assets/s_ncs_user_task_filter_from_view.png)

### 编辑任务 {#editing-tasks}

单击某个任务可对其进行编辑。

![](assets/s_ncs_user_task_edit_from_view.png)

## 创建新任务 {#creating-a-new-task}

要创建任务，请单击“营销活 **[!UICONTROL Tasks]** 动”范围中的链接，然后选择 **[!UICONTROL Create]**。

![](assets/s_ncs_user_task_create_new.png)

至少输入任务的名称，然后选择与之关联的营销活动。 您还必须指定开始日期和结束日期。 这三条信息是必须提供的。

单击 **[!UICONTROL Save]** 以创建任务。

![](assets/s_ncs_user_task_create_simple.png)

您还可以通过营销活动的仪表板创建任务：在这种情况下，它会自动链接到从中创建它的营销活动。

![](assets/s_ncs_user_task_create_new_from_op.png)

创建任务后，该任务会添加到营销活动计划和任务列表中。 要编辑任务，请从计划中选择该任务，或在任务概述中单击其名称，然后单击链 **[!UICONTROL Open]** 接。

![](assets/s_ncs_user_task_edit_simple.png)

要进行配置，您必须指示：

* 管理者和参加者：请参阅 [Manager和参加者](#manager-and-participants)。
* 创建计划：请参阅执 [行计划](#execution-schedule)。
* 承诺成本：请参阅 [费用和收入](#expenses-and-revenues)。

还可以为审阅人(请参阅审阅人 [)和引用的文档(请参阅引用的](#reviewers)文档 [](#documents-referenced))添加广告。

任务生命周期在生命周期中 [有所体现](#life-cycle)。

### 管理者和参加者 {#manager-and-participants}

只有负责任务的操作员才有权关闭任务。

默认情况下，当Adobe Campaign操作员创建任务时，该任务会自动分配给他们。 要选择其他运算符，请使用字 **[!UICONTROL Assigned to]** 段。

![](assets/s_ncs_user_task_edit_simple_general_tab.png)

>[!NOTE]
>
>本节介绍了运营商 [管理](../../platform/using/access-management.md)。

您可以指定执行任务时涉及的操作符。 这些运营商无权关闭任务。 他们只能批准分配给他们的任务。

使用任务工具栏中 **[!UICONTROL Resources]** 的图标选择它们。 单击 **[!UICONTROL Add]** 并选择相关的运算符。

![](assets/s_ncs_user_task_add_resources.png)

单击 **[!UICONTROL Ok]** 并输入使用率：这表示在任务执行期间分配给操作员的负载。 此比率只是一个指示，以百分比表示。

例如，对于将执行计划设置为10天的任务，在10天的工作时间中，将为此任务调动使用率为50%的操作员一半。

对于每个操作员，您可以输入计划的工作量和实际的工作量。 这些持续时间也仅用于信息用途。

可以配置提醒，该提醒将在任务结束日期前自动发送给参与任务的所有操作员。

您可以通过图标查看Adobe Campaign运营商配置 **[!UICONTROL Edit link]** 文件。

![](assets/s_ncs_user_task_edit_resource_profile.png)

运算符控制板允许您检查其工作量（其他正在执行的任务）。

![](assets/s_ncs_user_task_edit_resource_planning.png)

### 审阅者 {#reviewers}

除了参加者之外，您还可以定义在任务被负责人关闭后将审核任务的操作员。 为此，请单 **[!UICONTROL Enable task approval]** 击窗口左下角的选项 **[!UICONTROL Resources]** 。 这可以是单个运算符、一组运算符或运算符列表。

![](assets/s_ncs_user_task_edit_resource_validation.png)

要指定运算符列表，请单击第 **[!UICONTROL Edit...]** 一位审阅者右侧的链接，并根据需要添加任意数量的运算符，如下所示：

![](assets/s_ncs_user_task_edit_resource_operators.png)

您可以在审核者配置窗口的下半部分为任务定义审批计划。 默认情况下，审阅者从提交日期开始有三天时间批准任务。 可以配置提醒，提醒将在批准截止日期之前自动发送给相关运营商。

![](assets/s_ncs_user_edit_op_valid_calendar.png)

负责任务的人员可以自行分配批准任务，即使已指派其他操作员进行批准。 如果尚未定义审阅者，则通知将发送给负责任务的人员。 所有其他具有权限的Adobe Campaign运 **[!UICONTROL Administrator]** 营商也可以批准该任务。 但是，他们不会收到通知。

### 文档引用 {#documents-referenced}

可以将文档和营销资源添加到任务中(有关详细信息，请参阅管 [理营销资源](../../campaign/using/managing-marketing-resources.md))。 为此，请打开任务，然后单击任 **[!UICONTROL Documents]** 务工具栏中的图标。

单 **[!UICONTROL Add]** 击并选择要添加到任务的文档。 对营销资源应用相同的流程。

![](assets/s_ncs_user_task_edit_documents.png)

引用的文档将显示在发送给任务中涉及的操作员的通知中以及任务功能板上。

![](assets/s_ncs_user_task_notification_documents.png)

### 执行计划 {#execution-schedule}

任务的有效期在和字段中 **[!UICONTROL Start]** 指 **[!UICONTROL End]** 示。 调度的负载表示该期间要执行的工作负载。 它以天或小时表示。

>[!NOTE]
>
>任务的生命周期在生命周期中 [表示](#life-cycle)。

该字 **[!UICONTROL Workload performed]** 段还以天数和小时数表示，允许您根据计划的工作量手动更新任务进度。

![](assets/s_ncs_user_task_percentage_done_enter.png)

任 **[!UICONTROL Progress status]** 务的百分比表示根据相关操作员执行的任务自动更新。 可以手动输入。

此信息可在任务功能板中查看。

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

该选项卡也显示在营销活动选项卡中。

![](assets/s_ncs_user_task_percentage_done_from_op.png)

如果任务执行计划结束日期已达到但任务未完成，则任务将完成 **[!UICONTROL Late]**。 还将向警报操作员显示警告消息。

有关详细信息，请参阅任 [务的进度状态](#progress-status-of-a-task)。

### 开支和收入 {#expenses-and-revenues}

您可以为每个任务定义相关费用和预测收入。 这些任务将计算并合并到任务所附加的营销活动。

要指定此信息，请单击任 **[!UICONTROL Expenses and revenue]** 务工具栏中的图标。

![](assets/s_ncs_user_task_edit_costs.png)

默认情况下，已支付的预算是任务所附加到的营销活动的预算。 它显示在任务详细信息中。

>[!NOTE]
>
>有关费用和预算的更多信息，请参 [阅成本承诺、计算和费用](../../campaign/using/controlling-costs.md#cost-commitment--calculation-and-charging)。

在此窗口中，您还可以定义要达到的目标。 目标以任务的预测收入表示。

### 服务提供商 {#service-providers}

外部服务提供商可以参与任务的管理。

为此，请编辑任务属性并选择相关的服务提供商。 与服务提供商关联的成本类别将自动列在窗口的中央部分。

有关详细信息，请参 [阅创建服务提供商及其成本类别](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

选择与执行任务相关的成本类别。 为此，请选择成本类型，并根据需要添加附加费金额。

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>管理预算及成本之方法于控制成本 [中呈列](../../campaign/using/controlling-costs.md)。

选择服务提供商后，该服务提供商会显示在任务功能板中：

![](assets/s_ncs_user_task_supplier_view.png)

### 延迟任务 {#late-tasks}

如果任务已到达结束日期，且状态未更改为，则任务会迟到 **[!UICONTROL Finished]**。 默认情况下，任务延迟时不会警告任何运算符。 您可以配置通知电子邮件的发送方式：即使所有运营商不参与任务，也可以通知它们。

转到框 **[!UICONTROL Resources]** 并将运算符添加到字 **[!UICONTROL Assignation]** 段。 要通知多个人，请选择一组运营商。

![](assets/mrm_task_alert_if_late.png)

### 初始通知 {#initial-notifications}

当您在将来创建或修改具有开始日期的任务时，Adobe Campaign会建议向负责该任务的人员发送电子邮件，告知他们该任务何时开始。

![](assets/mrm_task_first_notif.png)

但是，如果您正在创建的任务离开时间很长，则最好在任务开始之前安排发送通知。 例如，如果任务在一个月内开始，您可以在任务开始前一周通知负责该任务的人员。

要计划通知，请转到框 **[!UICONTROL Resources]** 并使用字 **[!UICONTROL Initial notification]** 段。

![](assets/mrm_task_alert_before.png)

* 对于营销活动中的任务，请选择特定的日期和时间。
* 对于营销活动模板中的任务，通知时间表示为任务开始前的剩余时间（例如，如果您在字段中输入2d，则电子邮件将在任务开始日期前2天发送）。 **[!UICONTROL Initial notification]**

如果您已计划通知，则在保存任务时，Adobe Campaign会提供通知以立即发送。 您可以决定发送它，但这不会替换计划的通知。

### 链接到程序的任务 {#task-linked-to-a-program}

您可以直接在程序中创建任务，以管理与其整体组织而非特定营销活动相关的操作（例如，会议，讨论计划内即将进行的营销活动的主题）。 该任务将显示在程序计划中。

要创建直接链接到程序的任务，请执行以下操作：

1. 打开程序计划：在主页上，转到 **[!UICONTROL Campaigns > Browse > Other choices > Programs]**。 整个程序计划将在窗口的右侧部分打开。
1. 在计划中，单击所需的程序：一个窗子里出现了那个程序。
1. 在此窗口中，单击 **[!UICONTROL Open]**。 此时将打开程序计划。
1. 单击右 **[!UICONTROL Add]** 侧计划上方的按钮，然后单击 **[!UICONTROL Add a task]**。

![](assets/mrm_task_create_from_prg.png)

### 运营商可用性 {#operator-availability}

在任务功能板中，操作员姓名旁边的图标表示他们在任务涵盖的时间段内已经处理了其他任务或事件。 (操作员负责或参与的任务：他显示在字 **[!UICONTROL Assigned to]** 段或任务框 **[!UICONTROL Resources]** 中)。

![](assets/mrm_task_alert_operator_busy.png)

### 工作流中的任务 {#task-in-a-workflow}

在营销活 **[!UICONTROL Task]** 动工作流中使用元素使您能够根据任务是否已批准来定义两种方案。

![](assets/mrm_task_in_workflow.png)

在营销活动工作流中， **[!UICONTROL Task]** 活动位于选项卡 **[!UICONTROL Flow control]** 中。

## 任务类型 {#types-of-task}

通过营销活动创建任务时，可以创建特定任务。 任务类型在选定的模板中定义。

![](assets/s_ncs_user_task_select_template.png)

可以计划以下任务：

* **[!UICONTROL Control task]**, refer to [Control tasks](#control-tasks),
* **[!UICONTROL Marketing resource creation task]**, refer to [Grouping task](#grouping-task),
* **[!UICONTROL Grouping task]**, refer to [Grouping task](#grouping-task),
* **[!UICONTROL Notification task]**, refer to [Notification task](#notification-task).

>[!NOTE]
>
>**[!UICONTROL Control task]** 而且 **[!UICONTROL Grouping]** 只能通过营销 **活动控制板** 创建任务。\
>它们显示在向其分配它们的操作员的任务图中。 请参阅 [访问任务](#accessing-tasks)。

### 控制任务 {#control-tasks}

A链 **[!UICONTROL Control task]** 接到交付批准：批准定位、内容、提取文件、预算或证明。

![](assets/s_ncs_user_task_new_control.png)

创建任务后，该任务即添加到营销活动功能板。

![](assets/s_ncs_user_task_edit_from_board.png)

然后，您可以编辑它并指定其参数。

### 营销资源创建任务 {#marketing-resource-creation-task}

营销资源创建任务可用于管理营销资源的创建和发布。 如果您通过任务而不是通过资源本身管理资源，则可以：

* 通过营销活动控制资源创建过程。
* 在计划中查看资源创建过程。
* 管理资源创建过程（提醒、通知）。
* 计算并控制与资源创建关联的成本。
* 通过任务批准和发布资源（如果启用了相关选项）。

#### 任务与其链接的资源之间的交互 {#interaction-between-the-task-and-its-linked-resource}

营销资源创建任务与与其关联的资源交互。 这意味着：

* 通过任务管理资源创建计划和与其关联的成本。
* 操作员可以处理像正常（下载或上传、锁定和解锁）这样的资源：这不会影响任务。
* 资源审批和发布可以通过以下任务进行：如果启 **[!UICONTROL Publish the marketing resource]** 用此选项，则任务完成后，资源会自动获得批准并发布。 如果未启用此选项，则任务和资源不会交互：对一个不会影响另一个。

   您可以使用一系列链接任务来定义完整的审批周期。 仅选中 **[!UICONTROL Publish the marketing resource]** 最后一个任务的选项：所有任务都需要完成才能发布资源。 此外，当您创建子营销资源任务时，该资源将在子任务中自动选择。

   * **通过资源**:如果您提交资源进行批准或批准，则这些操作不会影响任务。
   * **通过任务**:如果选 **[!UICONTROL Publish the marketing resource]** 中了任务中的选项，则任务完成后，资源会自动获得批准并发布（请参阅上文）。 如果未选中此选项，则任务和资源不会交互：对一个不会影响另一个。

#### 配置营销资源创建任务 {#configuring-a-marketing-resource-creation-task}

审阅任务的人员不必是审阅资源中定义的内容的同一人。 但是，如果选 **[!UICONTROL Publish the marketing resource]** 中了该选项（请参阅下文），则任务审核者在完成任务后将自动批准资源（或者，如果未定义审核者，则授权任务管理者）批准资源内容。

![](assets/mrm_task_asset_creation.png)

在字 **[!UICONTROL Marketing resource]** 段中，定义要通过此任务管理的资源。 您可以：

* 选择现有资源：下拉列表将提供状态为的所有资源 **[!UICONTROL Being edited]**
* 创建资源：单击图 **[!UICONTROL Select the link]** 标，然后单击图 **[!UICONTROL Create]** 标。

通过该 **[!UICONTROL Publish the marketing resource]** 选项，您可以自动发布资源：任务完成后，即 **[!UICONTROL Finished]****[!UICONTROL Published]**&#x200B;使资源既未提交审批也未获得批准，资源的状态也会自动切换到该状态，包括完成任务的审阅人不是资源中定义的内容审阅人。

该 **[!UICONTROL Publish the resource]** 按钮可用，资源发布审阅者会收到通知电子邮件，通知他已准备好发布。 在选项卡 **[!UICONTROL Edit > Tracking]** 中，任务审阅者的审阅和发布会变为可见。 如果已定义资源后处理工作流，则立即执行该工作流。

![](assets/mrm_resource_audit_tab.png)

### 分组任务 {#grouping-task}

通过 **[!UICONTROL Grouping task]** 类型任务，您可以对多个任务进行分组，并同步对其进度和批准的管理。

分组任务没有关联的费用或资源。

分组到分组任务的所有任务都可以在其自己的仪表板上查看。 这样，您就可以过滤任务列表，以仅显示您感兴趣的任务。

分组任务有一个链接，可让您轻松创建分组任务。

要基于分组任务创建分组任务，请转至营销活动功能板，单击分组任务的名称以显示其说明，然后单击 **[!UICONTROL Add a task]**。

![](assets/mrm_task_grouped_create.png)

但是，如果已创建要链接到分组任务的任务，则可以通过框的字段 **[!UICONTROL Linked to]** 执行此操作 **[!UICONTROL Properties]** 。

![](assets/s_ncs_user_task_group_with.png)

### 通知任务 {#notification-task}

通知任务使您能够安排向操作员、一组操作员、服务提供商等发送电子邮件。 这样，您就可以计划提醒，例如通知某个营销活动即将完成，或在营销活动开始之前发送文档，以便运营商准备。 这意味着您可以跟踪营销活动或计划中的通信，并更密切地关注所执行的操作。

#### 生命周期 {#life-cycle}

通知任务不需要批准。 这意味着他们的生命周期比标准任务的生命周期要简单：

![](assets/mrm_task_notif_lifecycle.png)

通知任务可以具有以下状态：

* **[!UICONTROL Scheduled]** 直到电子邮件发送
* **[!UICONTROL In progress]** 发送电子邮件后，直到到达结束日期
* **[!UICONTROL Finished]** 到达结束日期后。

#### 配置 {#configuration}

![](assets/mrm_task_notif_dashboard.png)

在创建过程中，必须在任务中输入以下元素：

* **[!UICONTROL Assigned to]** :接收电子邮件的运营商或运营商组。 如果在发送电子邮件后重新分配任务，则该电子邮件将不会发送给新操作员（要执行此操作，您需要重新初始化任务并更改其开始日期）。
* **任务开始日期**:发送通知电子邮件的日期。 此日期必须在将来记录任务时发生。
* **任务结束日期**:任务状态更改为的日期 **[!UICONTROL Finished]**。 默认情况下，结束日期与开始日期相同。 但是，为任务分配持续时间允许您象征操作员在计划中必须执行的时间量（如果需要）。
* **[!UICONTROL Description]** :此处输入的文本将显示在通知电子邮件的正文中。

   ![](assets/mrm_task_notif_dashboard_msg.png)

您可以向任务和通知电子邮件中添加附件。 要执行此操作，请单 **[!UICONTROL Documents]** 击右上角工具栏中的图标。

## 生命周期 {#life-cycle-1}

### 任务之间的链接 {#links-between-tasks}

每个 **[!UICONTROL Properties]** 任务中的按钮使您能够定义营销活动中任务之间的链接。 您可以使用分组任务将任务拆分为子任务(请参阅 [链接的任务](#linked-tasks))，或定义任务之间的依赖关系(请参阅 [分组任务](#grouping-tasks))。

#### 链接任务 {#linked-tasks}

使用字 **[!UICONTROL Linked task]** 段将任务与分组任务关联。 请参 [阅任务类型](#types-of-task)。

在以下示例中，定位的批准分为四个子任务。

![](assets/s_ncs_user_task_linked_tasks.png)

每个子任务都是链接到主任务的标准任务。

![](assets/s_ncs_user_task_depends_on.png)

#### 分组任务 {#grouping-tasks}

使用字 **[!UICONTROL Grouped to]** 段，可以根据另一个任务的执行来执行任务。

![](assets/s_ncs_user_task_group_with.png)

任务之间的依赖关系在营销活动仪表板中由箭头表示。

![](assets/s_ncs_user_task_dependencies_from_board.png)

对于分组任务，Adobe Campaign会自动将父任务的结束日期指定给子任务作为开始日期。 例如，如果“创 **建邀请** ”任务于10月15日下午3:30结束，则“发送邀请电子邮件 **** ”子任务将于10月15日下午3:30开始。

此外，如果您推迟了父项任务的结束，则其某些子项任务可能会受到影响：这些是状态为且开始日期早 **[!UICONTROL Scheduled]** 于父任务的新结束日期的子任务。 任务的持续时间保持不变。 如果子任务的开始日期晚于父任务的新结束日期，则子任务不受影响。

**示例**

预定在10月9日下午5点结束的父任务有两个子任务，任务A和任务B。任务A定于10月10日下午2点开始，任务B定于10月12日上午8点开始。

让我们推迟父任务：现在10月11日下午1点结束。 只有任务A被推迟，并将于10月11日下午1点开始。

![](assets/mrm_task_parent_postpones_child.png)

### 任务的执行状态 {#execution-status-of-a-task}

任务状态可在任务图中查看。 根据操作员操作自动更新任务的执行状态。

任务可以是： **[!UICONTROL Scheduled]**、 **[!UICONTROL In progress]****[!UICONTROL Finished]**、 **[!UICONTROL Canceled]**&#x200B;或 **[!UICONTROL Pending approval]****[!UICONTROL Rejected]**。

* 创建任务时，其开始日 **[!UICONTROL Scheduled]** 期是将来的日期。 它会保持此状态，直到达到其开始日期。
* 一旦启动，任务即为 **[!UICONTROL In progress]**。 当负责任务的人关闭任务时，它会变为 **[!UICONTROL Finished]**。
* 如果已定义审阅者，则任务将在其负责 **[!UICONTROL Pending approval]** 人关闭该任务后，直到审阅者批准该任务为止。 如果审阅人拒绝了该任务，则任务将为 **[!UICONTROL Rejected]**。
* 任务的负责人可以通过仪表板或单击按钮来取消 **[!UICONTROL Task map]** 该任 **[!UICONTROL Cancel]** 务。
* 要计划任务，请输入将来的开始日期。 然后，您可以向执行任务时涉及的Adobe Campaign操作员发送第一个通知。 请参 [阅完成任务生命周期](#complete-task-life-cycle)。

>[!NOTE]
>
>* 任务状态会自动更新。
>* 即使有效期已结束，尚未关闭的任务仍会显示在进行中的任务列表中。 警告会通知操作员任务已延迟。
>



### 任务的进度状态 {#progress-status-of-a-task}

除了执行状态之外，任务还可以与进度状态关联： **[!UICONTROL Late]**、 **[!UICONTROL To approve]****[!UICONTROL To do today]** 或 **[!UICONTROL To do this week]**。 此信息将根据任务计划自动输入。

您可以按进程或进度状态过滤任务列表。

For more on this, refer to [Accessing tasks](#accessing-tasks).

### 完成任务生命周期 {#complete-task-life-cycle}

以下是整个任务生命周期的各个阶段，负责人为这些阶段定义了参加者和审阅者。

1. 负责人创建任务并进入各个字段。 有关此功能的详细信息，请参 [阅创建新任务](#creating-a-new-task)。

   在将来创建和编 **辑计划的任务** （只要未到达任务开始日期）时，可以向参加者和管理者发送通知，让他们知道已计划新任务。

   ![](assets/s_ncs_user_task_planed_send_message.png)

   要发送此第一个通知，请单击 **[!UICONTROL Yes]**。 此通知会告知他们下一个任务的相关信息，并包含有关内容的详细信息以及截止日期前的剩余天数。

   创建任务并计划在以后执行时，其状态为 **[!UICONTROL Scheduled]**。

1. 在任务开始日期，负责人和参加者将收到通知，告知他们任务已开始。 其状态将更改为 **[!UICONTROL In progress]**。
1. 完成分配给他们的部分后，参加者可以批准该任务，具体方法如下：

   * 通过通知电子邮件。
   * 通过控制台或Web界面，在任务功能板中。

      ![](assets/s_ncs_user_task_start_rea.png)

1. 每次参加者批准作业时，任务的进度状态都会更新。

   ![](assets/s_ncs_user_task_percentage_done_op.png)

1. 审阅者收到通知电子邮件，告知他操作员已完成分配给他们的部分。

   他们可以按照任务功能板上的进度操作。

   ![](assets/s_ncs_user_task_follow_from_dashboard.png)

1. 一旦负责任务的人员确定任务已完成，他们便可以使用启动任务时发送的通知电子邮件中的链接、控制台或界面将其关闭。

   ![](assets/s_ncs_user_task_console_ressource_validation.png)

   >[!NOTE]
   >
   >任务负责人可以随时关闭该任务，即使缺少批准也是如此。 进度状态会自动更改为100%。

1. 任务状态将更 **[!UICONTROL To approve]**&#x200B;改为，并向审阅者发送通知。

   他们通过通知电子邮件、控制台或Web界面批准任务。

   他们可以通过营销活动仪表板进行操作：

   ![](assets/s_ncs_user_task_console_validation.png)

   他们还可以使用任务批准按钮：

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >只有在任务窗口中启 **[!UICONTROL To approve]** 用了该选项后，任 **[!UICONTROL Enable task validation]** 务状态才 **[!UICONTROL Resources]** 会更改为。\
   >如果审阅人拒绝了任务，则其状态将更 **[!UICONTROL Rejected]**&#x200B;改为，并且任务生命周期将再次自动启动。

1. 任务状态将更改为 **[!UICONTROL Finished]**。 系统会向所有相关人员发送通知。

   >[!NOTE]
   >
   >任务完成后，其生命周期可由负责人重新初始化。 为此，请打开任务，然后单击功 **[!UICONTROL Reset task to execute it again...]** 能板底部的链接。

