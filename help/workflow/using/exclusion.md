---
product: campaign
title: 差集
description: 了解有关排除工作流活动的更多信息
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 1%

---

# 差集{#exclusion}



**排除项**&#x200B;类型活动基于从中提取一个或多个其他目标的主目标创建目标。

要配置此活动，请输入其标签并选择主收件人集：通过主集中的群体，可构建结果。 将排除由主集和至少一个进入活动共享的用户档案。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>有关配置和使用排除活动的详细信息，请参阅[排除群体（排除项）](targeting-data.md#excluding-a-population--exclusion-)。

如果要利用剩余群体，请选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。 补数将包含主传入群体减去传出群体。 然后，将向该活动添加一个额外的输出转换，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除项示例 {#exclusion-examples}

以下示例试图编制18至30岁之间的收件者名单，但不包括巴黎居民。

1. 在两次查询后插入并打开&#x200B;**[!UICONTROL Exclusion]** -type活动。 第一个查询针对居住在巴黎的收件人。 第二个查询面向18至30岁的人。
1. 输入主集。 此处主集是&#x200B;**18-30年前的**&#x200B;查询。 将从最终结果中排除与第二个集合相关的元素。
1. 如果要利用排除后保留的数据，请选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。 在本例中，补充人口为18至30岁的巴黎居民。
1. 批准排除配置，然后为结果插入更新列表活动。 如有必要，您还可以向补码插入其他列表更新。
1. 执行工作流。 在本例中，结果由18到30岁的收件人组成，但居住在巴黎的人被排除在外，并被发送至补充数据。

   ![](assets/exclusion_example.png)

## 输入参数 {#input-parameters}

* 表名
* 架构

每个入站事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值可标识排除项导致的目标。 **[!UICONTROL tableName]**&#x200B;是记录目标标识符的表的名称，**[!UICONTROL schema]**&#x200B;是群体的架构（通常为nms：recipient），**[!UICONTROL recCount]**&#x200B;是表中的元素数。

与补充关联的转换具有相同的参数。
