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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '3737'
ht-degree: 0%

---


# 创建和管理任务{#creating-and-managing-tasks}

## 关于任务 {#about-tasks}

Adobe Campaign允许您直接在应用程序中创建任务并管理其整个生命周期。 项目和活动实现可分解为分配给Adobe Campaign操作符或外部服务提供商的任务。 通过此操作模式，您可以创建包含所有项目参加者和外部参加者的开放式协作环境。

任务可以从任务的列表或活动仪表板创建、查看和监视。 还可以在营销计划、项目和活动的计划中查看和跟踪它们。

任务与活动相连，可以具有相关性，即关联任务。 每个任务都有状态、优先级、估计负载和相关成本。

所有任务都分组在一个列表中，可通过活动 **世界** 访问。 For more on this, refer to [Accessing tasks](#accessing-tasks).

它们可以在它们所属项目的计划中显示。

![](assets/d_ncs_user_tasks_in_planning.png)

## 访问任务 {#accessing-tasks}

### 显示任务 {#displaying-tasks}

任务显示在任务列表中，可通过宇宙访 **[!UICONTROL Campaigns]** 问。

![](assets/s_ncs_user_task_edit_view.png)

您可以在此视图所连接运算符的所有任务。

有关详细信息，请参 [阅任务的执行状态](#execution-status-of-a-task)[和任务的进度状态](#progress-status-of-a-task)。

### 筛选任务 {#filtering-tasks}

当您显示此视图时，系统会自动过滤它，以便仅显示 **[!UICONTROL operator tasks]**。 您还可以使用窗口上半部分的字段过滤任务。

![](assets/s_ncs_user_task_filter_from_view.png)

### 编辑任务 {#editing-tasks}

单击任务进行编辑。

![](assets/s_ncs_user_task_edit_from_view.png)

## Creating a new task {#creating-a-new-task}

要创建任务，请单击 **[!UICONTROL Tasks]** 活动范围中的链接并选择 **[!UICONTROL Create]**。

![](assets/s_ncs_user_task_create_new.png)

至少输入任务的名称，并选择与之链接的活动。 您还必须指定开始和结束日期。 这三条信息是强制性的。

单击 **[!UICONTROL Save]** 以创建任务。

![](assets/s_ncs_user_task_create_simple.png)

您还可以通过任务的仪表板创建活动:在这种情况下，它会自动链接到它所创建的活动。

![](assets/s_ncs_user_task_create_new_from_op.png)

创建任务后，它将添加到活动计划和任务列表。 要编辑任务，请从计划中选择它，或在任务概述中单击其名称，然后单击链 **[!UICONTROL Open]** 接。

![](assets/s_ncs_user_task_edit_simple.png)

要进行配置，您必须指明：

* 管理者和参加者：请参阅 [管理者和参加者](#manager-and-participants)。
* 创建计划:请参阅 [执行计划](#execution-schedule)。
* 承诺成本：请参阅 [费用和收入](#expenses-and-revenues)。

还可以向审阅者广告(请参 [阅审](#reviewers)阅者)和引用文档 [(请参阅引用](#documents-referenced)的文档)。

任务生命周期在生命 [周期中](#life-cycle)。

### 管理者和参加者 {#manager-and-participants}

只有负责任务的运营商才有权关闭它。

默认情况下，当Adobe Campaign运算符创建任务时，会自动将其分配给它们。 要选择其他运算符，请使用 **[!UICONTROL Assigned to]** 字段。

![](assets/s_ncs_user_task_edit_simple_general_tab.png)

>[!NOTE]
>
>操作员管理在本节 [中介绍](../../platform/using/access-management.md)。

您可以指定执行任务时涉及的运算符。 这些运营商无权关闭任务。 他们只能批准分配给他们的任务。

它们将使用任务工 **[!UICONTROL Resources]** 具栏中的图标进行选择。 单击 **[!UICONTROL Add]** 并选择相关的运算符。

![](assets/s_ncs_user_task_add_resources.png)

单击 **[!UICONTROL Ok]** 并输入使用率：这表示在任务执行期间分配给运算符的负载。 此比率仅表示，以百分比表示。

例如，对于执行计划设置为10天的任务，使用率为50%的操作员将在此任务上移动其10天半工作时间。

对于每个操作员，您可以输入计划的工作量和实际的工作量。 这些持续时间也仅用于信息目的。

可以配置提醒，提醒将在任务结束之前自动发送给该提醒中涉及的所有操作员。

您可以通过图标视图Adobe Campaign运算符 **[!UICONTROL Edit link]** 用户档案。

![](assets/s_ncs_user_task_edit_resource_profile.png)

运算符仪表板允许您检查其工作量(其他正在进行的任务)。

![](assets/s_ncs_user_task_edit_resource_planning.png)

### 审阅者 {#reviewers}

除了参加者之外，您还可以定义操作员，在任务被负责人关闭后，操作员将审核该数据。 为此，请单 **[!UICONTROL Enable task approval]** 击窗口左下方的选 **[!UICONTROL Resources]** 项。 这可以是单个运算符、操作员组或运算符列表。

![](assets/s_ncs_user_task_edit_resource_validation.png)

要指定运算符的列表，请单 **[!UICONTROL Edit...]** 击第一个审阅者右侧的链接，并根据需要添加任意数量的运算符，如下所示：

![](assets/s_ncs_user_task_edit_resource_operators.png)

您可以在审阅者配置窗口的下半部分为任务定义审批计划。 默认情况下，审阅人从提交日期开始有三天时间批准任务。 可以配置提醒，提醒将在批准截止日期之前自动发送给相关运营商。

![](assets/s_ncs_user_edit_op_valid_calendar.png)

任务负责人可以自行分配批准任务，即使已指派其他运营商这样做。 如果尚未定义审阅人，则通知将发送给任务负责人。 所有其他具有权限 **[!UICONTROL Administrator]** 的Adobe Campaign运营商也可以批准任务。 但是，他们不会收到通知。

### 文档引用 {#documents-referenced}

可以向任务添加文档和营销资源(有关详细信息，请参阅管 [理营销资源](../../campaign/using/managing-marketing-resources.md))。 要这样做，请打开任务并单 **[!UICONTROL Documents]** 击任务工具栏中的图标。

单 **[!UICONTROL Add]** 击并选择要添加到文档的任务。 对营销资源应用相同的流程。

![](assets/s_ncs_user_task_edit_documents.png)

引用的文档将显示在发送给任务中涉及的操作符的通知中以及任务仪表板中。

![](assets/s_ncs_user_task_notification_documents.png)

### 执行计划 {#execution-schedule}

任务的有效期在和字段中 **[!UICONTROL Start]** 指 **[!UICONTROL End]** 示。 调度的负载表示在该期间要执行的工作负荷。 它以天或小时表示。

>[!NOTE]
>
>任务的生命周期在生命周期中 [表示](#life-cycle)。

该字 **[!UICONTROL Workload performed]** 段还以天和小时为单位，允许您手动更新任务在计划工作量方面的进度。

![](assets/s_ncs_user_task_percentage_done_enter.png)

任务 **[!UICONTROL Progress status]** 以百分比表示，根据相关操作员执行的任务自动更新。 可以手动输入。

此信息可在任务仪表板中查看。

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

它也显示在“活动”选项卡中。

![](assets/s_ncs_user_task_percentage_done_from_op.png)

如果任务执行计划结束日期已达到但任务未完成，则任务将被 **[!UICONTROL Late]**。 警告消息还将显示给警报操作符。

有关此内容的详细信息，请参 [阅任务的进度状态](#progress-status-of-a-task)。

### 费用和收入 {#expenses-and-revenues}

您可以为每个任务定义相关费用和预测收入。 这些值将计算，然后合并到活动所附加的任务。

要指定此信息，请单击 **[!UICONTROL Expenses and revenue]** 任务工具栏中的图标。

![](assets/s_ncs_user_task_edit_costs.png)

默认情况下，已支付预算是附加活动的任务的预算。 它显示在任务详细信息中。

>[!NOTE]
>
>有关费用和预算的更多信息，请参 [阅成本承诺、计算和费用](../../campaign/using/controlling-costs.md#cost-commitment--calculation-and-charging)。

在此窗口中，您还可以定义要达到的目标。 目标以任务的预测收入表示。

### 服务提供商 {#service-providers}

外部服务提供商可以参与任务管理。

为此，请编辑任务属性并选择相关服务提供商。 与服务提供商关联的成本类别会自动列在窗口的中央部分。

有关此内容的详细信息，请 [参阅创建服务提供商及其成本类别](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

选择与执行类别相关的成本任务。 为此，请选择成本类型，并根据需要添加附加费金额。

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>管理预算及成本之方法于控 [制成本](../../campaign/using/controlling-costs.md)。

选择服务提供商后，任务仪表板中将显示该：

![](assets/s_ncs_user_task_supplier_view.png)

### 延迟任务 {#late-tasks}

如果任务已达到其结束日期，且其状态未更改为，则该订阅将延迟 **[!UICONTROL Finished]**。 默认情况下，当任务延迟时，不会警告任何运算符。 您可以配置通知电子邮件的投放:即使所有运营商不参与任务，也可以通知它们。

转到框 **[!UICONTROL Resources]** 并将运算符添加到字 **[!UICONTROL Assignation]** 段。 要通知多个人，请选择操作员组。

![](assets/mrm_task_alert_if_late.png)

### 初始通知 {#initial-notifications}

在将来创建或修改具有任务日期的开始时，Adobe Campaign优惠会向任务负责人发送电子邮件，告知其开始时间。

![](assets/mrm_task_first_notif.png)

但是，如果您创建的任务距离很远，则最好计划要在任务开始之前发送的通知。 例如，如果任务开始在一个月内，您可以在开始一周前通知负责此事的人。

要计划通知，请转到框 **[!UICONTROL Resources]** 并使用字 **[!UICONTROL Initial notification]** 段。

![](assets/mrm_task_alert_before.png)

* 对于活动内的任务，选择特定日期和时间。
* 对于活动模板内的任务，通知时间表示为任务开始之前的剩余时间(例如，如果您在字段中输入2d，则在任务开始日期前2天将发送电子邮件 **[!UICONTROL Initial notification]** )。

如果已安排通知，则在保存任务时，Adobe Campaign会停止优惠以立即发送通知。 您可以决定发送它，但不会替换计划的通知。

### 任务链接到项目 {#task-linked-to-a-program}

您可以直接在项目中创建任务，以管理与其整体组织而非特定活动相关的操作(例如，讨论该项目中即将进行的活动的主题的会议)。 任务将显示在项目计划中。

要创建直接链接到任务的项目，请执行以下操作：

1. 打开项目计划:在主页上，转到 **[!UICONTROL Campaigns > Browse > Other choices > Programs]**。 整个项目计划在窗口的右侧部分打开。
1. 在计划中，单击所需的项目:窗子里有项目。
1. 在此窗口中，单击 **[!UICONTROL Open]**。 项目计划打开。
1. 单击右 **[!UICONTROL Add]** 侧计划上方的按钮，然后单击 **[!UICONTROL Add a task]**。

![](assets/mrm_task_create_from_prg.png)

### 运营商可用性 {#operator-availability}

在任务仪表板中，操作符名称旁的图标表示在任务所涵盖的期间，他们已在处理其他任务或事件。 (经营者负责或参与的任务:他出现在 **[!UICONTROL Assigned to]** 字段或任务 **[!UICONTROL Resources]** 框中)。

![](assets/mrm_task_alert_operator_busy.png)

### 任务工作流 {#task-in-a-workflow}

在活动工 **[!UICONTROL Task]** 作流中使用元素，您可以根据任务是否获得批准来定义两种方案。

![](assets/mrm_task_in_workflow.png)

在活动工作流中， **[!UICONTROL Task]** 活动位于选项卡 **[!UICONTROL Flow control]** 中。

## 任务类型 {#types-of-task}

通过任务创建活动时，可以创建特定任务。 任务类型在所选模板中定义。

![](assets/s_ncs_user_task_select_template.png)

可以计划以下任务:

* [控制任务](#control-tasks),
* [分组任务](#grouping-task),
* [分组任务](#grouping-task),
* [通知任务](#notification-task)。

>[!NOTE]
>
>**[!UICONTROL Control task]** 而 **[!UICONTROL Grouping]** 任务只能 **通过** 活动仪表板创建。\
>它们显示在为其分配了它们的运算符的任务图中。 请参 [阅访问任务](#accessing-tasks)。

### 控制任务 {#control-tasks}

A **[!UICONTROL Control task]** 与投放批准关联：批准定位、内容、提取文件、预算或验证。

![](assets/s_ncs_user_task_new_control.png)

创建任务后，该活动会添加到该仪表板。

![](assets/s_ncs_user_task_edit_from_board.png)

然后，可以编辑它并指定其参数。

### 营销资源创建任务 {#marketing-resource-creation-task}

营销资源创建任务可用于管理营销资源的创建和发布。 如果您通过任务而不是通过资源本身管理资源，您可以：

* 通过活动控制资源创建过程。
* 视图计划中的资源创建过程。
* 管理资源创建过程（提醒、通知）。
* 计算和控制与资源创建相关的成本。
* 通过任务批准和发布资源（如果启用了相关选项）。

#### 任务与其链接资源之间的交互 {#interaction-between-the-task-and-its-linked-resource}

营销资源创建任务与链接到它的资源交互。 这意味着：

* 资源创建计划和与其关联的成本通过任务进行管理。
* 操作员可以处理资源，如普通资源（下载或上传、锁定和解锁）:这不会影响任务。
* 资源审批和发布可以通过以下任务进行：如果启 **[!UICONTROL Publish the marketing resource]** 用了该选项，则任务完成后，资源将自动获得批准并发布。 如果未启用该选项，则任务与资源不会交互：对一个不会影响另一个。

   您可以使用一系列链接任务来定义完整的审批周期。 仅选 **[!UICONTROL Publish the marketing resource]** 中最后一个任务:需要完成所有任务才能发布资源。 此外，当您创建子营销资源任务时，将在子任务中自动选择资源。

   * **通过资源**:如果您提交资源进行审批或批准，则这些操作不会影响任务。
   * **通过任务**:如果 **[!UICONTROL Publish the marketing resource]** 选项已在任务中选中，则任务完成后，资源将自动获得批准并发布（请参阅上文）。 如果未选中该选项，则任务与资源不会交互：对一个不会影响另一个。

#### 配置营销资源创建任务 {#configuring-a-marketing-resource-creation-task}

审阅任务的人员并非需要审阅资源中定义的内容的人员。 但是，如果选 **[!UICONTROL Publish the marketing resource]** 中了该选项（请参阅下文），则任务审查者在完成任务时将自动批准资源(如果未定义审查者，则授权任务管理者)，以批准资源内容。

![](assets/mrm_task_asset_creation.png)

在字 **[!UICONTROL Marketing resource]** 段中，定义要通过此任务管理的资源。 您可以：

* 选择现有资源：下拉列表将优惠所有具有状态的资源 **[!UICONTROL Being edited]**。
* 创建资源：单击图 **[!UICONTROL Select the link]** 标，然后单击图 **[!UICONTROL Create]** 标。

通过 **[!UICONTROL Publish the marketing resource]** 此选项，可自动发布资源：一旦任务 **[!UICONTROL Finished]**&#x200B;生效，资源的状态即自动切换为 **[!UICONTROL Published]**，即使它既未提交审批也未获得批准，包括完成任务的审阅者不是资源中定义的内容审阅者。

该 **[!UICONTROL Publish the resource]** 按钮可用，资源发布审阅者会收到通知电子邮件，告知其已准备好发布。 在选项卡 **[!UICONTROL Edit > Tracking]** 中，任务审阅者的审阅和发布变为可见。 如果已定义资源后处理工作流，则立即执行该工作流。

![](assets/mrm_resource_audit_tab.png)

### 分组任务 {#grouping-task}

通过 **[!UICONTROL Grouping task]** 类型任务，您可以对多个任务进行分组，并同步对其进度和批准的管理。

分组任务没有关联的费用或资源。

分组到分组任务的所有任务都可以在其自己的仪表板上查看。 这样，您可以过滤任务的列表，以仅显示您感兴趣的内容。

分组任务有一个链接，可让您轻松创建分组任务。

要根据分组任务创建分组任务，请转到活动仪表板，单击分组任务的名称以显示其说明，然后单击 **[!UICONTROL Add a task]**。

![](assets/mrm_task_grouped_create.png)

但是，如果已创建要链接到分组任务的任务，则可以通过框的字 **[!UICONTROL Linked to]** 段进行链 **[!UICONTROL Properties]** 接。

![](assets/s_ncs_user_task_group_with.png)

### 通知任务 {#notification-task}

通知任务允许您计划电子邮件投放(向操作员、操作员组、服务提供商等)。 这允许您计划提醒，例如通知某人活动即将完成，或在活动开始之前发送文档，以便操作员可以准备。 这意味着您可以跟踪活动或项目内的通信，并更密切地关注所执行的操作。

#### 生命周期 {#life-cycle}

通知任务不需要批准。 这意味着他们的生命周期比标准任务更简单：

![](assets/mrm_task_notif_lifecycle.png)

通知任务可以具有以下状态：

* **[!UICONTROL Scheduled]** 直到电子邮件被发送
* **[!UICONTROL In progress]** 发送电子邮件，直到到达结束日期
* **[!UICONTROL Finished]** 到达结束日期后。

#### 配置{#configuration}

![](assets/mrm_task_notif_dashboard.png)

在创建过程中，必须在任务中输入以下元素：

* **[!UICONTROL Assigned to]** :接收电子邮件的运营商或操作员组。 如果在发送电子邮件后重新分配任务，则电子邮件将不会发送给新操作员(为此，您需要重新初始化任务并更改其开始日期)。
* **任务开始日期**:通知电子邮件的发送日期。 此日期必须在将来记录任务时发生。
* **任务结束日期**:任务状态更改为的日期 **[!UICONTROL Finished]**。 默认情况下，结束日期与开始日期相同。 但是，为任务指定持续时间允许您象征操作员在计划中必须执行的时间量（如果需要）。
* **[!UICONTROL Description]** :此处输入的文本将显示在通知电子邮件的正文中。

   ![](assets/mrm_task_notif_dashboard_msg.png)

您可以向任务和通知电子邮件中添加附件。 为此，请单 **[!UICONTROL Documents]** 击右上角工具栏中的图标。

## 生命周期 {#life-cycle-1}

### 任务之间的链接 {#links-between-tasks}

每个 **[!UICONTROL Properties]** 任务中的按钮使您能够定义活动中任务之间的链接。 您可以使用分组任务将任务拆分为子任务(请参 [阅链接任务](#linked-tasks))，或定义任务之间的依赖关系(请参 [阅分组任务](#grouping-tasks))。

#### 链接任务 {#linked-tasks}

使用该 **[!UICONTROL Linked task]** 字段将任务与分组任务关联。 请参 [阅任务类型](#types-of-task)。

在以下示例中，目标批准被划分为四个子任务。

![](assets/s_ncs_user_task_linked_tasks.png)

每个子任务都是链接到主任务的标准任务。

![](assets/s_ncs_user_task_depends_on.png)

#### 分组任务 {#grouping-tasks}

使用 **[!UICONTROL Grouped to]** 该字段，可以根据执行其他任务来执行任务。

![](assets/s_ncs_user_task_group_with.png)

任务之间的依赖关系在活动仪表板中由箭头表示。

![](assets/s_ncs_user_task_dependencies_from_board.png)

对于分组任务,Adobe Campaign会自动将父任务的结束日期分配给子任务，作为开始日期。 例如，如果“创 **建邀请** ”任务在10月15日下午3:30结束，则“发送邀 **请电子邮件** ”子任务将于10月15日下午3:30开始。

此外，如果你推迟了父母任务的结束，其子任务可能会受到影响：这些是状态为且其任务日 **[!UICONTROL Scheduled]** 期早于父开始的新结束日期的子任务。 任务的持续时间保持不变。 如果子开始的任务日期晚于父任务的新结束日期，则子任务不受影响。

**示例**

任务A计划于10月9日下午5点结束，其父有两个子任务,任务A和任务B。任务A计划于10月10日下午2点开始,任务B计划于10月12日上午8点开始。

让我们推迟家长任务:现在10月11日下午1点结束。 只有任务A推迟，将于10月11日下午1点开始。

![](assets/mrm_task_parent_postpones_child.png)

### 任务的执行状态 {#execution-status-of-a-task}

任务状态可以是任务图中的视图。 任务的执行状态根据操作符操作自动更新。

任务可以是： **[!UICONTROL Scheduled]**、 **[!UICONTROL In progress]**、 **[!UICONTROL Finished]****[!UICONTROL Canceled]**&#x200B;或 **[!UICONTROL Pending approval]****[!UICONTROL Rejected]**。

* 创建任务时，是 **[!UICONTROL Scheduled]** 否将来开始日期。 它将保持此状态，直到达到其开始日期。
* 一旦启动，任务就开始了 **[!UICONTROL In progress]**。 当任务负责人关闭它时，它会变为 **[!UICONTROL Finished]**。
* 如果已定义审阅者，则任务将 **[!UICONTROL Pending approval]** 在其负责人关闭该审阅者后，直到审阅者批准它。 如果审阅者拒绝，则任务将为 **[!UICONTROL Rejected]**。
* 任务可由负责该仪表板的人员通过或单击按钮 **[!UICONTROL Task map]** 来取消该 **[!UICONTROL Cancel]** 订阅。
* 要计划任务，请输入开始日期。 然后，您可以向执行Adobe Campaign时涉及的任务操作符发送第一个通知。 请参 [阅完整的任务生命周期](#complete-task-life-cycle)。

>[!NOTE]
>
>* 任务状态会自动更新。
>* 即使有效期结束，未关闭的任务仍显示在进行中的列表中。 警告会通知运算符任务已延迟。

>



### 任务进度状态 {#progress-status-of-a-task}

除了执行状态之外，任务还可以与进度状态关联： **[!UICONTROL Late]**、 **[!UICONTROL To approve]**&#x200B;或 **[!UICONTROL To do today]** 者 **[!UICONTROL To do this week]**。 此信息会根据任务计划自动输入。

您可以按流程或进度状态过滤任务列表。

For more on this, refer to [Accessing tasks](#accessing-tasks).

### 完整的任务生命周期 {#complete-task-life-cycle}

以下是整个任务生命周期的各个阶段，负责人已为其定义了参与者和审阅者。

1. 负责人创建任务并进入各个字段。 有关此内容的详细信息，请 [参阅创建新任务](#creating-a-new-task)。

   在将来创建和编 **辑计划的任务** (只要任务开始日期未达到)时，可以向参加者和管理者发送通知，让他们知道已计划新任务。

   ![](assets/s_ncs_user_task_planed_send_message.png)

   要发送此第一个通知，请单击 **[!UICONTROL Yes]**。 此通知会告知他们下一个任务，并包含有关内容的详细信息以及截止日期前剩余天数。

   在创建任务并计划在将来时，其状态为 **[!UICONTROL Scheduled]**。

1. 在任务开始日期，负责人和参加者将收到通知，告知他们任务已开始。 其状态将更改为 **[!UICONTROL In progress]**。
1. 完成分配给他们的部分后，参加者可以批准任务，可以：

   * 通知电子邮件。
   * 或web界面，在任务仪表板中。

      ![](assets/s_ncs_user_task_start_rea.png)

1. 每次参加者批准作业时，任务的进度状态都会更新。

   ![](assets/s_ncs_user_task_percentage_done_op.png)

1. 审阅者收到通知电子邮件，告知他操作员已完成分配给他们的部分。

   他们可以追踪任务仪表板的进展。

   ![](assets/s_ncs_user_task_follow_from_dashboard.png)

1. 任务负责人一旦确定任务已完成，便可使用启动时发送的通知电子邮件中的链接、控制台或界面将其关闭。

   ![](assets/s_ncs_user_task_console_ressource_validation.png)

   >[!NOTE]
   >
   >任务负责人可以随时关闭它，即使没有批准。 进度状态自动更改为100%。

1. 任务状态将变 **[!UICONTROL To approve]**&#x200B;为，并向审阅者发送通知。

   他们通过通知电子邮件、控制台或Web界面批准任务。

   他们可以通过活动仪表板采取行动：

   ![](assets/s_ncs_user_task_console_validation.png)

   他们还可以使用任务批准按钮：

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >只有在任务窗口中启 **[!UICONTROL To approve]** 用了该选项 **[!UICONTROL Enable task validation]** ,任务 **[!UICONTROL Resources]** 状态才会更改为。\
   >如果审阅者拒绝任务，其状态将更 **[!UICONTROL Rejected]**&#x200B;改为，任务生命周期将再次自动开始。

1. 任务状态将更改为 **[!UICONTROL Finished]**。 通知会发送给所有相关人员。

   >[!NOTE]
   >
   >任务完成后，其生命周期可由负责人重新初始化。 为此，请打开任务并 **[!UICONTROL Reset task to execute it again...]** 单击仪表板底部的链接。

