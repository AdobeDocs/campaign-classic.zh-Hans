---
product: campaign
title: 工作流最佳实践
description: 了解Campaign工作流最佳实践
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 1baf424138c95b16add37d9d556e3a2566a869c2
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 15%

---

# 工作流最佳实践{#workflow-best-practices}



## 执行和性能 {#execution-and-performance}

下面列出了有关优化Campaign性能的常规准则，包括适用于您的工作流的最佳实践。

有关工作流执行的疑难解答指南，请参见 [《Campaign Classic v7生产指南》](../../production/using/workflow-execution.md).

### 日志 {#logs}

JavaScript方法 **[!UICONTROL logInfo()]** 是用于调试工作流的绝佳解决方案。 它很有用，但必须小心使用，尤其是对于经常运行的活动：它会使日志过载并显着增加日志表的大小。 但您可能还需要 **[!UICONTROL logInfo()]**.

另外还有两种解决方案可提供帮助：

* **保留两次执行之间的临时群体结果**

  此选项在两次执行工作流之间保留临时表。 它可以在工作流属性中使用 **[!UICONTROL General]** 选项卡，并可用于开发和测试目的，以监测数据并检查结果。 您可以在开发环境中使用此选项，但切勿在生产环境中使用。保留临时表可能会导致数据库的大小显著增加并最终达到大小限制。此外，这还将减慢备份速度。

  仅保留最后一次工作流执行的工作表。先前执行的工作表由清除 **[!UICONTROL cleanup]** 工作流，每天运行。

  >[!CAUTION]
  >
  >不得在生产工作流中勾选此选项。此选项用于分析结果，并且是仅为测试目的而设计，因此只能用于开发或暂存环境。

* **在日志中记录 SQL 查询**

  中提供 **[!UICONTROL Execution]** 选项卡中，此选项将记录工具从不同活动生成的所有SQL查询。 这是查看平台实际执行操作的好方法。 但是，此选项应仅在开发期间临时使用，而不在生产环境中激活。

在不再需要日志时清除日志。 系统不会自动清除工作流历史记录：默认情况下会保留所有消息。 可通过以下方式清除历史记录 **[!UICONTROL File > Actions]** 菜单或单击“操作”按钮（位于列表上方的工具栏）。 选择清除历史记录。
要了解如何清除日志，请参阅此 [文档](starting-a-workflow.md).

### 工作流规划 {#workflow-planning}

* 尝试保持一天的稳定活动水平并避免出现峰值以防止实例过载。 为此，请在一天中平均分配工作流的开始时间。
* 安排隔夜加载数据以减少资源争用。
* 较长时间的工作流可能会对服务器和数据库资源产生影响。 拆分最长的工作流以减少处理时间。
* 要缩短总体运行时间，请用简化且更快的活动替换耗时的活动。
* 避免同时运行20个以上的工作流。 当同时执行的工作流过多时，系统可能会耗尽资源并且变得不稳定。 有关工作流可能未启动原因的更多信息，请参阅此 [文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).


### 在引擎中执行选项 {#execute-in-the-engine-option}

在 **[!UICONTROL Workflow properties]** 窗口，从不检查 **[!UICONTROL Execute in the engine]** 选项。 启用此选项后，工作流将具有优先级，并且所有其他工作流都将被工作流引擎停止，直到该工作流完成。

![](assets/wf-execute-in-engine.png)

## 工作流属性 {#workflow-properties}

### 工作流文件夹 {#workflow-folders}

Adobe建议您在专用文件夹中创建工作流。

如果工作流影响整个平台（例如清理流程），您可以考虑在内置中添加子文件夹 **[!UICONTROL Technical Workflows]** 文件夹。

### 工作流命名 {#workflow-naming}

Adobe 建议为工作流赋予正确的名称和标签，这样工作流没有按照预期的方式执行，可轻松地找到并排除故障：填写工作流的描述字段，在其中加入执行流程的摘要，以便操作员能够轻松理解。

如果工作流是涉及多个工作流的流程的一部分，则在输入标签时可以很明确；使用数字是对工作流进行排序（按标签）的好方法。

例如：

* 001 — 导入 — 导入收件人
* 002 — 导入 — 导入销售
* 003 — 导入 — 导入销售详细信息
* 010 — 导出 — 导出投放日志
* 011 — 导出 — 导出跟踪日志

### 工作流严重性 {#workflow-severity}

您可以在工作流属性中配置工作流的严重性，路径是 **[!UICONTROL Execution]** 选项卡：

* 正常
* 生产
* 重要

创建工作流时提供此信息将有助于您了解所配置进程的严重性。

此选项对除活动工作流之外的工作流没有功能影响。

