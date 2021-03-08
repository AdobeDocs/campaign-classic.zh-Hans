---
solution: Campaign Classic
product: campaign
title: 工作流最佳实践
description: 学习活动工作流程最佳实践
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 5%

---


# 工作流最佳实践{#workflow-best-practices}

## 执行和性能{#execution-and-performance}

以下是有关优化活动性能的一般准则，包括适用于工作流的最佳实践。

[本节](../../production/using/workflow-execution.md)中还提供与工作流执行相关的疑难解答指南。

### 日志{#logs}

JavaScript方法&#x200B;**[!UICONTROL logInfo()]**&#x200B;是调试工作流的绝佳解决方案。 它很有用，但必须谨慎使用，特别是对于经常运行的活动:它可以使日志过载，并显着增加日志表的大小。 但您可能还需要多于&#x200B;**[!UICONTROL logInfo()]**。

还提供两个其他解决方案，以帮助您：

* **在两次处决之间保留临时人口的结果**

   此选项在工作流的两个执行之间保留临时表。 它位于工作流属性的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，可用于开发和测试以监控数据和检查结果。 您可以在开发环境中使用此选项，但绝不能在生产环境中使用它。 保留临时表可能导致数据库的大小显着增加，最终达到大小限制。 此外，这会减缓备份速度。

   只保留上次执行工作流时的工作表。 以前执行中的工作表将由每天运行的&#x200B;**[!UICONTROL cleanup]**&#x200B;工作流清除。

   >[!CAUTION]
   >
   >不得在生产工作流中选中此选项。 此选项用于分析结果，仅用于测试目的，因此只能用于开发或暂存环境。

* **在日志中记录SQL查询**

   在工作流属性的&#x200B;**[!UICONTROL Execution]**&#x200B;选项卡中，此选项将记录该工具从不同查询生成的所有SQL活动。 这是查看平台实际执行的内容的好方法。 但是，此选项仅应在开发期间暂时使用，而不应在生产时激活。

当日志不再需要时清除它们。 工作流历史记录不会自动清除：默认情况下，所有消息都保留。 可以通过&#x200B;**[!UICONTROL File > Actions]**菜单或单击列表上方工具栏中的“操作”按钮清除历史记录。 选择清除历史记录。
要了解如何清除日志，请参阅此[文档](../../workflow/using/starting-a-workflow.md)。

### 工作流计划{#workflow-planning}

* 尝试在一天中保持稳定的活动级别并避免出现峰值，以防止实例过载。 为此，请在一天中平均分配工作流开始时间。
* 计划数据以隔夜加载，以减少资源争用。
* 长工作流可能会对服务器和数据库资源产生潜在影响。 拆分最长的工作流以缩短处理时间。
* 要缩短总体运行时间，请将耗时的活动替换为简化的、更快的活动。
* 避免同时运行20多个工作流。 当同时执行工作流过多时，系统会耗尽资源，变得不稳定。 有关工作流可能未启动的原因的详细信息，请参阅此[文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html)。

### 工作流执行 {#workflow-execution}

最好不要将工作流计划为每15分钟以上运行一次，因为它可能会妨碍总体系统性能并在数据库中创建块。

避免将工作流置于暂停状态。 如果创建临时工作流，请确保它能够正确完成且不能保持&#x200B;**[!UICONTROL paused]**&#x200B;状态。 如果暂停，则表示需要保留临时表，从而增加数据库的大小。 在工作流属性下分配工作流监管器，以在工作流失败或系统暂停时发送警报。

要避免工作流处于暂停状态：

* 定期检查工作流，确保没有意外错误。
* 使工作流尽可能简单，例如，将大工作流拆分为多个不同工作流。 您可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活动根据其他工作流的执行触发执行。
* 避免禁用活动，使工作流中的流处于打开状态并导致许多临时表占用大量空间。 不要将活动保留在工作流的&#x200B;**[!UICONTROL Do not enable]**&#x200B;或&#x200B;**[!UICONTROL Enable but do not execute]**&#x200B;状态中。

此外，停止未使用的工作流。 继续运行的工作流会维护与数据库的连接。

在最少情况下，只使用无条件停止。 请勿定期使用此操作。 不对由工作流生成的连接执行干净关闭会影响性能。

### 在引擎选项{#execute-in-the-engine-option}中执行

在&#x200B;**[!UICONTROL Workflow properties]**&#x200B;窗口中，从不检查&#x200B;**[!UICONTROL Execute in the engine]**&#x200B;选项。 启用此选项后，工作流将优先处理，工作流引擎将停止所有其他工作流，直到完成此操作。

![](assets/wf-execute-in-engine.png)

## 工作流属性 {#workflow-properties}

### 工作流文件夹{#workflow-folders}

Adobe建议您在专用文件夹中创建工作流。

如果工作流影响整个平台(例如，清理进程)，您可以考虑在内置&#x200B;**[!UICONTROL Technical Workflows]**&#x200B;文件夹中添加子文件夹。

### 工作流命名{#workflow-naming}

Adobe 建议为工作流赋予正确的名称和标签，这样工作流没有按照预期的方式执行，可轻松地找到并排除故障：填写工作流的描述字段，在其中加入执行流程的摘要，以便操作员能够轻松理解。

