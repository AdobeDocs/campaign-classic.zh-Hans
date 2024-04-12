---
product: campaign
title: 执行聚合计算
description: 了解如何在查询中执行聚合计算
feature: Workflows
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# 执行聚合计算 {#performing-aggregate-computing}



在本例中，我们要根据性别统计居住在伦敦的接收人数。

* 需要选择哪个表？

  收件人表(**nms：recipient**)

* 应在输出列中选择哪些字段？

  主键（计数）和性别

* 信息过滤基于什么条件？

  基于居住在伦敦的收件人

要创建此示例，请应用以下步骤：

1. 在 **[!UICONTROL Data to extract]**，定义主键的计数（如上一个示例中所示）。 添加 **[!UICONTROL Gender]** 字段输入。 查看 **[!UICONTROL Group]** 中的选项 **[!UICONTROL Gender]** 列。 这样，收件人将按性别分组。

   ![](assets/query_editor_nveau_27.png)

1. 在 **[!UICONTROL Sorting]** 窗口，单击 **[!UICONTROL Next]**：此处无需排序。
1. 配置数据筛选。 在此，您希望将选择限制为居住在伦敦的联系人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值区分大小写。 如果在条件中输入“London”值时没有使用大写字母，并且收件人列表包含带大写字母的“London”一词，则查询将失败。

1. 在 **[!UICONTROL Data formatting]** 窗口，单击 **[!UICONTROL Next]**：此示例无需任何格式。
1. 在预览窗口中，单击 **[!UICONTROL Launch data preview]**.

   按性别划分的每种排序有三个不同的值： **2** 对于女性， **1** 为男性和 **0** 当性别不明时。 在本例中，名单上有10名妇女、16名男子和2名性别不明的妇女。

   ![](assets/query_editor_agregat_04.png)
