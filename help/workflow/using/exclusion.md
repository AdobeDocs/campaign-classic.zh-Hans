---
product: campaign
title: 排除
description: 详细了解排除工作流活动
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 排除{#exclusion}



An **排除项**-type活动基于从中提取一个或多个其他目标的主目标创建目标。

要配置此活动，请输入其标签并选择主收件人集：通过主集中的群体，可构建结果。 将排除由主集和至少一个登入活动共享的用户档案。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>有关配置和使用排除活动的更多信息，请参阅 [排除群体（排除）](targeting-data.md#excluding-a-population--exclusion-).

查看 **[!UICONTROL Generate complement]** 选项。 补数将包含主传入群体减去传出群体。 随后将向该活动添加一个额外的输出过渡，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除示例 {#exclusion-examples}

以下示例试图编列18至30岁之间的接受者名单，但不包括巴黎居民。

1. 插入并打开 **[!UICONTROL Exclusion]** -type活动。 第一个查询针对居住在巴黎的收件人。 第二个查询面向18至30岁的人。
1. 输入主集。 这里的主集是 **18-30岁** 查询。 将从最终结果中排除与第二个集相关的元素。
1. 查看 **[!UICONTROL Generate complement]** 选项。 在这种情况下，补充人数由居住在巴黎的18至30岁的接收人组成。
1. 批准排除配置，然后向结果插入更新列表活动。 如有必要，您还可以向补码插入其他列表更新。
1. 执行工作流。 在此示例中，结果由18至30岁的收件人组成，但居住在巴黎的人被排除并发送到补充项。

   ![](assets/exclusion_example.png)

## 输入参数 {#input-parameters}

* 表名
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识排除项导致的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms：recipient）和 **[!UICONTROL recCount]** 是表中的元素数。

与补充关联的过渡具有相同的参数。
