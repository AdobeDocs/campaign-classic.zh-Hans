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

  基于主键数超过30的电子邮件域。 此操作使用&#x200B;**[!UICONTROL Group by + Having]**&#x200B;选项执行。 **[!UICONTROL Group by + Having]**&#x200B;允许您对数据进行分组（“分组依据”），并选择已分组的内容（“具有”）。

要创建此示例，请应用以下步骤：

1. 打开&#x200B;**[!UICONTROL Generic query editor]**&#x200B;并选择收件人表(**nms：recipient**)。

   ![](assets/query_editor_02.png)

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Email domain]**&#x200B;和&#x200B;**[!UICONTROL Primary key]**&#x200B;字段。 对&#x200B;**[!UICONTROL Primary key]**&#x200B;字段运行计数。

   有关主键计数的详细信息，请参阅[此部分](../../platform/using/defining-filter-conditions.md#building-expressions)。

1. 选中&#x200B;**[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;框。

   ![](assets/query_editor_nveau_29.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;窗口中，按降序对电子邮件域进行排序。 为此，请检查&#x200B;**[!UICONTROL Descending sort]**&#x200B;列中的&#x200B;**[!UICONTROL Yes]**。 单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_70.png)

1. 在&#x200B;**[!UICONTROL Data filtering]**&#x200B;中，选择&#x200B;**[!UICONTROL Filtering conditions]**。 转到&#x200B;**[!UICONTROL Target elements]**&#x200B;窗口并单击&#x200B;**[!UICONTROL Next]**。
1. 在&#x200B;**[!UICONTROL Data grouping]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Add]**&#x200B;以选择&#x200B;**[!UICONTROL Email domain]**。

   此数据分组窗口仅在选中&#x200B;**[!UICONTROL Handle groupings (GROUP BY + HAVING]**)框时显示。

   ![](assets/query_editor_blocklist_04.png)

1. 在&#x200B;**[!UICONTROL Grouping condition]**&#x200B;窗口中，指示大于30的主键计数，因为我们希望目标值超过30次的电子邮件域仅作为结果返回。

   勾选&#x200B;**[!UICONTROL Manage groupings (GROUP BY + HAVING)]**&#x200B;框后将显示此窗口：这是筛选分组结果(HAVING)的地方。

   ![](assets/query_editor_blocklist_05.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**：此处不需要格式化。
1. 在数据预览窗口中，单击&#x200B;**[!UICONTROL Launch data preview]**：在此处，将返回三个目标发送次数超过30次的不同电子邮件域。

   ![](assets/query_editor_blocklist_06.png)
