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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 排除{#exclusion}

排 **除类型**(Exclusion)活动基于从中提取一个或多个其他目标的主目标创建目标。

要配置此活动，请输入其标签并选择主收件人集：主集合中的人口允许您构建结果。 将排除由主集共享的配置文件和至少一个条目活动。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>有关配置和使用排除活动的详细信息，请参 [阅排除人群（排除）](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-)。

如果您 **[!UICONTROL Generate complement]** 希望利用剩余人口，请选中此选项。 补充将包括主要的外来人口减去外来人口。 然后，将向活动添加额外的输出过渡，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除示例 {#exclusion-examples}

以下示例试图编写18至30岁的受助者列表，但不包括巴黎居民。

1. 插入并打开两 **[!UICONTROL Exclusion]** 个查询后的-type活动。 第一个查询以居住在巴黎的收件人为目标。 第二个查询的对象是18至30岁的人。
1. 输入主集。 这里的主集是 **18到30年前的查询** 。 与第二组相关的元素将从最终结果中排除。
1. 如果您 **[!UICONTROL Generate complement]** 希望利用排除后保留的数据，请选中此选项。 在这种情况下，补编由居住在巴黎的18至30岁的受助者组成。
1. 批准排除配置，然后向结果插入更新列表活动。 您还可以在必要时，为补充插入其他列表更新。
1. 执行工作流。 在本例中，结果由18至30岁的受助者组成，但居住在巴黎的受助者被排除在外，并被送至补编。

   ![](assets/exclusion_example.png)

黑名单导入示例使用 **Exclusion**-type活动，该活动可在“读取”列 [表中找到](../../workflow/using/read-list.md)。

## 输入参数 {#input-parameters}

* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这三个值集标识了排除所导致的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口（通常nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素数。

与补码相关联的过渡具有相同的参数。
