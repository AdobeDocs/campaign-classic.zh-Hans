---
product: campaign
title: 增量查询
description: 了解有关增量查询工作流活动的更多信息
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 3%

---

# 增量查询{#incremental-query}



增量查询允许您根据条件定期选择目标，同时排除已为此条件设定了目标的人员。

已定向的群体按工作流实例和活动存储在内存中，即从同一模板启动的两个工作流不共享同一日志。 另一方面，对于同一工作流实例，两个基于同一增量查询的任务将使用同一日志。

查询的定义方式与标准查询的定义方式相同，但会计划其执行。

**相关主题：**

* [用例：使用增量查询每季度更新列表](quarterly-list-update.md)
* [创建查询](query.md#creating-a-query)

>[!CAUTION]
>
>如果增量查询的结果在其中一个执行期间等于&#x200B;**0**，则工作流将暂停，直到查询下一次程序化执行。 因此，在后续执行之前，不会处理增量查询之后的过渡和活动。

操作步骤：

1. 在&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;选项卡中选择&#x200B;**[!UICONTROL Schedule execution]**&#x200B;选项。 创建任务后，该任务将保持活动状态，并且仅在计划指定的执行查询的时间触发。 但是，如果该选项被禁用，则查询将立即执行&#x200B;**并且一次执行**。
1. 单击 **[!UICONTROL Change]** 按钮。

   在&#x200B;**[!UICONTROL Schedule editing assistant]**&#x200B;窗口中，可以配置频率类型、事件重复周期和事件有效期。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;保存计划。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. **[!UICONTROL Scheduling & History]**&#x200B;选项卡的下部允许您选择要在历史记录中考虑的天数。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

     对于已定向的收件人，可以记录其从被定向之日起的最大天数。 如果此值为零，则不会从日志中清除收件人。

   * **[!UICONTROL Keep history when starting]**

     启用活动后，使用此选项不会清除日志。

   * **[!UICONTROL SQL table name]**

     此参数允许您重载包含历史记录数据的默认SQL表。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识查询所定向的群体。 **[!UICONTROL tableName]**&#x200B;是记录目标标识符的表的名称，**[!UICONTROL schema]**&#x200B;是群体的架构（通常为nms：recipient），**[!UICONTROL recCount]**&#x200B;是表中的元素数。
