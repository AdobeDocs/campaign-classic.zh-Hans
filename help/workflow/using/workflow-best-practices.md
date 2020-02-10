---
title: 工作流最佳实践
seo-title: 工作流最佳实践
description: 工作流最佳实践
seo-description: null
page-status-flag: never-activated
uuid: 56b04004-5d96-4169-9494-3d04284d5a3d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 3da951ef-5775-4593-8301-f143c71edc19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4b4ec97e52a494dd88b2516650ae514294f00934

---


# 工作流最佳实践{#workflow-best-practices}

## 执行和性能 {#execution-and-performance}

下面列出了有关优化Campaign效果的一般准则，包括适用于您的工作流的最佳实践。

本节还提供了与工作流执行相关的疑难解答 [指南](../../production/using/workflow-execution.md)。

### 日志 {#logs}

JavaScript方法是 **[!UICONTROL logInfo()]** 调试工作流的一个很好的解决方案。 它很有用，但必须谨慎使用，尤其是对于经常运行的活动：它可以使日志过载，并显着增加日志表的大小。 但你可能还需要更多 **[!UICONTROL logInfo()]**。

还提供两个其他解决方案来帮助：

* **在两次处决之间保留临时人口的结果**

   此选项可在工作流的两个执行操作之间保留临时表。 它位于工作流属性的选项卡 **[!UICONTROL General]** 中，可用于开发和测试目的以监控数据和检查结果。 您可以在开发环境中使用此选项，但绝不能在生产环境中使用它。 保留临时表可能导致数据库的大小显着增加，并最终达到大小限制。 此外，它还会减慢备份速度。

   只保留上次执行工作流的工作表。 以前执行的工作表将由每天 **[!UICONTROL cleanup]** 运行的工作流清除。

   >[!CAUTION]
   >
   >在生产工作流程中，不得选中此选项。 此选项用于分析结果，并且仅用于测试目的，因此只能用于开发或升级环境。

* **日志中的SQL查询**

   此选项在工 **[!UICONTROL Execution]** 作流属性的选项卡中可用，它将记录该工具从不同活动生成的所有SQL查询。 这是查看平台实际执行哪些操作的好方法。 但是，此选项仅应在开发过程中暂时使用，而不应在生产时激活。

