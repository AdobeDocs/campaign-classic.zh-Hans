---
title: 使用分组管理进行查询
description: 了解如何使用分组管理执行查询
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 使用分组管理进行查询 {#querying-using-grouping-management}

在此示例中，我们要运行查询以查找之前发送期间目标超过30次的所有电子邮件域。

* 需要选择哪个表？

   收件人表（nms：收件人）

* 要在输出列中选择的字段？

   电子邮件域和主密钥（含计数）

* 数据分组？

   基于主键数超过30的电子邮件域。 此操作是使用选项执 **[!UICONTROL Group by + Having]** 行的。 **[!UICONTROL Group by + Having]** 允许您将数据分组（“分组依据”），并选择已分组的内容（“有”）。

要创建此示例，请应用以下步骤：

1. 打开收 **[!UICONTROL Generic query editor]** 件人表(**nms:recipient**)。

   ![](assets/query_editor_02.png)

1. 在窗 **[!UICONTROL Data to extract]** 口中，选择和 **[!UICONTROL Email domain]** 字 **[!UICONTROL Primary key]** 段。 运行对字段的 **[!UICONTROL Primary key]** 计数。

   有关主键盘计数的详细信息，请参 [阅此部分](../../platform/using/defining-filter-conditions.md#building-expressions)。

1. 选中 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 框。

   ![](assets/query_editor_nveau_29.png)

1. 在窗口 **[!UICONTROL Sorting]** 中，按降序对电子邮件域进行排序。 要执行此操作，请 **[!UICONTROL Yes]** 在列中选 **[!UICONTROL Descending sort]** 中。 单击 **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. 在中 **[!UICONTROL Data filtering]**，选择 **[!UICONTROL Filtering conditions]**。 转到窗 **[!UICONTROL Target elements]** 口并单击 **[!UICONTROL Next]**。
1. 在窗 **[!UICONTROL Data grouping]** 口中，单击 **[!UICONTROL Email domain]** 以选择 **[!UICONTROL Add]**。

   此数据分组窗口仅在选中( **[!UICONTROL Handle groupings (GROUP BY + HAVING]**)框时显示。

   ![](assets/query_editor_blacklist_04.png)

1. 在窗口 **[!UICONTROL Grouping condition]** 中，指示主键计数大于30，因为我们只希望将目标电子邮件域设置为超过30次以返回结果。

   选中该框时，将 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 显示此窗口：这是过滤分组结果(HAVING)的地方。

   ![](assets/query_editor_blacklist_05.png)

1. 在窗口 **[!UICONTROL Data formatting]** 中，单击 **[!UICONTROL Next]**:此处不需要格式设置。
1. 在数据预览窗口中，单击 **[!UICONTROL Launch data preview]**:此处，将返回三个目标超过30次的不同电子邮件域。

   ![](assets/query_editor_blacklist_06.png)
