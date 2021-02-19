---
solution: Campaign Classic
product: campaign
title: 并集
description: 进一步了解合并工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---


# 并集{#union}

合并将单个目标中多个入站活动的结果分组。 创建目标时会收到所有结果：因此，必须完成所有先前活动才能执行合并。

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>有关配置和使用合并活动的详细信息，请参阅[组合多个目标(合并)](../../workflow/using/targeting-data.md#combining-several-targets--union-)。

## 合并示例{#union-example}

在以下示例中，已合并两个查询的结果以更新列表。 两个查询目标收件人。 因此，结果基于同一表。

1. 将&#x200B;**[!UICONTROL Union]** -type活动直接插入两个查询之后，并在列表的update-type活动之前，打开它。
1. 您可以输入标签。
1. 选择&#x200B;**[!UICONTROL Keys only]**&#x200B;对帐方法，因为在本例中，由查询生成的人口包含一致的数据。
1. 如果您已为查询添加了其他数据，则可以决定仅保留共享的数据。
1. 如果希望限制最终人口的大小，请选中&#x200B;**[!UICONTROL Limit size of generated population]**&#x200B;框。

   通过输入最大收件人数和选择人口将优先查询来指定此最终数字。

1. 批准合并活动，然后配置列表更新活动(请参阅[列表更新](../../workflow/using/list-update.md))。
1. 启动工作流。将显示结果数，并创建或更新在列表更新活动中定义的列表。 此列表包含一组查询的收件人，如果适用，还包含在上一步中定义的数字。

   ![](assets/union_example.png)

## 输入参数{#input-parameters}

* tableName
* 模式

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数{#output-parameters}

* tableName
* 模式
* recCount

这三个值集标识由合并产生的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通常是nms: **[!UICONTROL recCount]** 收件人)，是表中元素的数量。
