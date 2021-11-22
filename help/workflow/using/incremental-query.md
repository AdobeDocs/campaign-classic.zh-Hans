---
product: campaign
title: 增量查询
description: 了解有关增量查询工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# 增量查询{#incremental-query}

![](../../assets/common.svg)

通过增量查询，您可以根据条件定期选择目标，同时排除已针对此条件定向的人员。

已定向的群体按工作流实例和活动存储在内存中，即从同一模板启动的两个工作流不共享同一日志。 另一方面，基于同一工作流实例的相同增量查询的两个任务将使用相同的日志。

查询的定义方式与标准查询的定义方式相同，但其执行是计划的。

**相关主题：**

* [用例：使用增量查询每季度更新列表](quarterly-list-update.md)
* [创建查询](query.md#creating-a-query)

>[!CAUTION]
>
>如果增量查询的结果等于 **0** 在其中一次执行期间，工作流会暂停，直到查询的下次编程执行为止。 因此，在执行后续操作之前，不会处理增量查询后的过渡和活动。

操作步骤：

1. 在 **[!UICONTROL Scheduling & History]** 选项卡，选择 **[!UICONTROL Schedule execution]** 选项。 创建任务后，该任务将保持活动状态，并且只会在计划指定的时间执行查询时触发。 但是，如果禁用了选项，则会立即执行查询 **一下子**.
1. 单击 **[!UICONTROL Change]** 按钮。

   在 **[!UICONTROL Schedule editing wizard]** 窗口中，您可以配置频度类型、事件重复和事件有效期。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 单击 **[!UICONTROL Finish]** 以保存计划。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. 的下部 **[!UICONTROL Scheduling & History]** 选项卡，以选择历史记录中需要考虑的天数。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      已定向的收件人可在自定向之日起的最大天数内被记录。 如果此值为零，则从不会从日志中清除收件人。

   * **[!UICONTROL Keep history when starting]**

      此选项允许您在启用活动时不清除日志。

   * **[!UICONTROL SQL table name]**

      此参数允许您使包含历史数据的默认SQL表过载。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这组值由三个值组成，用于标识查询所定向的群体。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体模式（通常为nms:recipient）和 **[!UICONTROL recCount]** 是表中的元素数。
