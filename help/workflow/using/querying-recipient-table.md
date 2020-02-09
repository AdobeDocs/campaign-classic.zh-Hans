---
title: 查询收件人表
description: 了解如何查询收件人表
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
source-git-commit: ab2c133aaa2f754e56fe8fdfc76d10526d4d1ce2

---


# 查询收件人表 {#querying-recipient-table}

在此示例中，我们希望恢复电子邮件域为“orange.co.uk”且不住在伦敦的收件人的姓名和电子邮件。

* 我们应选择哪张表？

   收件人表（nms：收件人）

* 要选择为输出列的字段

   电子邮件、姓名、城市和帐户号

* 收件人的过滤条件是什么？

   城市和电子邮件域

* 是否配置了类型？

   是，基于和 **[!UICONTROL Account number]****[!UICONTROL Last name]**

要创建此示例，请应用以下步骤：

1. 单击 **[!UICONTROL Tools > Generic query editor...]** 并选择“收 **件人** (nms:**recipient**)”表。 然后单击 **[!UICONTROL Next]**。
1. 选择： **[!UICONTROL Last name]**、 **[!UICONTROL First name]****[!UICONTROL Email]**、 **[!UICONTROL City]** 和 **[!UICONTROL Account number]**。 这些字段将添加到 **[!UICONTROL Output columns]**。 然后单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_03.png)

1. 对列进行排序以按正确的顺序显示它们。 此处，我们希望按降序对帐户编号排序，按字母顺序对名称排序。 然后单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_04.png)

1. 在窗口 **[!UICONTROL Data filtering]** 中，优化搜索：选择 **[!UICONTROL Filtering conditions]** 并单击 **[!UICONTROL Next]**。
1. 在窗 **[!UICONTROL Target element]** 口中可以输入筛选器设置。

   定义以下过滤条件：电子邮件域等于“orange.co.uk”的收件人。 为此，请在列中选 **择“电子邮件域(@email)** ”，在列 **[!UICONTROL Expression]** 中选择等于 **,** 然后在列中输入“orange.co.uk” **[!UICONTROL Operator]****[!UICONTROL Value]** 。

   ![](assets/query_editor_05.png)

1. 如果需要，请单击 **[!UICONTROL Distribution of values]** 该按钮以根据潜在客户的电子邮件域查看分发。 数据库中每个电子邮件域都有一个百分比。 除“orange.co.uk”之外的域将一直显示，直到应用过滤器。

   查询摘要显示在窗口底部：电 **子邮件域等于“orange.co.uk”**。

1. 单击 **[!UICONTROL Preview]** 可了解查询结果：只显示“orange.co.uk”电子邮件域。

   ![](assets/query_editor_nveau_17.png)

1. 我们现在将更改查询，以查找不住在伦敦的联系人。

   在列 **[!UICONTROL City (location/@city)]** 中选 **[!UICONTROL Expression]** 择，作 **[!UICONTROL different from]** 为运算符，然后 **[!UICONTROL London]** 在列中 **[!UICONTROL Value]** 输入。

   ![](assets/query_editor_08.png)

1. 这会带你到窗 **[!UICONTROL Data formatting]** 户。 检查列顺序。 在“帐户编号”列下向上移动“城市”列。

   取消选中“名”列，将其从列表中删除。

   ![](assets/query_editor_nveau_15.png)

1. 在窗口 **[!UICONTROL Data preview]** 中，单击 **[!UICONTROL Start the preview of the data]**。 此函数计算查询的结果。

   该选 **[!UICONTROL Column results]** 项卡在列中显示查询结果。

   结果显示所有收件人都有“orange.co.uk”电子邮件域名，他们不住在伦敦。 不显示“名”列，因为在上一阶段中未选中该列。 帐号按降序排序。

   ![](assets/query_editor_nveau_12.png)

   该选 **[!UICONTROL XML result]** 项卡以XML格式显示结果。

   ![](assets/query_editor_nveau_13.png)

   该选 **[!UICONTROL Generated QSL queries]** 项卡以SQL格式显示查询结果。

   ![](assets/query_editor_nveau_14.png)
