---
product: campaign
title: 并集
description: 进一步了解Union工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# 并集{#union}

![](../../assets/common.svg)

并集会将单个目标中多个集客活动的结果分组。 将创建目标，并收到所有结果：因此，必须完成之前的所有活动才能执行并集。

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>有关配置和使用并集活动的更多信息，请参阅 [合并多个目标（合并）](targeting-data.md#combining-several-targets--union-).

## 并集示例 {#union-example}

在以下示例中，为了更新列表，已合并了两个查询的结果。 这两个查询针对的是收件人。 因此，结果基于同一表。

1. 插入 **[!UICONTROL Union]** -type活动在两个查询之后，在列表的update-type活动之前，然后将其打开。
1. 您可以输入标签。
1. 选择 **[!UICONTROL Keys only]** 协调方法，因为在本例中，由查询产生的群体包含一致的数据。
1. 如果您为查询添加了其他数据，则可以决定仅保留共享的数据。
1. 如果要限制最终群体的大小，请检查 **[!UICONTROL Limit size of generated population]** 框中。

   通过输入最大收件人数并选择群体优先的查询来指定此最终数字。

1. 批准并集活动，然后配置列表更新活动(请参阅 [列表更新](list-update.md))。
1. 启动工作流. 将显示结果数，并创建或更新列表更新活动中定义的列表。 此列表包含两个查询的收件人集，或（如果适用）上一步中定义的编号。

   ![](assets/union_example.png)

## 输入参数 {#input-parameters}

* tableName
* 模式

每个集客事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这组三个值用于标识由并集生成的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体模式（通常为nms:recipient）和 **[!UICONTROL recCount]** 是表中的元素数。
