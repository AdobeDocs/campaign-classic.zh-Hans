---
product: campaign
title: 查询收件人表
description: 了解如何查询收件人表
feature: Query Editor, Workflows
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# 查询收件人表 {#querying-recipient-table}



在本例中，我们要恢复其电子邮件域为“orange.co.uk”且不在伦敦居住的收件人的姓名和电子邮件。

* 我们应该选择哪个表？

  收件人表(nms：recipient)

* 要选为输出列的字段

  电子邮件、姓名、城市和帐号

* 收件人的过滤条件是什么？

  城市和电子邮件域

* 是否已配置排序？

  是，基于&#x200B;**[!UICONTROL Account number]**&#x200B;和&#x200B;**[!UICONTROL Last name]**

要创建此示例，请应用以下步骤：

1. 单击&#x200B;**[!UICONTROL Tools > Generic query editor...]**&#x200B;并选择&#x200B;**收件人** (**nms：recipient**)表。 然后单击 **[!UICONTROL Next]**。
1. 选择： **[!UICONTROL Last name]**、**[!UICONTROL First name]**、**[!UICONTROL Email]**、**[!UICONTROL City]**&#x200B;和&#x200B;**[!UICONTROL Account number]**。 这些字段已添加到&#x200B;**[!UICONTROL Output columns]**。 然后单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_03.png)

1. 对列进行排序，以按正确的顺序显示它们。 在这里，我们要按降序对帐号进行排序，并按字母顺序对名称进行排序。 然后单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_04.png)

1. 在&#x200B;**[!UICONTROL Data filtering]**&#x200B;窗口中，优化您的搜索：选择&#x200B;**[!UICONTROL Filtering conditions]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**。
1. **[!UICONTROL Target element]**&#x200B;窗口允许您输入筛选器设置。

   定义以下筛选条件：电子邮件域等于“orange.co.uk”的收件人。 为此，请在&#x200B;**[!UICONTROL Expression]**&#x200B;列中选择&#x200B;**电子邮件域(@email)**，在&#x200B;**[!UICONTROL Operator]**&#x200B;列中选择&#x200B;**等于**，并在&#x200B;**[!UICONTROL Value]**&#x200B;列中输入“orange.co.uk”。

   ![](assets/query_editor_05.png)

1. 如果需要，请单击&#x200B;**[!UICONTROL Distribution of values]**&#x200B;按钮以查看基于潜在客户电子邮件域的分发。 对于数据库中的每个电子邮件域，都有一个百分比可用。 在应用过滤器之前，将显示“orange.co.uk”以外的域。

   查询的摘要显示在窗口底部： **电子邮件域等于“orange.co.uk”**。

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;了解查询结果：只显示“orange.co.uk”电子邮件域。

   ![](assets/query_editor_nveau_17.png)

1. 现在，我们将更改查询以查找不住在伦敦的联系人。

   选择&#x200B;**[!UICONTROL Expression]**&#x200B;列中的&#x200B;**[!UICONTROL City (location/@city)]**，选择&#x200B;**[!UICONTROL different from]**&#x200B;作为运算符，并在&#x200B;**[!UICONTROL Value]**&#x200B;列中输入&#x200B;**[!UICONTROL London]**。

   ![](assets/query_editor_08.png)

1. 这会将您转到&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口。 检查列顺序。 将“City”列向上移动到“Account number”列下。

   取消选中“名字”列以将其从列表中删除。

   ![](assets/query_editor_nveau_15.png)

1. 在&#x200B;**[!UICONTROL Data preview]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Start the preview of the data]**。 此函数计算查询的结果。

   **[!UICONTROL Column results]**&#x200B;选项卡以列显示查询结果。

   结果会显示所有具有“orange.co.uk”电子邮件域的收件人，这些收件人不在伦敦居住。 “名字”列未显示，因为它在上一阶段中未被选中。 帐号按降序排序。

   ![](assets/query_editor_nveau_12.png)

   **[!UICONTROL XML result]**&#x200B;选项卡以XML格式显示结果。

   ![](assets/query_editor_nveau_13.png)

   **[!UICONTROL Generated QSL queries]**&#x200B;选项卡以SQL格式显示查询结果。

   ![](assets/query_editor_nveau_14.png)
