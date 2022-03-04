---
product: campaign
title: 排除
description: 进一步了解排除工作流活动
feature: Workflows, Targeting Activity
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 排除{#exclusion}

![](../../assets/common.svg)

安 **排除**-type活动会根据从中提取一个或多个其他目标的主目标创建目标。

要配置此活动，请输入其标签并选择主收件人集：利用主集中的群体，可构建结果。 将排除由主集和至少一个登入活动共享的用户档案。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>有关配置和使用排除活动的更多信息，请参阅 [排除群体（排除）](targeting-data.md#excluding-a-population--exclusion-).

检查 **[!UICONTROL Generate complement]** 选项。 补码将包含主传入群体减去传出群体。 随后，将向活动添加额外的输出过渡，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除示例 {#exclusion-examples}

以下示例试图汇编一份18至30岁的收件人名单，但不包括巴黎居民。

1. 插入并打开 **[!UICONTROL Exclusion]** -type活动。 第一个查询针对的是居住在巴黎的收件人。 第二个查询针对的是18至30岁的人。
1. 输入主集。 在此，主集是 **18岁–30岁** 查询。 与第二组相关的元素将从最终结果中排除。
1. 检查 **[!UICONTROL Generate complement]** 选项。 在这种情况下，补编由居住在巴黎的18至30岁的收件人组成。
1. 批准排除配置，然后为结果插入更新列表活动。 您还可以在必要时，为补码插入额外的列表更新。
1. 执行工作流。 在此示例中，结果由18至30岁的收件人组成，但居住在巴黎的收件人将被排除并发送到补码中。

   ![](assets/exclusion_example.png)

## 输入参数 {#input-parameters}

* tableName
* 模式

每个集客事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这组值由三个值组成，用于标识由排除项生成的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体模式（通常为nms:recipient）和 **[!UICONTROL recCount]** 是表中的元素数。

与补码关联的过渡具有相同的参数。
