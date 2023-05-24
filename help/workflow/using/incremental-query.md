---
product: campaign
title: 增量查询
description: 了解有关增量查询工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# 增量查询{#incremental-query}



增量查询允许您定期根据条件选择目标，同时排除已针对此条件定向的人员。

已定向的群体按工作流实例和活动存储在内存中，即从同一模板启动的两个工作流不共享同一日志。 另一方面，两个基于同一增量查询的任务将使用同一日志。

查询的定义方式与标准查询的定义方式相同，但会计划其执行。

**相关主题：**

* [用例：使用增量查询每季度更新列表](quarterly-list-update.md)
* [创建查询](query.md#creating-a-query)

>[!CAUTION]
>
>如果增量查询的结果等于 **0** 在其执行之一期间，工作流将暂停，直到查询下一次计划执行。 因此，在后续执行之前，不会处理增量查询之后的过渡和活动。

操作步骤：

1. 在 **[!UICONTROL Scheduling & History]** 选项卡，选择 **[!UICONTROL Schedule execution]** 选项。 创建任务后，该任务将保持活动状态，并且仅在计划执行查询时指定的时间触发。 但是，如果该选项被禁用，则会立即执行查询 **一举一动**.
1. 单击 **[!UICONTROL Change]** 按钮。

   在 **[!UICONTROL Schedule editing wizard]** 窗口中，可以配置频率类型、事件重复周期和事件有效期。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 单击 **[!UICONTROL Finish]** 以保存计划。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. 的下部 **[!UICONTROL Scheduling & History]** 选项卡允许您选择要在历史记录中考虑的天数。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      已定向的收件人可以记录自其被定向之日起的最大天数。 如果此值为零，则不会从日志中清除收件人。

   * **[!UICONTROL Keep history when starting]**

      此选项允许您在启用活动时不清除日志。

   * **[!UICONTROL SQL table name]**

      此参数允许您重载包含历史记录数据的默认SQL表。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识查询所针对的群体。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms：recipient）和 **[!UICONTROL recCount]** 是表中的元素数。
