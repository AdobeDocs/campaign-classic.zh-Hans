---
solution: Campaign Classic
product: campaign
title: 使用分组管理进行查询
description: 了解如何使用分组管理执行查询
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---


# 使用分组管理进行查询 {#querying-using-grouping-management}

在此示例中，我们要运行一个查询，以在以前的投放中查找目标超过30次的所有电子邮件域。

* 需要选择哪个表？

   收件人表(nms:收件人)

* 要在输出列中选择的字段？

   电子邮件域和主键（含计数）

* 数据分组？

   基于主键数超过30的电子邮件域。 此操作是使用选项执 **[!UICONTROL Group by + Having]** 行的。 **[!UICONTROL Group by + Having]** 允许您对数据进行分组（“分组依据”），并选择已分组的内容（“有”）。

要创建此示例，请应用以下步骤：

1. 打开 **[!UICONTROL Generic query editor]** 收件人表并选&#x200B;**择收件人**。

   ![](assets/query_editor_02.png)

1. 在窗 **[!UICONTROL Data to extract]** 口中，选择 **[!UICONTROL Email domain]** 和字 **[!UICONTROL Primary key]** 段。 运行对字段的 **[!UICONTROL Primary key]** 计数。

   有关主键计数的详细信息，请参 [阅此部分](../../platform/using/defining-filter-conditions.md#building-expressions)。

1. 选中 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 框。

   ![](assets/query_editor_nveau_29.png)

1. 在窗口 **[!UICONTROL Sorting]** 中，按降序对电子邮件域进行排序。 要执行此操作，请 **[!UICONTROL Yes]** 在列中 **[!UICONTROL Descending sort]** 选中。 单击 **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. 在 **[!UICONTROL Data filtering]** 中，选择 **[!UICONTROL Filtering conditions]**。转到窗 **[!UICONTROL Target elements]** 口并单击 **[!UICONTROL Next]**。
1. 在窗 **[!UICONTROL Data grouping]** 口中，单击 **[!UICONTROL Email domain]** 以选择 **[!UICONTROL Add]**。

   此数据分组窗口仅在选中() **[!UICONTROL Handle groupings (GROUP BY + HAVING]**&#x200B;框时显示。

   ![](assets/query_editor_blocklist_04.png)

1. 在窗口 **[!UICONTROL Grouping condition]** 中，指示主密钥计数大于30，因为我们只希望将目标电子邮件域的数目设置为超过30次以返回结果。

   复选框后将显 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 示此窗口：这是筛选分组结果(HAVING)的地方。

   ![](assets/query_editor_blocklist_05.png)

1. 在窗口 **[!UICONTROL Data formatting]** 中，单击 **[!UICONTROL Next]**:此处无需格式设置。
1. 在数据预览窗口中，单击 **[!UICONTROL Launch data preview]**:此处，将返回三个目标超过30次的不同电子邮件域。

   ![](assets/query_editor_blocklist_06.png)
