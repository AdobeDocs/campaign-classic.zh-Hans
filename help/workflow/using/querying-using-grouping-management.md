---
product: campaign
title: 使用分组管理进行查询
description: 了解如何使用分组管理执行查询
feature: Query Editor, Workflows
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 3%

---

# 使用分组管理进行查询 {#querying-using-grouping-management}



在本例中，我们希望运行查询以查找在以前的投放期间定向超过30次的所有电子邮件域。

* 需要选择哪个表？

  收件人表(nms：recipient)

* 要在输出列中选择的字段？

  电子邮件域和主键（计数）

* 数据分组？

  基于主键数超过30的电子邮件域。 此操作是通过 **[!UICONTROL Group by + Having]** 选项。 **[!UICONTROL Group by + Having]** 允许您分组数据（“分组依据”），并选择已分组的内容（“具有”）。

要创建此示例，请应用以下步骤：

1. 打开 **[!UICONTROL Generic query editor]** 并选择收件人表(**nms：recipient**)。

   ![](assets/query_editor_02.png)

1. 在 **[!UICONTROL Data to extract]** 窗口中，选择 **[!UICONTROL Email domain]** 和 **[!UICONTROL Primary key]** 字段。 对运行计数 **[!UICONTROL Primary key]** 字段。

   有关主键计数的详细信息，请参阅 [本节](../../platform/using/defining-filter-conditions.md#building-expressions).

1. 查看 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 盒子。

   ![](assets/query_editor_nveau_29.png)

1. 在 **[!UICONTROL Sorting]** 窗口，按降序对电子邮件域进行排序。 为此，请选中 **[!UICONTROL Yes]** 在 **[!UICONTROL Descending sort]** 列。 单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_70.png)

1. 在 **[!UICONTROL Data filtering]**，选择 **[!UICONTROL Filtering conditions]**. 转到 **[!UICONTROL Target elements]** 窗口，然后单击 **[!UICONTROL Next]**.
1. 在 **[!UICONTROL Data grouping]** 窗口中，选择 **[!UICONTROL Email domain]** 通过单击 **[!UICONTROL Add]**.

   此数据分组窗口仅在 **[!UICONTROL Handle groupings (GROUP BY + HAVING]**)框已被选中。

   ![](assets/query_editor_blocklist_04.png)

1. 在 **[!UICONTROL Grouping condition]** 窗口，指示大于30的主键计数，因为我们希望目标电子邮件域作为结果返回超过30次。

   此窗口出现于 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 复选框：这是过滤(HAVING)分组结果的地方。

   ![](assets/query_editor_blocklist_05.png)

1. 在 **[!UICONTROL Data formatting]** 窗口，单击 **[!UICONTROL Next]**：此处无需设置格式。
1. 在数据预览窗口中，单击 **[!UICONTROL Launch data preview]**：在本例中，将返回三个定位时间超过30次的不同电子邮件域。

   ![](assets/query_editor_blocklist_06.png)
