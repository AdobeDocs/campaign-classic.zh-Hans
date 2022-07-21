---
product: campaign
title: 工作流最佳实践
description: 了解Campaign工作流最佳实践
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1687'
ht-degree: 6%

---

# 工作流最佳实践{#workflow-best-practices}

![](../../assets/v7-only.svg)

## 执行和性能 {#execution-and-performance}

下面列出了有关优化Campaign效果的一般准则，包括应用于工作流的最佳实践。

与工作流执行相关的故障诊断准则也在 [Campaign Classicv7生产指南](../../production/using/workflow-execution.md).

### 日志 {#logs}

JavaScript方法 **[!UICONTROL logInfo()]** 是调试工作流的绝佳解决方案。 此插件非常有用，但必须仔细使用，尤其是对于经常运行的活动：它可能会使日志过载，并显着增加日志表的大小。 但你可能还需要 **[!UICONTROL logInfo()]**.

另外还提供了两个可帮助的解决方案：

* **在两次处决之间保留临时人口的结果**

   此选项会在工作流的两次执行之间保留临时表。 它可在工作流属性的 **[!UICONTROL General]** 选项卡，可用于开发和测试以监控数据和检查结果。 您可以在开发环境中使用此选项，但决不能在生产环境中使用此选项。 保留临时表可导致数据库的大小显着增加，最终达到大小限制。 此外，这会减缓备份速度。

   只保留上次执行工作流的工作表。 以前执行中的工作表会被 **[!UICONTROL cleanup]** 工作流，每天运行。

   >[!CAUTION]
   >
   >不得在生产工作流中勾选此选项。此选项用于分析结果，仅用于测试目的，因此必须仅用于开发或暂存环境。

* **在日志中记录SQL查询**

   在 **[!UICONTROL Execution]** 选项卡，此选项将记录该工具从不同活动生成的所有SQL查询。 这是查看平台实际执行的操作的好方法。 但是，此选项只应在开发期间临时使用，而不应在生产时激活。

当日志不再需要时清除日志。 工作流历史记录不会自动清除：默认情况下，会保留所有消息。 历史记录可以通过 **[!UICONTROL File > Actions]** 菜单，或通过单击位于列表上方工具栏中的“操作”按钮来访问。 选择清除历史记录。
要了解如何清除日志，请参阅 [文档](starting-a-workflow.md).

### 工作流计划 {#workflow-planning}

