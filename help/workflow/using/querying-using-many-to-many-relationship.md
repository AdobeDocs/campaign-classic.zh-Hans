---
title: 使用多对多关系进行查询
description: 了解如何使用多对多关系执行查询
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


# 使用多对多关系进行查询 {#querying-using-a-many-to-many-relationship}

在此示例中，我们希望恢复过去7天内未联系的收件人。 此查询涉及所有提交。

此示例还说明如何配置与选择集合元素（或橙色节点）相关的筛选器。 集合元素在窗口中可 **[!UICONTROL Field to select]** 用。

* 需要选择哪个表？

   收件人表(**nms:recipient**)

* 要为输出列选择的字段

   主键、姓、名和电子邮件

* 根据筛选的信息所依据的条件

   基于今天前7天收件人的交付日志

应用以下步骤：

1. 打开“通用查询编辑器”，然后选择“收件人”表 **[!UICONTROL (nms:recipient)]**。
1. 在窗 **[!UICONTROL Data to extract]** 口中，选 **[!UICONTROL Primary key]**&#x200B;择、 **[!UICONTROL First name]**&#x200B;和 **[!UICONTROL Last name]****[!UICONTROL Email]**。

   ![](assets/query_editor_nveau_33.png)

1. 在排序窗口中，按字母顺序对名称排序。

   ![](assets/query_editor_nveau_34.png)

1. 在窗口 **[!UICONTROL Data filtering]** 中，选择 **[!UICONTROL Filtering conditions]**。
1. 在窗口 **[!UICONTROL Target element]** 中，用于提取最近7天没有跟踪日志的配置文件的过滤条件涉及两个步骤。 您需要选择的元素是多对多链接。

   * 首先，为第一 **[!UICONTROL Recipient delivery logs (broadlog)]** 列选择集合元素(橙色节 **[!UICONTROL Value]** 点)。

      ![](assets/query_editor_nveau_67.png)

      选择运 **[!UICONTROL do not exist as]** 算符。 无需在此行中选择第二个值。

   * 第二过滤条件的内容取决于第一过滤条件。 此处，该 **[!UICONTROL Event date]** 字段直接在表中提 **[!UICONTROL Recipient delivery logs]** 供，因为有指向此表的链接。

      ![](assets/query_editor_nveau_36.png)

      使用 **[!UICONTROL Event date]** 运算符进 **[!UICONTROL greater than or equal to]** 行选择。 选择 **[!UICONTROL DaysAgo (7)]** 值。 要执行此操作，请单 **[!UICONTROL Edit expression]** 击字 **[!UICONTROL Value]** 段。 在窗 **[!UICONTROL Formula type]** 口中，选 **[!UICONTROL Process on dates]** 择 **[!UICONTROL Current date minus n days]**&#x200B;并赋值“7”。

      ![](assets/query_editor_nveau_37.png)

      过滤器条件已配置。

      ![](assets/query_editor_nveau_38.png)

1. 在窗 **[!UICONTROL Data formatting]** 口中，将姓氏切换为大写。 单击 **[!UICONTROL Last name]** 列中的行， **[!UICONTROL Transformation]** 然后在下 **[!UICONTROL Switch to upper case]** 拉菜单中选择。

   ![](assets/query_editor_nveau_39.png)

1. 使用该 **[!UICONTROL Add a calculated field]** 函数可在数据预览窗口中插入列。

   在此示例中，在单列中添加一个计算字段，其中包含收件人的名字和姓氏。 单击该 **[!UICONTROL Add a calculated field]** 函数。 在窗口 **[!UICONTROL Export calculated field definition]** 中，输入标签和内部名称，然后选择类 **[!UICONTROL JavaScript Expression]** 型。 然后输入以下表达式：

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   单击 **[!UICONTROL OK]**. 窗 **[!UICONTROL Data formatting]** 口已配置。

   有关添加计算字段的详细信息，请参阅此部分。

1. 结果显示在窗 **[!UICONTROL Data preview]** 口中。 过去7天内尚未联系的收件人按字母顺序显示。 名称以大写显示，并且已创建具有名和姓的列。

   ![](assets/query_editor_nveau_41.png)
