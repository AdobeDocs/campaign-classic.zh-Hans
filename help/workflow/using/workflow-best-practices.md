---
product: campaign
title: 工作流最佳实践
description: 了解Campaign工作流最佳实践
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1687'
ht-degree: 12%

---

# 工作流最佳实践{#workflow-best-practices}



## 执行和性能 {#execution-and-performance}

下面列出了有关优化Campaign性能的常规准则，包括应用于工作流的最佳实践。

有关工作流执行的疑难解答指南，请参见 [《Campaign Classicv7生产指南》](../../production/using/workflow-execution.md).

### 日志 {#logs}

JavaScript方法 **[!UICONTROL logInfo()]** 是用于调试工作流的绝佳解决方案。 它很有用，但必须谨慎使用，尤其是对于经常运行的活动：它会使日志过载，并显着增加日志表的大小。 但您可能还需要 **[!UICONTROL logInfo()]**.

另外还有两个解决方案可提供帮助：

* **在两次执行之间保留中期群体的结果**

   此选项保留工作流两次执行之间的临时表。 它可以在工作流属性中找到 **[!UICONTROL General]** 选项卡，并可用于开发和测试目的，以监控数据和检查结果。 您可以在开发环境中使用此选项，但切勿在生产环境中使用。保留临时表可能会导致数据库的大小显著增加并最终达到大小限制。此外，这还将减慢备份速度。

   仅保留最后一次工作流执行的工作表。先前执行的工作表由清除 **[!UICONTROL cleanup]** 工作流，每天运行。

   >[!CAUTION]
   >
   >不得在生产工作流中勾选此选项。此选项用于分析结果，并且是仅为测试目的而设计，因此只能用于开发或暂存环境。

* **在日志中记录 SQL 查询**

   中提供 **[!UICONTROL Execution]** 选项卡中，此选项将记录工具从不同活动生成的所有SQL查询。 这是查看平台实际执行操作的好方法。 但是，此选项应仅在开发期间临时使用，而不应在生产时激活。

在不再需要日志时清除日志。 不会自动清除工作流历史记录：默认情况下保留所有消息。 可以通过清除历史记录 **[!UICONTROL File > Actions]** 菜单上，或者单击位于列表上方工具栏中的操作按钮。 选择清除历史记录。
要了解如何清除日志，请参阅此 [文档](starting-a-workflow.md).

### 工作流计划 {#workflow-planning}

