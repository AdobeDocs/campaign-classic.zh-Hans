---
solution: Campaign Classic
product: campaign
title: 查询收件人表
description: 了解如何查询收件人表
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---


# 查询收件人表 {#querying-recipient-table}

在此示例中，我们要恢复电子邮件域为“orange.co.uk”且不住在伦敦的收件人的姓名和电子邮件。

* 我们应选择哪个表？

   收件人表(nms:收件人)

* 要选作输出列的字段

   电子邮件、姓名、城市和帐号

* 收件人的过滤条件是什么？

   城市和电子邮件域

* 是否配置了类型？

   是，基于&#x200B;**[!UICONTROL Account number]**&#x200B;和&#x200B;**[!UICONTROL Last name]**

要创建此示例，请应用以下步骤：

1. 单击&#x200B;**[!UICONTROL Tools > Generic query editor...]**&#x200B;并选择&#x200B;**收件人**(**nms:收件人**)表。 然后单击 **[!UICONTROL Next]**。
1. 选择：**[!UICONTROL Last name]**、**[!UICONTROL First name]**、**[!UICONTROL Email]**、**[!UICONTROL City]**&#x200B;和&#x200B;**[!UICONTROL Account number]**。 这些字段将添加到&#x200B;**[!UICONTROL Output columns]**。 然后单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_03.png)

1. 对列进行排序以按正确的顺序显示它们。 在此，我们希望按降序对帐户编号排序，按字母顺序对名称排序。 然后单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_04.png)

1. 在&#x200B;**[!UICONTROL Data filtering]**&#x200B;窗口中，细化搜索：选择&#x200B;**[!UICONTROL Filtering conditions]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**。
1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;窗口中可以输入过滤器设置。

   定义以下筛选条件：电子邮件域等于“orange.co.uk”的收件人。 为此，请在&#x200B;**[!UICONTROL Expression]**&#x200B;列中选择&#x200B;**电子邮件域(@email)**，在&#x200B;**[!UICONTROL Operator]**&#x200B;列中选择&#x200B;**等于**，并在&#x200B;**[!UICONTROL Value]**&#x200B;列中输入“orange.co.uk”。

   ![](assets/query_editor_05.png)

1. 如果需要，单击&#x200B;**[!UICONTROL Distribution of values]**&#x200B;按钮以视图基于潜在客户电子邮件域的分发。 数据库中每个电子邮件域都有一个百分比。 应用过滤器之前，将显示“orange.co.uk”以外的域。

   查询的摘要显示在窗口底部：**电子邮件域等于“orange.co.uk”**。

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;可了解查询结果：只显示“orange.co.uk”电子邮件域。

   ![](assets/query_editor_nveau_17.png)

1. 我们现在将改变查询，寻找不住在伦敦的人。

   在&#x200B;**[!UICONTROL Expression]**&#x200B;列中选择&#x200B;**[!UICONTROL City (location/@city)]**&#x200B;作为运算符，在&#x200B;**[!UICONTROL Value]**&#x200B;列中输入&#x200B;**[!UICONTROL London]**。**[!UICONTROL different from]**

   ![](assets/query_editor_08.png)

1. 这将带您进入&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口。 检查列顺序。 将“Account number”列下的“City”列向上移动。

   取消选中“名”列，将其从列表中删除。

   ![](assets/query_editor_nveau_15.png)

1. 在&#x200B;**[!UICONTROL Data preview]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Start the preview of the data]**。 此函数计算查询的结果。

   **[!UICONTROL Column results]**&#x200B;选项卡在列中显示查询结果。

   结果会显示所有不住在伦敦的具有“orange.co.uk”电子邮件域的收件人。 不显示“名”列，因为在上一阶段未选中该列。 帐号按降序排序。

   ![](assets/query_editor_nveau_12.png)

   **[!UICONTROL XML result]**&#x200B;选项卡以XML格式显示结果。

   ![](assets/query_editor_nveau_13.png)

   **[!UICONTROL Generated QSL queries]**&#x200B;选项卡以SQL格式显示查询结果。

   ![](assets/query_editor_nveau_14.png)
