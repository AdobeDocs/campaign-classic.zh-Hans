---
title: 交叉
seo-title: 交叉
description: 交叉
seo-description: null
page-status-flag: never-activated
uuid: a8ff7a66-6c12-4e3c-ad45-d11b34ca64ff
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d0dd9c74-aad5-452e-a11d-c231dacd2aec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 交叉{#intersection}

“交 **叉点**”类型活动从接收目标的交叉点创建目标。

交叉点允许您仅提取所有入站活动结果所通用的人群。 目标创建时会收到所有结果：因此，在执行交叉点之前，必须完成所有先前的活动。 要配置此活动，您需要为其输入标签以及与结果相关的选项。

![](assets/s_user_segmentation_inter.png)

有关配置和使用交叉点活动的详细信息，请参阅提 [取关节数据（交叉点）](../../workflow/using/targeting-data.md#extracting-joint-data--intersection-)。

如果 **[!UICONTROL Generate complement]** 要处理剩余人口，请选中此选项。 补码将包含所有入站活动结果的并除交集。 然后，将向活动添加额外的出站过渡，如下所示：

![](assets/s_user_segmentation_inter_compl.png)

## 交集示例 {#intersection-example}

在以下示例中，交集的目的是计算三个简单查询的通用收件人，以便创建列表。

1. 在三个简单查询后，插入一 **[!UICONTROL Intersection]** 个-type活动。

   在本例中；调查对象分别是男性、住在巴黎的收件人和18至30岁的收件人。

1. 配置交叉点。 为此，请选择协调方 **[!UICONTROL Keys only]** 法，因为查询生成的群体包含一致的数据。
1. 如果您为查询输入了其他数据，则可以通过选中相关框来选择仅保留收件人共享的数据。
1. 如果您希望使用其余数据（关于查询，但不涉及查询的交点），请选中该 **[!UICONTROL Generate complement]** 框。
1. 在交叉结果之后添加列表更新活动。 如果您也希望使用此补充，还可以向补充添加列表更新。
1. 执行工作流。 在此，两个收件人同时应用于所有三个输入的查询。 补码由五个收件人组成，他们只申请三个查询中的一两个。

   交集结果被发送到第一个列表更新。 如果您选择使用补码，它也会发送到第二个列表更新。

   ![](assets/intersection_example.png)

## 输入参数 {#input-parameters}

* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这组三个值标识由交叉点生成的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口(通常 **[!UICONTROL nms:recipient]**)的架构 **[!UICONTROL recCount]** ，是表中的元素数。
