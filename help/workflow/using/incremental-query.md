---
title: 增量查询
description: 进一步了解增量查询工作流活动
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---


# 增量查询{#incremental-query}

增量查询允许您根据某个标准定期选择目标，同时排除已针对该标准定位的人员。

已定位的填充按工作流实例和活动存储在内存中，即从同一模板启动的两个工作流不共享同一日志。 另一方面，基于同一工作流实例的同一增量查询的两个任务将使用同一日志。

该查询的定义方式与标准查询的定义方式相同，但会计划执行该。

**相关主题：**

* [用例：每季度列表更新(使用增量查询)](../../workflow/using/quarterly-list-update.md)
* [创建查询](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>如果增量查询的结果在其其中一个执行 **期间** 等于0，则暂停工作流，直到查询的下一个编程执行。 因此，在执行以下操作之前，不会处理遵循增量查询的过渡和活动。

操作步骤：

1. In the **[!UICONTROL Scheduling & History]** tab, select the **[!UICONTROL Schedule execution]** option. 创建任务后，该计划将保持活动状态，并且只会在为执行该查询指定的时间触发。 但是，如果禁用该选项，则立即执行查询, **并且一次性执行**。
1. 单击 **[!UICONTROL Change]** 按钮。

   在窗 **[!UICONTROL Schedule editing wizard]** 口中，您可以配置频率类型、事件循环和事件有效期。

   ![](assets/s_user_segmentation_wizard_11.png)

1. Click **[!UICONTROL Finish]** to save the schedule.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. 选项卡的下 **[!UICONTROL Scheduling & History]** 半部分允许您选择历史记录中要考虑的天数。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      已定位收件人可以从定位之日起记录最多天数。 如果此值为零，则从不从日志中清除收件人。

   * **[!UICONTROL Keep history when starting]**

      此选项允许您在启用活动时不清除日志。

   * **[!UICONTROL SQL table name]**

      通过此参数，可以使包含历史记录数据的默认SQL表过载。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这三组值标识查询所针对的人群。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通常是nms:收件人 **[!UICONTROL recCount]** )，是表中元素的数量。
