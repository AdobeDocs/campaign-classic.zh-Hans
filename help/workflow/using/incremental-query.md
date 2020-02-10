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
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 增量查询{#incremental-query}

通过增量查询，您可以基于某个标准定期选择目标，同时排除已针对该标准定位的人员。

已定位的人口按工作流实例和活动存储在内存中，即从同一模板启动的两个工作流不共享同一日志。 另一方面，基于同一工作流实例的同一增量查询的两个任务将使用相同的日志。

查询的定义方式与标准查询的定义方式相同(请参阅 [创建查询](../../workflow/using/query.md#creating-a-query))，但会计划其执行。

>[!CAUTION]
>
>如果增量查询的结果在其其中一个执行期间等于 **0** ，则暂停工作流直到查询的下一个编程执行。 因此，在执行下列操作之前，不会处理增量查询之后的过渡和活动。

操作步骤：

1. 在选项卡 **[!UICONTROL Scheduling & History]** 中，选择相应的 **[!UICONTROL Schedule execution]** 选项。 创建任务后，该任务将保持活动状态，并且只会在计划指定的时间触发以执行查询。 但是，如果禁用此选项，则将立即执行查 **询并一次执行**。
1. Click the **[!UICONTROL Change]** button.

   在窗口 **[!UICONTROL Schedule editing wizard]** 中，您可以配置频率类型、事件循环和事件有效期。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 单击 **[!UICONTROL Finish]** 以保存计划。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. 选项卡的下部 **[!UICONTROL Scheduling & History]** 部分允许您选择历史记录中要考虑的天数。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      已定位的收件人可以从其定位之日起记录最大天数。 如果此值为零，则从日志中清除收件人。

   * **[!UICONTROL Keep history when starting]**

      此选项允许您在启用活动时不清除日志。

   * **[!UICONTROL SQL table name]**

      通过此参数，可以使包含历史记录数据的默认SQL表过载。

## 增量查询的示例：季度列表更新 {#example-of-an-incremental-query--quarterly-list-update}

在以下示例中，增量查询用于自动更新收件人列表。 这些收件人是季节性营销活动的一部分。

由于这些活动是在每个赛季的开始时发起的，以便提供相关的体育活动，因此这些列表会在每个季度进行更新。 但是，此营销活动每9个月只能将此处的收件人定位一次。 这样，您就可以排除接收者的资格频率，并提供多年来不同季节的活动。

![](assets/incremental_query_example.png)

1. 将增量查询以及列表更新活动添加到新工作流中。
1. 根据创 **[!UICONTROL Incremental query]** 建查询中指定的活动 [选项卡配置](../../workflow/using/query.md#creating-a-query)。
1. 选择选 **[!UICONTROL Scheduling & History]** 项卡，然后指定270天的历史记录。 已被定位的收件人在270天或大约9个月内不再被定位。

   然后单击该 **[!UICONTROL Change...]** 按钮。

1. 要确保列表在每个赛季开始之前更新，请选择 **[!UICONTROL Monthly]**。
1. 在下一个屏幕上，选择3月、6月、9月和12月。 选择当月20日，然后选择要启动该工作流的时间。
1. 接下来，为查询选择有效期。 例如，如果希望此活动永久处于活动状态，请选择 **[!UICONTROL Permanent validity]**。

   ![](assets/incremental_query_example_2.png)

1. 批准增量查询后，请配置列表更新活动，如列表更 [新中所述](../../workflow/using/list-update.md)。

因此，该工作流将在每个赛季开始之前自动启动。 该列表将更新为符合条件的新收件人以接收选件。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这三个值集标识查询所定位的人群。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口（通常nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素数。
