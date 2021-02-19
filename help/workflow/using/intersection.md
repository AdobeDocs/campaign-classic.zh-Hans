---
solution: Campaign Classic
product: campaign
title: 交集
description: 交集
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---


# 交集{#intersection}

**交叉**&#x200B;类型活动从所接收目标的交集创建目标。

交集允许您仅提取所有入站活动结果共有的人口。 创建目标时会收到所有结果：因此，在执行交叉点之前，必须完成所有先前活动。 要配置此活动，您需要为其输入标签以及有关结果的选项。

![](assets/s_user_segmentation_inter.png)

有关配置和使用交集活动的详细信息，请参阅[提取联合数据(交叉)](../../workflow/using/targeting-data.md#extracting-joint-data--intersection-)。

如果要处理剩余人口，请选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。 补码将包含所有入站活动的结果的合并，但不包括交集。 随后将向该活动添加额外的出站过渡，如下所示：

![](assets/s_user_segmentation_inter_compl.png)

## 交叉示例{#intersection-example}

在下面的示例中，交集的目的是计算三个简单查询的共同收件人，以创建列表。

1. 在三个简单查询后，插入一个&#x200B;**[!UICONTROL Intersection]** -type活动。

   在本例中；查询人分别是目标男子、住在巴黎的收件人和18岁至30岁的收件人。

1. 配置交叉点。 为此，请选择&#x200B;**[!UICONTROL Keys only]**&#x200B;协调方法，因为查询生成的种群包含一致的数据。
1. 如果您为查询输入了其他数据，则可以通过选中相关框来选择仅保留由收件人共享的数据。
1. 如果要使用其余数据(涉及查询，但不涉及其交集)，请选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;框。
1. 在交集结果之后添加列表更新活动。 如果您也希望使用此补充，还可以向补充添加列表更新。
1. 执行工作流。 此处，两个收件人同时应用于所有三个输入查询。 补编由五个收件人组成，只适用于三个查询中的一个或两个。

   交集结果将发送到第一个列表更新。 如果您选择使用补充，则还会将其发送到第二个列表更新。

   ![](assets/intersection_example.png)

## 输入参数{#input-parameters}

* tableName
* 模式

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数{#output-parameters}

* tableName
* 模式
* recCount

这三个值集标识由交集产生的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通 **[!UICONTROL nms:recipient]**&#x200B;常) **[!UICONTROL recCount]** ，是表中元素的数量。
