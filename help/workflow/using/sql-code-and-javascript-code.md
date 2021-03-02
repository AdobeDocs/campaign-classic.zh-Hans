---
solution: Campaign Classic
product: campaign
title: SQL 代码和 JavaScript 代码
description: 进一步了解SQL和JavaScript代码工作流活动
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: add0efb4efd5a37129c649b942799622947f3143
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---


# SQL 代码和 JavaScript 代码{#sql-code-and-javascript-code}

## SQL代码{#sql-code}

**[!UICONTROL SQL code]**&#x200B;活动执行SQL脚本。 脚本是JST模板。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   编辑器的中心区域包含要执行的脚本。 此脚本是JST模板，因此可以根据工作流上下文进行配置。

* **[!UICONTROL Processing errors]**

   请参阅[处理错误](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## JavaScript代码和高级JavaScript代码{#javascript-code}

**[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活动在工作流的上下文中执行JavaScript脚本。有关脚本的详细信息，请参阅[JavaScript脚本和模板](../../workflow/using/javascript-scripts-and-templates.md)部分。

### 执行延迟{#exec-delay}

从20.2版本开始，已向&#x200B;**[!UICONTROL JavaScript code]**&#x200B;和&#x200B;**[!UICONTROL Advanced JavaScript code]**&#x200B;活动添加执行延迟。 默认情况下，执行阶段不能超过1小时。 在此延迟后，进程将中止，并显示错误消息，活动执行将失败。

您可以在这些活动中可用的&#x200B;**[!UICONTROL Stop execution after]**&#x200B;字段中更改此延迟。

要忽略此限制，您需要将值设置为&#x200B;**0**。

### JavaScript代码{#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**:编辑器的中心区域包含要执行的脚本。

* **[!UICONTROL Process errors]**:请参阅处 [理错误](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

### 高级JavaScript代码{#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**:编辑器的第一个区域包含要在第一次调用期间执行的脚本。
* **[!UICONTROL Next calls]**:编辑器的第二个区域包含在下次调用期间执行的脚本。
* **[!UICONTROL Transitions]**:您可以定义多个活动输出过渡。
* **[!UICONTROL Schedule]**:通 **[!UICONTROL Schedule]** 过选项卡可计划何时触发活动。

高级JavaScript是一个持续性任务，如果尚未标记为已完成，将定期调用它。 要终止任务并防止将来的召回，必须使用&#x200B;**[!UICONTROL Next calls]**&#x200B;部分中的&#x200B;**任务.setCompleted()**&#x200B;方法：

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
