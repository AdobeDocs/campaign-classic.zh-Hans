---
product: campaign
title: 交集
description: 交集
feature: Workflows, Targeting Activity
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 12%

---

# 交集{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="交集活动"
>abstract="交集类型活动从收到的目标的交集创建目标。交集允许您仅提取所有入站活动结果共有的群体。"
>additional-url="https://video.tv.adobe.com/v/329373" text="观看演示视频"




An **交叉**-type活动根据接收目标的交集创建目标。

利用交集，可仅提取所有集客活动结果共有的群体。 创建目标时收到所有结果：因此，必须先完成所有先前的活动，然后才能执行交集。 要配置此活动，需要输入其标签以及有关结果的选项。

![](assets/s_user_segmentation_inter.png)

有关配置和使用交叉点活动的更多信息，请参阅 [提取连接数据（交集）](targeting-data.md#extracting-joint-data--intersection-).

查看 **[!UICONTROL Generate complement]** 选项。 补充将包含所有集客活动减去交集的结果的并集。然后，将向活动添加其他叫客过渡，如下所示：

![](assets/s_user_segmentation_inter_compl.png)

## 交集示例 {#intersection-example}

在以下示例中，交集的目的是计算三个简单查询共有的收件人以创建列表。

1. 在三个简单查询之后，插入 **[!UICONTROL Intersection]** -type活动。

   在本例中，查询分别针对男性、居住在巴黎的收件人以及18至30岁的收件人。

1. 配置交集。 要执行此操作，请选择 **[!UICONTROL Keys only]** 协调方法，因为由查询生成的群体包含一致的数据。
1. 如果您已输入查询的其他数据，则可以通过选中相关框来选择仅保留由收件人共享的数据。
1. 如果您希望使用其余数据（与查询相关，但不与它们的交集相关），请检查 **[!UICONTROL Generate complement]** 盒子。
1. 在交叉点结果后添加列表更新活动。 如果您也希望使用此项，您还可以将列表更新添加到补充中。
1. 执行工作流。 在此，两个收件人同时应用于所有三个输入的查询。 补码由五个收件人组成，他们只应用于三个查询中的一个或两个。

   交集结果将发送到第一个列表更新。 如果您已选择使用补充，它也会发送给第二次列表更新。

   ![](assets/intersection_example.png)

## 输入参数 {#input-parameters}

* 表名
* 架构

每个入站事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识从交叉点生成的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人群的架构(通常 **[!UICONTROL nms:recipient]**)和 **[!UICONTROL recCount]** 是表中的元素数。
