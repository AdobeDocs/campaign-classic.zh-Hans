---
title: 并集
description: 进一步了解合并工作流活动
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---


# 并集{#union}

合并将单个目标中多个入站活动的结果分组。 创建目标时会收到所有结果：因此，必须完成所有以前的活动才能执行合并。

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>有关配置和使用合并活动的详细信息，请参 [阅组合多个目标(合并)](../../workflow/using/targeting-data.md#combining-several-targets--union-)。

## 合并示例 {#union-example}

在以下示例中，已合并两个查询的结果以更新列表。 两个查询目标收件人。 因此，结果基于同一表。

1. 在两个 **[!UICONTROL Union]** 活动后面直接插入一个-type查询，然后在列表的更新类型活动前打开它。
1. 您可以输入标签。
1. 选择对 **[!UICONTROL Keys only]** 帐方法，因为在本例中，由查询产生的人口包含一致的数据。
1. 如果已为查询添加其他数据，则可以决定仅保留共享的数据。
1. If you wish to limit the size of the final population, check the **[!UICONTROL Limit size of generated population]** box.

   通过输入最大收件人数和选择人口优先的查询，指定此最终数。

1. 批准合并活动，然后配置列表更新活动(请参 [阅列表更](../../workflow/using/list-update.md)新)。
1. 启动工作流。将显示结果数，并创建或更新在列表更新活动中定义的列表。 此列表包含两个收件人的查询集，或者（如果适用）上一步中定义的数字。

   ![](assets/union_example.png)

## 输入参数 {#input-parameters}

* tableName
* 模式

每个入站事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这三个值集标识由目标产生的合并。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通常是nms:收件人 **[!UICONTROL recCount]** )，是表中元素的数量。
