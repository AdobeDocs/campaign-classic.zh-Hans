---
title: 增量查询
seo-title: 增量查询
description: 增量查询
seo-description: null
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aa192d975a08246ba684940fff3d33853d7d9345
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 4%

---


# 增量查询{#incremental-query}

增量查询允许您根据某个标准定期选择目标，同时排除已针对该标准定位的人员。

The population already targeted is stored in the memory by workflow instance and by activity, i.e. two workflows started from the same template do not share the same log. 另一方面，基于同一工作流实例的同一增量查询的两个任务将使用同一日志。

该查询的定义方式与标准查询的定义方式相同，但会计划执行该。

**相关主题：**

* [用例： 每季度列表更新(使用增量查询)](../../workflow/using/quarterly-list-update.md)
* [创建查询](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>If the result of an incremental query is equal to **0** during one of its executions, the workflow is paused until the query&#39;s next programmed execution. 因此，在执行以下操作之前，不会处理遵循增量查询的过渡和活动。

操作步骤：

1. In the **[!UICONTROL Scheduling & History]** tab, select the **[!UICONTROL Schedule execution]** option. The task remains active once it has been created and will only be triggered at the times specified by the schedule for executing the query. However, if the option is disabled, the query is executed immediately **and in one go**.
1. 单击&#x200B;**[!UICONTROL Change]**&#x200B;按钮。

   In the **[!UICONTROL Schedule editing wizard]** window, you can configure the type of frequency, event recurrence and event validity period.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Click **[!UICONTROL Finish]** to save the schedule.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. The lower section of the **[!UICONTROL Scheduling & History]** tab allows you to select the number of days to be taken into account in the history.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      Recipients already targeted can be logged a maximum number of days from the day they were targeted. If this value is zero, the recipients are never purged from the log.

   * **[!UICONTROL Keep history when starting]**

      This option lets you not purge the log when the activity is enabled.

   * **[!UICONTROL SQL table name]**

      通过此参数，可以使包含历史记录数据的默认SQL表过载。

## Output parameters {#output-parameters}

* tableName
* 模式
* recCount

This set of three values identifies the population targeted by the query. **[!UICONTROL tableName]** is the name of the table that records the target identifiers, **[!UICONTROL schema]** is the schema of the population (usually nms:recipient) and **[!UICONTROL recCount]** is the number of elements in the table.
