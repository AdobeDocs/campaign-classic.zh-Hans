---
product: campaign
title: SQL 代码和 JavaScript 代码
description: 了解有关SQL和JavaScript代码工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 12%

---

# SQL 代码和 JavaScript 代码{#sql-code-and-javascript-code}



## SQL 代码 {#sql-code}

An **[!UICONTROL SQL code]** 活动执行SQL脚本。 脚本是JST模板。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

  编辑器的中心区域包含要执行的脚本。 此脚本是一个JST模板，因此可以根据工作流上下文进行配置。

* **[!UICONTROL Processing errors]**

  请参阅 [正在处理错误](monitoring-workflow-execution.md#processing-errors).

## JavaScript代码和高级JavaScript代码 {#javascript-code}

**[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活动在工作流上下文中执行JavaScript脚本。 有关脚本的更多信息，请参阅以下章节：

* [JavaScript 脚本和模板](javascript-scripts-and-templates.md)
* [工作流中的 JavaScript 代码示例](javascript-in-workflows.md)

### 执行延迟 {#exec-delay}

从20.2版本开始，向添加了执行延迟 **[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活动。 默认情况下，执行阶段不能超过1小时。 在此延迟后，进程将中止，并显示一条错误消息，活动执行将失败。

您可以在 **[!UICONTROL Stop execution after]** 在这些活动中可用的字段。

要忽略此限制，您需要将值设置为 **0**.

### JavaScript 代码 {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**：编辑器的中心区域包含要执行的脚本。

* **[!UICONTROL Process errors]**：请参阅 [正在处理错误](monitoring-workflow-execution.md#processing-errors).

### 高级 JavaScript 代码 {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**：编辑器的第一个区域包含要在第一次调用期间执行的脚本。
* **[!UICONTROL Next calls]**：编辑器的第二个区域包含要在下次调用期间执行的脚本。
* **[!UICONTROL Transitions]**：您可以定义多个活动输出过渡。
* **[!UICONTROL Schedule]**：和 **[!UICONTROL Schedule]** 选项卡允许您计划何时触发活动。

高级JavaScript是一个持续性任务，如果未标记为已完成，则会定期回调。 要终止任务并防止将来出现撤回情况，您必须使用 **task.setCompleted()** 中的方法 **[!UICONTROL Next calls]** 部分：

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
