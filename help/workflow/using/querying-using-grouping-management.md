---
product: campaign
title: 使用分组管理进行查询
description: 了解如何使用分组管理执行查询
feature: Query Editor
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# 使用分组管理进行查询 {#querying-using-grouping-management}

![](../../assets/common.svg)

在本例中，我们要运行查询以查找在先前投放期间定向超过30次的所有电子邮件域。

* 需要选择哪个表？

   收件人表(nms:recipient)

* 要在输出列中选择的字段？

   电子邮件域和主键（包含计数）

* 数据分组？

   基于主键数超过30的电子邮件域。 此操作通过 **[!UICONTROL Group by + Having]** 选项。 **[!UICONTROL Group by + Having]** 允许您对数据（“分组依据”）进行分组，并选择分组的内容（“有”）。

要创建此示例，请应用以下步骤：

1. 打开 **[!UICONTROL Generic query editor]** 并选择收件人表(**nms:recipient**)。

   ![](assets/query_editor_02.png)

1. 在 **[!UICONTROL Data to extract]** 窗口，选择 **[!UICONTROL Email domain]** 和 **[!UICONTROL Primary key]** 字段。 运行计数 **[!UICONTROL Primary key]** 字段。

   有关主键计数的更多信息，请参阅 [此部分](../../platform/using/defining-filter-conditions.md#building-expressions).

1. 检查 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 框中。

   ![](assets/query_editor_nveau_29.png)

1. 在 **[!UICONTROL Sorting]** 窗口中，按降序对电子邮件域进行排序。 要执行此操作，请检查 **[!UICONTROL Yes]** 在 **[!UICONTROL Descending sort]** 列。 单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_70.png)

1. 在 **[!UICONTROL Data filtering]** 中，选择 **[!UICONTROL Filtering conditions]**。转到 **[!UICONTROL Target elements]** 窗口，单击 **[!UICONTROL Next]**.
1. 在 **[!UICONTROL Data grouping]** 窗口，选择 **[!UICONTROL Email domain]** 单击 **[!UICONTROL Add]**.

   此数据分组窗口仅在 **[!UICONTROL Handle groupings (GROUP BY + HAVING]**&#x200B;复选框。

   ![](assets/query_editor_blocklist_04.png)

1. 在 **[!UICONTROL Grouping condition]** 窗口，指示主键计数大于30，因为我们只希望返回超过30次的电子邮件域作为结果。

   当 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 复选框：这是过滤分组结果(HAVING)的位置。

   ![](assets/query_editor_blocklist_05.png)

1. 在 **[!UICONTROL Data formatting]** 窗口，单击 **[!UICONTROL Next]**:此处不需要格式设置。
1. 在数据预览窗口中，单击 **[!UICONTROL Launch data preview]**:在此，将返回三个定位超过30次的不同电子邮件域。

   ![](assets/query_editor_blocklist_06.png)
