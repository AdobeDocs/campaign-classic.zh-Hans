---
product: campaign
title: 查询收件人表
description: 了解如何查询收件人表
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 5%

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

  是，基于 **[!UICONTROL Account number]** 和 **[!UICONTROL Last name]**

要创建此示例，请应用以下步骤：

1. 单击 **[!UICONTROL Tools > Generic query editor...]** 并选择 **收件人** (**nms：recipient**)表。 然后单击 **[!UICONTROL Next]**。
1. 选择： **[!UICONTROL Last name]**， **[!UICONTROL First name]**， **[!UICONTROL Email]**， **[!UICONTROL City]** 和 **[!UICONTROL Account number]**. 这些字段已添加到 **[!UICONTROL Output columns]**. 然后单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_03.png)

1. 对列进行排序，以按正确的顺序显示它们。 在这里，我们要按降序对帐号进行排序，并按字母顺序对名称进行排序。 然后单击 **[!UICONTROL Next]**。

   ![](assets/query_editor_04.png)

1. 在 **[!UICONTROL Data filtering]** 窗口，优化您的搜索：选择 **[!UICONTROL Filtering conditions]** 并单击 **[!UICONTROL Next]**.
1. 此 **[!UICONTROL Target element]** 窗口允许您输入过滤器设置。

   定义以下筛选条件：电子邮件域等于“orange.co.uk”的收件人。 要执行此操作，请选择 **电子邮件域(@email)** 在 **[!UICONTROL Expression]** 列，选择 **等于** 在 **[!UICONTROL Operator]** 列并在中输入“orange.co.uk” **[!UICONTROL Value]** 列。

   ![](assets/query_editor_05.png)

1. 如果需要，请单击 **[!UICONTROL Distribution of values]** 按钮以查看基于潜在客户电子邮件域的分发。 对于数据库中的每个电子邮件域，都有一个百分比可用。 在应用过滤器之前，将显示“orange.co.uk”以外的域。

   查询摘要显示在窗口底部： **电子邮件域等于“orange.co.uk”**.

1. 单击 **[!UICONTROL Preview]** 要了解查询结果，请仅显示“orange.co.uk”电子邮件域。

   ![](assets/query_editor_nveau_17.png)

1. 现在，我们将更改查询以查找不住在伦敦的联系人。

   选择 **[!UICONTROL City (location/@city)]** 在 **[!UICONTROL Expression]** 列， **[!UICONTROL different from]** 作为运算符，并输入 **[!UICONTROL London]** 在 **[!UICONTROL Value]** 列。

   ![](assets/query_editor_08.png)

1. 这会将您转到 **[!UICONTROL Data formatting]** 窗口。 检查列顺序。 将“City”列向上移动到“Account number”列下。

   取消选中“名字”列以将其从列表中删除。

   ![](assets/query_editor_nveau_15.png)

1. 在 **[!UICONTROL Data preview]** 窗口，单击 **[!UICONTROL Start the preview of the data]**. 此函数计算查询的结果。

   此 **[!UICONTROL Column results]** 选项卡以列显示查询结果。

   结果会显示所有具有“orange.co.uk”电子邮件域的收件人，这些收件人不在伦敦居住。 “名字”列未显示，因为它在上一阶段中未被选中。 帐号按降序排序。

   ![](assets/query_editor_nveau_12.png)

   此 **[!UICONTROL XML result]** 选项卡以XML格式显示结果。

   ![](assets/query_editor_nveau_13.png)

   此 **[!UICONTROL Generated QSL queries]** 选项卡以SQL格式显示查询结果。

   ![](assets/query_editor_nveau_14.png)
