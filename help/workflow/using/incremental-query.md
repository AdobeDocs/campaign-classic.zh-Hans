---
solution: Campaign Classic
product: campaign
title: 增量查询
description: 进一步了解增量查询工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---


# 增量查询{#incremental-query}

增量查询允许您根据某个标准定期选择目标，同时排除已针对该标准定位的人员。

已定位的填充按工作流实例和活动存储在内存中，即从同一模板启动的两个工作流不共享同一日志。 另一方面，基于同一工作流实例的相同增量查询的两个任务将使用相同的日志。

该查询的定义方式与标准查询的定义方式相同，但会计划其执行。

**相关主题：**

* [用例：每季度列表更新(使用增量查询)](../../workflow/using/quarterly-list-update.md)
* [创建查询](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>如果增量查询的结果在其执行之一期间等于&#x200B;**0**，则暂停工作流，直到查询的下次编程执行。 因此，在执行以下操作之前，不会处理增量查询后面的过渡和活动。

操作步骤：

1. 在&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Schedule execution]**&#x200B;选项。 创建任务后，该查询将保持活动状态，并且仅在计划指定的时间触发该。 但是，如果禁用了该选项，则立即执行查询&#x200B;**，并执行一次操作**。
1. 单击 **[!UICONTROL Change]** 按钮。

   在&#x200B;**[!UICONTROL Schedule editing wizard]**&#x200B;窗口中，可以配置频率类型、事件循环和事件有效期。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;保存计划。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. **[!UICONTROL Scheduling & History]**&#x200B;选项卡的下半部分允许您选择历史记录中要考虑的天数。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      已定位的收件人可以从其定位之日起记录最大天数。 如果此值为零，则不会从日志中清除收件人。

   * **[!UICONTROL Keep history when starting]**

      此选项允许您在启用活动时不清除日志。

   * **[!UICONTROL SQL table name]**

      通过此参数，可以使包含历史记录数据的默认SQL表过载。

## 输出参数{#output-parameters}

* tableName
* 模式
* recCount

这三个值集标识查询所针对的人口。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通常是nms: **[!UICONTROL recCount]** 收件人)，是表中元素的数量。