如果工作流是涉及多个工作流的流程的一部分，则在输入标签时可以明确；使用数字是对工作流（按标签）排序的绝佳方式。

例如：

* 001 — 导入 — 导入收件人
* 002 — 导入 — 导入销售
* 003 — 导入 — 导入销售详细信息
* 010 — 导出 — 导出投放日志
* 011 — 导出 — 导出跟踪日志

### 工作流严重性{#workflow-severity}

您可以在工作流属性的&#x200B;**[!UICONTROL Execution]**&#x200B;选项卡中配置工作流的严重性：

* 正常
* Production
* 关键

在创建工作流时提供此信息将帮助您了解所配置进程的严重性。

此选项对除活动工作流之外的工作流没有功能影响。

以优先级执行活动工作流(作为活动/操作的一部分创建的工作流)，以防活动有多个进程应同时运行。 根据NmsOperation_LimitConcurrency选项，默认情况下，在活动中只能同时运行10个进程。 例如，如果活动包含25个工作流，则在10个进程的第一个池中执行严重性较高的工作流。

### 工作流监视{#workflow-monitoring}

您在生产环境上运行的所有计划工作流都应受到监视，以便在出错时收到警告。

在工作流属性中，选择一个主管组（默认的&#x200B;**[!UICONTROL Workflow supervisors]**&#x200B;或自定义组）。 确保至少有一个操作员属于此组，并设置了电子邮件。

在开始构建工作流之前，请记住定义工作流监管器。 出错时，将通过电子邮件通知他们。 有关详细信息，请参阅[管理错误](../../workflow/using/monitoring-workflow-execution.md#managing-errors)。

定期检查&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡以视图活动工作流的整体状态。 有关详细信息，请参阅[实例监视](../../workflow/using/monitoring-workflow-execution.md#instance-supervision)。

Workflow HeatMap使Adobe Campaign平台管理员能够监控实例上的负载并相应地规划工作流。 有关详细信息，请参阅[工作流监视](../../workflow/using/heatmap.md)。

## 使用活动{#using-activities}

>[!CAUTION]
>
>您可以在同一工作流中复制和粘贴活动。 但是，我们不建议跨不同的工作流复制粘贴活动。 某些附加到活动(如投放和调度程序)的设置可能会在执行目标工作流时导致冲突和错误。 我们建议您&#x200B;**重复**&#x200B;工作流。 有关详细信息，请参阅[复制工作流](../../workflow/using/building-a-workflow.md#duplicating-workflows)。

### 活动{#name-of-the-activity}的名称

在开发工作流时，所有活动都将有一个名称，所有Adobe Campaign对象也一样。 当工具生成该名称时，我们建议您在配置时使用显式名称对其重命名。 以后执行该操作的风险在于，它可能会使用另一个以前活动的名称，用活动中断工作流。 因此，更新姓名将是一项困难的工作。

活动名称位于&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中。 不要将它们保留为&#x200B;**[!UICONTROL query]**、**[!UICONTROL query1]**、**[!UICONTROL query11]**，但请为它们指定显式名称，如&#x200B;**[!UICONTROL querySubscribedRecipients]**。 此名称将显示在日志中，如果适用于SQL日志，这将有助于在配置工作流时调试该工作流。

### 第一个和最后一个活动{#first-and-last-activities}

* 始终使用&#x200B;**[!UICONTROL Start]**&#x200B;活动或&#x200B;**[!UICONTROL Scheduler]**&#x200B;活动开始您的工作流。 相关时，您还可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活动。
* 在构建工作流时，每个分支只使用一个&#x200B;**[!UICONTROL Scheduler]**&#x200B;活动。 如果工作流的同一分支具有多个调度程序（相互链接），则要执行的任务数量将呈指数级增长，这将使数据库严重过载。此规则也适用于具有&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;选项卡的所有活动。 了解有关[计划](../../workflow/using/scheduler.md)的详细信息。

   ![](assets/wf-scheduler.png)

* 对每个工作流使用&#x200B;**[!UICONTROL End]**&#x200B;活动。 这样，Adobe Campaign就可以释放用于工作流内计算的临时空间。 有关详细信息，请参阅：[开始和结束](../../workflow/using/start-and-end.md)。

### 活动{#javascript-within-an-activity}中的Javascript

在初始化工作流活动时，您可能希望添加JavaScript。 这可以在活动的&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中完成。

为了更轻松地发现工作流，我们建议在多次标签的开始和结尾使用活动短划线，如下所示： — 我的标签 — 

### 信号{#signal}

大多数时候，你都不知道信号从哪里被调用。 为避免此问题，请使用信号活动&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Comment]**&#x200B;字段来文档此活动的信号的预期来源。

![](assets/workflow-signal-bp.png)

## 工作流更新{#workflow-update}

不应直接更新生产工作流。 除非该过程包含使用模板工作流创建活动，否则应首先在开发环境上测试流程。 验证后，可以在生产上部署和启动工作流。

在开发或分阶环境(而非生产环境)中执行所有测试。 在这种情况下，无法确保业绩。

归档的工作流可以保存在开发平台或测试平台上的“归档”文件夹中，但生产环境应尽可能保持干净。 如果旧工作流处于非活动状态，则应从生产环境中删除它们。
