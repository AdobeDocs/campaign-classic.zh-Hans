---
title: SQL 代码和 JavaScript 代码
description: 进一步了解SQL和JavaScript代码工作流活动
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 5%

---


# SQL 代码和 JavaScript 代码{#sql-code-and-javascript-code}

## SQL代码 {#sql-code}

活动 **[!UICONTROL SQL code]** 执行SQL脚本。 脚本是JST模板。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   编辑器的中心区域包含要执行的脚本。 此脚本是JST模板，因此可以根据工作流上下文进行配置。

* **[!UICONTROL Processing errors]**

   请参阅处 [理错误](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## JavaScript代码和高级JavaScript代码 {#javascript-code}

**[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活动在工作流的上下文中执行JavaScript脚本。 有关脚本的详细信息，请参 [阅JavaScript脚本和模板](../../workflow/using/javascript-scripts-and-templates.md) 。

>[!NOTE]
>
>默认情况下，和活动的执 **[!UICONTROL JavaScript code]** 行 **[!UICONTROL Advanced JavaScript code]** 阶段不能超过1小时。 此延迟后，进程将中止，并显示错误消息，活动执行将失败。
>
>您可以在活动属性中 **[!UICONTROL Stop execution after]** 可用的字段中更改此延迟。

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**:编辑器的中心区域包含要执行的脚本。
   * **[!UICONTROL Processing errors]**:请参阅处 [理错误](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**:编辑器的第一个区域包含在第一次调用期间要执行的脚本。
   * **[!UICONTROL Next calls]**:编辑器的第二个区域包含在下次调用期间执行的脚本。
   * **[!UICONTROL Transitions]**:您可以定义多个活动输出过渡。
   * **[!UICONTROL Schedule]**:通 **[!UICONTROL Schedule]** 过选项卡可计划何时触发活动。