* 尝试在一天中保持活动的稳定级别，并避免出现峰值以防止实例过载。 要实现此目的，请在一天中平均分配工作流的开始时间。
* 安排隔夜数据加载以减少资源争用。
* 长工作流可能会对服务器和数据库资源产生潜在影响。 拆分最长的工作流以缩短处理时间。
* 为了缩短整体运行时间，请使用简化且更快的活动替换耗时的活动。
* 避免同时运行20个以上的工作流。 当同时执行的工作流过多时，系统可能会耗尽资源并变得不稳定。 有关工作流可能未启动的原因的更多信息，请参阅此 [文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### 工作流执行 {#workflow-execution}

**请勿将工作流计划为每15分钟运行一次以上** 因为它可能会妨碍系统的整体性能，并在数据库中创建块。

**避免将工作流保留为暂停状态**. 如果您创建临时工作流，请确保该工作流能够正确完成，并且不会停留在 **[!UICONTROL paused]** 状态。 如果暂停，则意味着需要保留临时表，从而增加数据库的大小。 在“工作流属性”下分配“工作流监管者”，以在工作流失败或系统暂停时发送警报。

要避免工作流处于暂停状态，请执行以下操作：

* 定期检查您的工作流，以确保没有意外错误。
* 尽可能简单地保持工作流，例如，将大型工作流拆分到多个不同的工作流中。 您可以使用 **[!UICONTROL External signal]** 活动会根据其他工作流的执行触发其执行。
* 避免在工作流中禁用流的活动导致线程打开，并导致许多临时表占用大量空间。 请勿将活动保留在 **[!UICONTROL Do not enable]** 或 **[!UICONTROL Enable but do not execute]** 状态。

**停止未使用的工作流**. 持续运行的工作流维护与数据库的连接。

**仅在最少情况下使用无条件停止**. 请勿定期使用此操作。 对工作流生成的与数据库的连接不执行干净关闭会影响性能。

**请勿在同一工作流上执行多个停止请求**. 停止工作流是一个异步过程：注册请求，然后工作流服务器或服务器取消正在进行的操作。 因此，停止工作流实例可能需要时间，尤其是当工作流在多个服务器上运行时，每个服务器都必须控制以取消正在进行的任务。 要避免出现任何问题，请等待停止操作完成，并避免多次停止工作流。

### 在引擎选项中执行 {#execute-in-the-engine-option}

在 **[!UICONTROL Workflow properties]** 窗口，从不检查 **[!UICONTROL Execute in the engine]** 选项。 启用此选项后，工作流将具有优先级，所有其他工作流将由工作流引擎停止，直到此工作流完成为止。

![](assets/wf-execute-in-engine.png)

## 工作流属性 {#workflow-properties}

### 工作流文件夹 {#workflow-folders}

Adobe建议您在专用文件夹中创建工作流。

如果工作流影响整个平台（例如清理流程），则可以考虑在内置文件夹中添加子文件夹 **[!UICONTROL Technical Workflows]** 文件夹。

### 工作流命名 {#workflow-naming}

Adobe 建议为工作流赋予正确的名称和标签，这样工作流没有按照预期的方式执行，可轻松地找到并排除故障：填写工作流的描述字段，在其中加入执行流程的摘要，以便操作员能够轻松理解。

如果工作流是涉及多个工作流的流程的一部分，则在输入标签时可以显式显示；使用数字是对工作流进行排序（按标签）的极好方法。

例如：

* 001 — 导入 — 导入收件人
* 002 — 导入 — 导入销售
* 003 — 导入 — 导入销售详细信息
* 010 — 导出 — 导出投放日志
* 011 — 导出 — 导出跟踪日志

### 工作流严重性 {#workflow-severity}

您可以在工作流属性中的 **[!UICONTROL Execution]** 选项卡：

* 正常
* 生产
* 关键

在创建工作流时提供此信息将帮助您了解配置流程的严重性。

此选项对工作流（营销活动工作流除外）没有功能影响。

优先级较高的营销活动工作流（作为营销活动/操作的一部分创建的工作流）会执行，以防营销活动有多个应同时运行的流程。 默认情况下，根据选项NmsOperation_LimitConcurrency，在营销活动中只能同时运行10个进程。 例如，如果营销活动包含25个工作流，则严重性较高的工作流将在10个流程的第一个池中执行。

### 工作流监测 {#workflow-monitoring}

应监控在生产环境中运行的所有计划工作流，以便在出错时收到警报。

在工作流属性中，选择一个“主管”组(默认为 **[!UICONTROL Workflow supervisors]** 或自定义群组。 确保至少有一个运算符属于此组，并设置了电子邮件。

在开始构建工作流之前，请记住定义工作流监管者。 如果出现错误，系统会通过电子邮件通知他们。 有关更多信息，请参阅 [管理错误](monitoring-workflow-execution.md#managing-errors).

定期查看 **[!UICONTROL Monitoring]** 选项卡，以查看活动工作流的整体状态。 有关更多信息，请参阅 [实例监督](monitoring-workflow-execution.md#instance-supervision).

Workflow HeatMap使Adobe Campaign平台管理员能够监控实例的负载并相应地规划工作流。 有关更多信息，请参阅 [工作流监控](heatmap.md).

## 使用活动 {#using-activities}

>[!CAUTION]
>
>您可以在同一工作流中复制并粘贴活动。 但是，我们不建议跨不同的工作流复制粘贴活动。 执行目标工作流时，附加到活动（如“投放”和“调度程序”）的某些设置可能会导致冲突和错误。 我们建议您  **复制** 工作流。 有关更多信息，请参阅 [复制工作流](building-a-workflow.md#duplicating-workflows).

### 活动的名称 {#name-of-the-activity}

在开发工作流时，所有活动都将具有名称，所有Adobe Campaign对象也将具有名称。 虽然该名称由工具生成，但我们建议您在配置时使用显式名称对其重命名。 以后执行该操作的风险在于，它可能会使用另一个先前活动的名称中断使用活动的工作流。 因此，更新姓名将是一项困难的工作。

活动名称可在 **[!UICONTROL Advanced]** 选项卡。 别留下他们的名字 **[!UICONTROL query]**, **[!UICONTROL query1]**, **[!UICONTROL query11]**，但请为其指定名称，例如 **[!UICONTROL querySubscribedRecipients]**. 此名称将显示在日志中，如果适用于SQL日志，这将有助于在配置工作流时调试该工作流。

### 第一个和最后一个活动 {#first-and-last-activities}

* 始终使用 **[!UICONTROL Start]** 活动或 **[!UICONTROL Scheduler]** 活动。 相关时，您还可以使用 **[!UICONTROL External signal]** 活动。
* 在构建工作流时，只使用一个 **[!UICONTROL Scheduler]** 每个分支的活动。 如果工作流的同一分支具有多个调度程序（相互链接），则要执行的任务数量将呈指数级增长，这将使数据库严重过载。此规则还适用于具有 **[!UICONTROL Scheduling & History]** 选项卡。 了解详情 [计划](scheduler.md).

   ![](assets/wf-scheduler.png)

* 使用 **[!UICONTROL End]** 活动。 这允许Adobe Campaign释放用于工作流中计算的临时空间。 有关更多信息，请参阅： [开始和结束](start-and-end.md).

### 活动中的Javascript {#javascript-within-an-activity}

初始化工作流活动时，您可能需要添加JavaScript。 这可以在活动的 **[!UICONTROL Advanced]** 选项卡。

为了更轻松地查找工作流，我们建议在活动标签的开始和结束处使用双破折号，如下所示： — 我的标签 — 

### 信号 {#signal}

在大多数情况下，您将不知道从何处调用信号。 为避免出现此问题，请使用 **[!UICONTROL Comment]** 字段 **[!UICONTROL Advanced]** 用于记录此活动信号的预期来源的选项卡。

![](assets/workflow-signal-bp.png)

## 工作流更新 {#workflow-update}

不应直接更新生产工作流。 除非该流程包含使用模板工作流创建营销活动，否则应首先在开发环境中对流程进行测试。 验证后，可以在生产环境中部署和启动工作流。

在开发或暂存环境中，而不是在生产环境中执行所有测试。 在这种情况下，无法确保性能。

存档的工作流可以保留在开发平台或测试平台上的存档文件夹中，但生产环境应尽可能保持干净。 如果旧工作流处于不活动状态，则应从生产环境中删除它们。