当日志不再需要时清除它们。 工作流历史记录不会自动清除：默认情况下，所有消息都会保留。 可以通过菜单或单击列 **[!UICONTROL File > Actions]** 表上方工具栏中的“操作”按钮来清除历史记录。 选择清除历史记录。
要了解如何清除日志，请参阅此 [文档](../../workflow/using/executing-a-workflow.md#actions-toolbar)。

### 工作流计划 {#workflow-planning}

* 尝试在一天中保持一个稳定的活动级别并避免出现峰值，以防止实例过载。 为此，请在一天中平均分配工作流开始时间。
* 安排夜间数据加载以减少资源争用。
* 长的工作流程可能会对服务器和数据库资源产生潜在影响。 拆分最长的工作流以缩短处理时间。
* 要缩短总体运行时间，请用简化的、更快的活动取代耗时的活动。
* 避免同时运行20多个工作流。 当同时执行过多的工作流时，系统资源会耗尽，变得不稳定。 有关工作流可能未启动的原因的详细信息，请参阅此 [文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html)。

### 工作流执行 {#workflow-execution}

最好不要将工作流计划为每15分钟以上运行一次，因为它可能会妨碍总体系统性能并在数据库中创建块。

避免将工作流保留为暂停状态。 如果创建临时工作流，请确保它能够正确完成并且不处于状 **[!UICONTROL paused]** 态。 如果暂停，则表示您需要保留临时表，从而增加数据库的大小。 在“工作流属性”下分配“工作流监督者”，以在工作流失败或系统暂停时发送警报。

要避免工作流处于暂停状态，请执行以下操作：

* 定期检查您的工作流，以确保没有意外错误。
* 使工作流尽可能简单，例如，将大型工作流分成多个不同的工作流。 您可以使用活 **[!UICONTROL External signal]** 动来触发基于其他工作流执行的执行。
* 避免在工作流中禁用流的活动，使线程处于打开状态并导致许多临时表占用大量空间。 请勿将活动保留在工 **[!UICONTROL Do not enable]** 作流 **[!UICONTROL Enable but do not execute]** 中或保留状态。

此外，停止未使用的工作流。 持续运行的工作流会维护与数据库的连接。

仅在最少情况下使用无条件停止。 请勿定期使用此操作。 对工作流与数据库生成的连接执行清理关闭会影响性能。

### 在引擎选项中执行 {#execute-in-the-engine-option}

在窗口 **[!UICONTROL Workflow properties]** 中，不要选中该 **[!UICONTROL Execute in the engine]** 选项。 启用此选项后，工作流将优先处理，所有其他工作流将由工作流引擎停止，直到此工作流完成。

![](assets/wf-execute-in-engine.png)

## 工作流属性 {#workflow-properties}

### 工作流文件夹 {#workflow-folders}

Adobe建议您在专用文件夹中创建工作流。

如果工作流影响整个平台（例如清理过程），您可以考虑在内置文件夹中添加子文 **[!UICONTROL Technical Workflows]** 件夹。

### 工作流命名 {#workflow-naming}

由于如果它们没有以预期的方式执行，可以更轻松地查找和排除故障，Adobe建议为工作流提供正确的名称和标签：填写工作流的描述字段以汇总要执行的过程，以便操作员能够轻松理解它。

如果工作流是涉及多个工作流的流程的一部分，则在输入标签时可以明确显示；使用数字是对工作流（按标签）进行排序的极好方法。

例如：

* 001 —— 导入——导入收件人
* 002 —— 导入——导入销售
* 003 —— 导入——导入销售详细信息
* 010 —— 导出——导出交付日志
* 011 —— 导出——导出跟踪日志

### 工作流严重性 {#workflow-severity}

您可以在以下选项卡的工作流属性中配置工作流的严 **[!UICONTROL Execution]** 重性：

* 正常
* 制作
* 关键

在创建工作流时提供此信息将帮助您了解所配置流程的严重性。

除营销活动工作流之外，此选项对工作流没有任何功能影响。

如果营销活动有多个进程应同时运行，则会以优先级执行具有较高严重性的营销活动工作流（作为营销活动／操作的一部分创建的工作流）。 根据NmsOperation_LimitConcurrency选项，默认情况下，在营销活动中只能同时运行10个进程。 例如，如果营销活动包含25个工作流，则在10个进程的第一个池中执行具有较高严重性的工作流。

### 工作流监控 {#workflow-monitoring}

应监视在生产环境上运行的所有计划工作流，以便在出错时收到警告。

在工作流属性中，选择一个主管组(默认组或自 **[!UICONTROL Workflow supervisors]** 定义组)。 确保至少有一个操作员属于此组，并设置了电子邮件。

在开始构建工作流之前，请务必定义工作流监管器。 如果出错，将通过电子邮件通知他们。 For more on this, refer to [Managing errors](../../workflow/using/monitoring-workflow-execution.md#managing-errors).

定期检查 **[!UICONTROL Monitoring]** 范围，以查看活动工作流程的整体状态。 For more on this, refer to [Instance supervision](../../workflow/using/monitoring-workflow-execution.md#instance-supervision).

Workflow HeatMap使Adobe Campaign平台管理员能够相应地监控实例负载和计划工作流。 For more on this, refer to [Workflow monitoring](../../workflow/using/heatmap.md).

## 使用活动 {#using-activities}

>[!CAUTION]
>
>您可以在同一工作流中复制和粘贴活动。 但是，我们不建议跨不同的工作流复制粘贴活动。 在执行目标工作流时，某些附加到活动（如“提交”和“调度程序”）的设置可能会导致冲突和错误。 我们建议您复制工 **作流** 。 有关详细信息，请参阅复 [制工作流](../../workflow/using/building-a-workflow.md#duplicating-workflows)。

### 活动的名称 {#name-of-the-activity}

在开发工作流程时，所有活动都将具有名称，所有Adobe Campaign对象也将具有名称。 当该工具生成名称时，我们建议您在配置时使用显式名称对其重命名。 以后这样做的风险在于，它可能会使用其他先前活动的名称中断使用活动的工作流。 因此，更新名称是一项困难的工作。

活动名称可在选项卡中找 **[!UICONTROL Advanced]** 到。 不要将其留为名 **[!UICONTROL query]**&#x200B;称， **[!UICONTROL query1]**&#x200B;但 **[!UICONTROL query11]**&#x200B;请为其指定名称，如 **[!UICONTROL querySubscribedRecipients]**。 此名称将显示在日志中，如果适用于SQL日志，此名称将有助于在配置工作流时调试该工作流。

### 第一个和最后一个活动 {#first-and-last-activities}

* 始终以活动或活动 **[!UICONTROL Start]** 启动工作 **[!UICONTROL Scheduler]** 流。 相关时，您还可以使用活 **[!UICONTROL External signal]** 动。
* 在构建工作流时，每个分支只 **[!UICONTROL Scheduler]** 使用一个活动。 如果工作流的同一分支有多个调度程序（相互链接），则要执行的任务数将以指数级数增加，这将使数据库过载。 此规则也适用于具有选项卡的所有 **[!UICONTROL Scheduling & History]** 活动。 进一步了 [解计划](../../workflow/using/scheduler.md)。

   ![](assets/wf-scheduler.png)

* 将活动 **[!UICONTROL End]** 用于每个工作流程。 这样，Adobe Campaign就可以释放用于工作流中计算的临时空间。 有关详细信息，请参阅：开 [始和结束](../../workflow/using/start-and-end.md)。

### 活动中的Javascript {#javascript-within-an-activity}

在初始化工作流活动时，您可能希望添加JavaScript。 这可以在活动的活动选项卡 **[!UICONTROL Advanced]** 中完成。

为了更轻松地发现工作流，我们建议在活动标签的开始和结尾使用双破折号，如下所示：—我的标签—.

### 信号 {#signal}

大多数时候，您都不知道信号从哪里被调用。 为避免出现此问题，请使用信 **[!UICONTROL Comment]** 号活动 **[!UICONTROL Advanced]** 选项卡中的字段记录此活动的信号的预期来源。

![](assets/workflow-signal-bp.png)

## 工作流更新 {#workflow-update}

不应直接更新生产工作流。 除非该流程包含使用模板工作流创建营销活动，否则应首先在开发环境中测试流程。 验证后，可以在生产上部署和启动工作流。

在开发或暂存环境中而不是在生产环境中执行所有测试。 在这种情况下，无法确保性能。

归档的工作流可以保存在开发或测试平台上的“归档”文件夹中，但生产环境应尽可能保持干净。 如果旧的工作流处于非活动状态，则应从生产环境中删除它们。
