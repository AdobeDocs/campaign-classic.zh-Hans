---
solution: Campaign Classic
product: campaign
title: 排除
description: 进一步了解排除工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# 排除{#exclusion}

**排除**&#x200B;类型活动基于主目标创建目标，从中提取一个或多个其他目标。

要配置此活动，请输入其标签并选择主收件人集：主集中的人口允许您构建结果。 将排除由主集共享的用户档案和至少一个条目活动。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>有关配置和使用排除活动的详细信息，请参阅[排除人口（排除）](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-)。

如果希望利用剩余人口，请选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。 补编将包括主要入境人口减去出境人口。 随后将向该活动添加一个额外的输出过渡，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除示例{#exclusion-examples}

下例试图汇编一份18至30岁收件人列表，但不包括巴黎居民。

1. 插入并打开一个&#x200B;**[!UICONTROL Exclusion]** -type活动，它遵循两个查询。 第一位住在巴黎的查询目标收件人。 第二个查询目标18到30岁的人。
1. 输入主集。 主集为&#x200B;**18-30岁**&#x200B;查询。 与第二组相关的元素将从最终结果中排除。
1. 如果要利用排除后保留的数据，请选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。 在这种情况下，补编由居住在巴黎的18至30岁收件人组成。
1. 批准排除配置，然后为结果插入更新列表活动。 如有必要，您还可以在补码中插入额外的列表更新。
1. 执行工作流。 在本例中，结果由18至30岁的收件人组成，但居住在巴黎的人被排除在外，并送到补编。

   ![](assets/exclusion_example.png)

## 输入参数{#input-parameters}

* tableName
* 模式

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数{#output-parameters}

* tableName
* 模式
* recCount

这三组值标识排除所产生的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通常是nms: **[!UICONTROL recCount]** 收件人)，是表中元素的数量。

与补码相关的过渡具有相同的参数。