* 尝试保持一天的稳定活动水平并避免出现峰值以防止实例过载。 为此，请在一天中平均分配工作流的开始时间。
* 安排数据加载过夜，以减少资源争用。
* 长工作流可能会对服务器和数据库资源产生影响。 拆分最长的工作流以减少处理时间。
* 要缩短总体运行时间，请用简化且更快的活动来取代耗时的活动。
* 避免同时运行20个以上的工作流。 如果同时执行的工作流过多，系统可能会耗尽资源，变得不稳定。 有关工作流可能未启动原因的更多信息，请参阅此 [文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### 工作流执行 {#workflow-execution}

**请勿将工作流计划为运行时间超过每15分钟一次** 因为它可能会影响整体系统性能，并在数据库中创建块。

**避免使工作流处于暂停状态**. 如果您创建临时工作流，请确保该工作流能够正确完成并且不会停留在 **[!UICONTROL paused]** 省/州。 如果暂停，则意味着您需要保留临时表，从而增加数据库的大小。 在“工作流属性”下分配工作流主管，以便在工作流失败或系统暂停时发送警报。

要避免工作流处于暂停状态，请执行以下操作：

* 请定期检查您的工作流，以确保没有意外错误。
* 使您的工作流尽可能简单，例如，通过将大型工作流拆分到多个不同的工作流中。 您可以使用 **[!UICONTROL External signal]** 活动根据其他工作流的执行触发其执行。
* 避免在工作流中禁用流活动，使线程处于打开状态，并导致许多临时表，占用大量空间。 不要将活动保留在 **[!UICONTROL Do not enable]** 或 **[!UICONTROL Enable but do not execute]** 工作流中的状态。

**停止未使用的工作流**. 保持运行的工作流保持与数据库的连接。

**仅在极少数情况下使用无条件停止**. 请勿定期使用此操作。 如果对工作流生成到数据库的连接不执行干净关闭，则会影响性能。

**不要在同一工作流上执行多个停止请求**. 停止工作流是一个异步过程：请求已注册，然后工作流服务器或服务器取消正在进行的操作。 因此，停止工作流实例可能需要一些时间，尤其是当工作流在多台服务器上运行时，每台服务器都必须控制以取消正在进行的任务。 要避免出现任何问题，请等待停止操作完成，避免多次停止工作流。

### 在引擎选项中执行 {#execute-in-the-engine-option}

在 **[!UICONTROL Workflow properties]** 窗口，不要选中 **[!UICONTROL Execute in the engine]** 选项。 启用此选项后，工作流具有优先权，并且所有其他工作流都由工作流引擎停止，直到该工作流完成。

![](assets/wf-execute-in-engine.png)

## 工作流属性 {#workflow-properties}

### 工作流文件夹 {#workflow-folders}

Adobe建议您在专用文件夹中创建工作流。

如果工作流影响整个平台（例如清理流程），您可以考虑在内置中添加子文件夹 **[!UICONTROL Technical Workflows]** 文件夹。

### 工作流命名 {#workflow-naming}

Adobe 建议为工作流赋予正确的名称和标签，这样工作流没有按照预期的方式执行，可轻松地找到并排除故障：填写工作流的描述字段，在其中加入执行流程的摘要，以便操作员能够轻松理解。

如果工作流是涉及多个工作流的流程的一部分，则在输入标签时可以很明确；使用数字是对工作流进行排序（按标签）的绝佳方法。

例如：

* 001 — 导入 — 导入收件人
* 002 — 导入 — 导入销售
* 003 — 导入 — 导入销售详细信息
* 010 — 导出 — 导出投放日志
* 011 — 导出 — 导出跟踪日志

### 工作流严重性 {#workflow-severity}

您可以在工作流属性中配置工作流的严重性，只需在 **[!UICONTROL Execution]** 选项卡：

* 正常
* 生产
* 严重

创建工作流时提供此信息将有助于您了解所配置进程的严重性。

此选项对除营销活动工作流之外的工作流没有功能影响。

如果营销活动具有多个应同时运行的流程，则优先执行具有较高严重性的营销活动工作流（作为营销活动/操作的一部分创建的工作流）。 默认情况下，根据选项NmsOperation_LimitConcurrency，营销活动中只能同时运行10个进程。 例如，如果营销策划包含25个工作流，则具有较高严重性的工作流随后将在第一个包含10个进程池中执行。

### 工作流监测 {#workflow-monitoring}

应监控在生产环境中运行的所有计划工作流，以便在发生错误时收到警报。

在工作流属性中，选择一个Supervisor组(默认 **[!UICONTROL Workflow supervisors]** 或自定义组。 确保至少有一个操作员属于此组，并设置了电子邮件。

在开始构建工作流之前，请记得定义工作流主管。 如果出现错误，他们将收到电子邮件通知。 有关更多信息，请参阅 [管理错误](monitoring-workflow-execution.md#managing-errors).

定期查看 **[!UICONTROL Monitoring]** 选项卡以查看活动工作流的整体状态。 有关更多信息，请参阅 [实例监督](monitoring-workflow-execution.md#instance-supervision).

通过Workflow HeatMap，Adobe Campaign平台管理员可以监控实例的负载并相应地规划工作流。 有关更多信息，请参阅 [工作流监测](heatmap.md).

## 使用活动 {#using-activities}

>[!CAUTION]
>
>您可以在同一工作流中复制和粘贴活动。 但是，我们不建议跨不同工作流复制粘贴活动。 在执行目标工作流时，附加到投放和调度程序等活动的某些设置可能会导致冲突和错误。 相反，我们建议您  **复制** 工作流。 有关更多信息，请参阅 [复制工作流](building-a-workflow.md#duplicating-workflows).

### 活动的名称 {#name-of-the-activity}

在开发工作流时，所有活动都将有一个名称，所有Adobe Campaign对象也将有一个名称。 虽然该名称由工具生成，但我们建议您在配置该名称时将其重命名为明确的名称。 稍后执行此操作的风险在于，它可能会使用另一个先前活动的名称中断工作流中的活动。 因此，事后更新名字会很困难。

可在以下位置找到活动名称： **[!UICONTROL Advanced]** 选项卡。 不要留给他们名字 **[!UICONTROL query]**， **[!UICONTROL query1]**， **[!UICONTROL query11]**，但请为它们指定明确的名称，例如 **[!UICONTROL querySubscribedRecipients]**. 此名称将显示在日志中，如果适用，还会显示在SQL日志中，这有助于在配置工作流时对其进行调试。

### 第一个和最后一个活动 {#first-and-last-activities}

* 始终使用启动工作流 **[!UICONTROL Start]** 活动或 **[!UICONTROL Scheduler]** 活动。 在相关时，您还可以使用 **[!UICONTROL External signal]** 活动。
* 在构建工作流时，仅使用一个 **[!UICONTROL Scheduler]** 每个分支的活动。 如果工作流的同一分支具有多个调度程序（相互链接），则要执行的任务数量将呈指数级增长，这将使数据库严重过载。此规则还适用于具有的所有活动 **[!UICONTROL Scheduling & History]** 选项卡。 详细了解 [计划](scheduler.md).

   ![](assets/wf-scheduler.png)

* 使用 **[!UICONTROL End]** 每个工作流的活动。 这允许Adobe Campaign释放用于工作流中计算的临时空间。 有关更多信息，请参阅： [开始和结束](start-and-end.md).

### 活动中的Javascript {#javascript-within-an-activity}

初始化工作流活动时，您可能需要添加JavaScript。 这可以在活动的 **[!UICONTROL Advanced]** 选项卡中列出的所有选项卡。

为了更轻松地找到工作流，我们建议在活动标签的开始和结束位置使用双破折号，如下所示： — 我的标签 — 。

### 信号 {#signal}

大多数情况下，您不会知道从哪里调用信号。 为避免此问题，请使用 **[!UICONTROL Comment]** 中的字段 **[!UICONTROL Advanced]** 信号活动的选项卡，用于记录此活动的信号的预期来源。

![](assets/workflow-signal-bp.png)

## 工作流更新 {#workflow-update}

不应直接更新生产工作流。 除非流程包括使用模板工作流创建活动，否则应首先在开发环境中测试流程。 在此验证后，可以部署工作流并在生产环境中启动该工作流。

在开发或暂存环境中执行所有测试，而不是在生产环境中执行。 在这种情况下，无法确保性能。

存档的工作流可以保存在开发或测试平台上的存档文件夹中，但生产环境应尽可能保持干净。 如果旧工作流处于非活动状态，则应将其从生产环境中删除。