如果营销活动具有多个应同时运行的流程，则优先执行严重性较高的营销活动工作流（作为营销活动/操作的一部分创建的工作流）。 默认情况下，根据选项NmsOperation_LimitConcurrency，营销活动中只能同时运行10个进程。 例如，如果某个营销策划包含25个工作流，则具有较高严重性的工作流随后将在10个进程的第一个池中执行。

### 工作流监测 {#workflow-monitoring}

应监视在生产环境中运行的所有计划工作流，以便在发生错误时收到警报。

在工作流属性中，选择一个Supervisor组（默认） **[!UICONTROL Workflow supervisors]** 或自定义组。 确保至少有一个操作员属于此组，并设置了电子邮件。

在开始构建工作流之前，请记得定义工作流主管。 发生错误时，会通过电子邮件通知他们。 有关详细信息，请参见 [管理错误](monitoring-workflow-execution.md#managing-errors).

定期查看 **[!UICONTROL Monitoring]** 选项卡以查看活动工作流的总体状态。 有关详细信息，请参见 [实例监督](monitoring-workflow-execution.md#instance-supervision).

通过Workflow HeatMap，Adobe Campaign平台管理员可以监控实例的负载并相应地规划工作流。 有关详细信息，请参见 [工作流监测](heatmap.md).

## 使用活动 {#using-activities}

>[!CAUTION]
>
>您可以在同一工作流中复制并粘贴活动。 但是，我们不建议跨不同的工作流复制并粘贴活动。 某些附加到活动（如投放和计划程序）的设置可能会导致执行目标工作流时出现冲突和错误。 为此，我们建议您  **复制** 工作流。 有关更多信息，请参阅 [复制工作流](building-a-workflow.md#duplicating-workflows).

### 活动的名称 {#name-of-the-activity}

在开发工作流时，所有活动都将有一个名称，所有Adobe Campaign对象也是如此。 虽然该名称由工具生成，但我们建议在配置时使用明确的名称重命名它。 稍后执行此操作的风险在于，它可能会使用另一个先前活动的名称中断包含该活动的工作流。 因此，之后更新名字将是一项困难的工作。

可在以下位置找到活动名称： **[!UICONTROL Advanced]** 选项卡。 不要留给他们名字 **[!UICONTROL query]**， **[!UICONTROL query1]**， **[!UICONTROL query11]**，但请为它们指定明确的名称，例如 **[!UICONTROL querySubscribedRecipients]**. 此名称将显示在日志中，如果适用，还会显示在SQL日志中，这有助于在配置工作流时对其进行调试。

### 第一个和最后一个活动 {#first-and-last-activities}

* 始终使用开始工作流 **[!UICONTROL Start]** 活动或 **[!UICONTROL Scheduler]** 活动。 在相关时，您还可以使用 **[!UICONTROL External signal]** 活动。
* 在构建工作流时，只能使用一个 **[!UICONTROL Scheduler]** 每个分支的活动。 如果工作流的同一分支具有多个调度程序（相互链接），则要执行的任务数量将呈指数级增长，这将使数据库严重过载。此规则还适用于具有的所有活动 **[!UICONTROL Scheduling & History]** 选项卡。 详细了解 [正在计划](scheduler.md).

  ![](assets/wf-scheduler.png)

* 使用 **[!UICONTROL End]** 每个工作流的活动。 这允许Adobe Campaign释放用于工作流中计算的临时空间。 有关更多信息，请参阅： [开始和结束](start-and-end.md).

### 活动中的Javascript {#javascript-within-an-activity}

初始化工作流活动时，您可能需要添加JavaScript。 这可以在活动的 **[!UICONTROL Advanced]** 选项卡中。

为了更轻松地找到工作流，我们建议在活动标签的开头和结尾使用双破折号，如下所示： — 我的标签 — 。

### 信号 {#signal}

大多数情况下，您不会知道从哪里调用信号。 为了避免此问题，请使用 **[!UICONTROL Comment]** 中的字段 **[!UICONTROL Advanced]** 信号活动的选项卡，用于记录此活动的信号的预期来源。

![](assets/workflow-signal-bp.png)

## 工作流更新 {#workflow-update}

不应直接更新生产工作流。 除非流程包括使用模板工作流创建营销活动，否则应首先在开发环境中测试流程。 完成此验证后，可以在生产环境中部署和启动工作流。

在开发或暂存环境中执行所有测试，而不是在生产环境中执行。 在这种情况下，无法确保性能。

归档的工作流可以保存在开发平台或测试平台上的归档文件夹中，但生产环境应尽可能保持干净。 如果旧工作流处于非活动状态，则应将其从生产环境中删除。
