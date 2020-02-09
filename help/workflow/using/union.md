---
title: 合并
seo-title: 合并
description: 合并
seo-description: null
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 合并{#union}

联合会将单个目标中多个入站活动的结果分组。 目标创建时会收到所有结果：因此，工会必须完成所有先前的活动才能执行。

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>有关配置和使用联合活动的详细信息，请参 [阅组合多个目标（联合）](../../workflow/using/targeting-data.md#combining-several-targets--union-)。

## Union示例 {#union-example}

在以下示例中，已组合两个查询的结果以更新列表。 这两个查询以收件人为目标。 因此，结果基于同一表。

1. 在两个查 **[!UICONTROL Union]** 询后直接插入一个-type活动，然后在列表的更新类型活动之前将其打开。
1. 您可以输入标签。
1. 选择协 **[!UICONTROL Keys only]** 调方法，因为在本例中，查询生成的群体包含一致的数据。
1. 如果已为查询添加其他数据，则可以决定仅保留共享的数据。
1. 如果希望限制最终人口的大小，请选中此 **[!UICONTROL Limit size of generated population]** 框。

   通过输入最大收件人数并选择其人口优先的查询，指定此最终编号。

1. 批准联合活动，然后配置列表更新活动(请参 [阅列表更新](../../workflow/using/list-update.md))。
1. 启动工作流。 将显示结果数，并创建或更新在列表更新活动中定义的列表。 此列表包含查询的收件人集，如果适用，还包含在上一步中定义的编号。

   ![](assets/union_example.png)

## 输入参数 {#input-parameters}

* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这组三个值标识了由联合生成的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口（通常nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素数。
