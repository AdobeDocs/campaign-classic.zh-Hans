---
title: 排除
seo-title: 排除
description: 排除
seo-description: null
page-status-flag: never-activated
uuid: e4f54a0b-2fec-4415-986b-83c8928ed174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: acab51f3-686b-4d2b-bb02-8fbfae36b1ba
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 1%

---


# 排除{#exclusion}

排 **除类**&#x200B;型活动基于主目标创建目标，从中提取一个或多个其他目标。

要配置此活动，请输入其标签并选择主收件人集：主集合中的人口允许您构建结果。 将排除由主集共享的用户档案和至少一个条目活动。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>有关配置和使用排除活动的详细信息，请 [参阅排除人口（排除）](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-)。

Check the **[!UICONTROL Generate complement]** option if you wish to exploit the remaining population. 补充将包括主要的外来人口减去即将流出的人口。 随后将向该过渡添加一个附加输出活动，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除示例 {#exclusion-examples}

以下示例旨在汇编一份列表，其中包括18至30岁的收件人，但不包括巴黎居民。

1. 插入并打开 **[!UICONTROL Exclusion]** 两个活动后的-type查询。 第一批查询目标收件人住在巴黎。 第二个查询目标18到30岁的人。
1. 输入主集。 主集是十八到 **三十岁的查询** . 属于第二组的元素将从最终结果中排除。
1. 如果希 **[!UICONTROL Generate complement]** 望利用排除后保留的数据，请选中此选项。 在这种情况下，补码由生活在巴黎的18至30岁收件人组成。
1. 批准排除配置，然后为结果插入更新列表活动。 如有必要，还可以向补充插入额外的列表更新。
1. 执行工作流。 在本例中，结果由18至30岁的收件人组成，但居住在巴黎的人被排除，并被送至补充。

   ![](assets/exclusion_example.png)

## 输入参数 {#input-parameters}

* tableName
* 模式

每个入站事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这三个值集标识排除所产生的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通常是nms:收件人 **[!UICONTROL recCount]** )，是表中元素的数量。

与补码关联的过渡具有相同的参数。
