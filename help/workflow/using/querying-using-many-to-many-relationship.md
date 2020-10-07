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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---


# 使用多对多关系进行查询 {#querying-using-a-many-to-many-relationship}

在此示例中，我们要恢复过去7天内未联系的收件人。 此查询涉及所有投放。

此示例还说明如何配置与选择集合元素（或橙色节点）相关的筛选器。 收藏元素在窗口中 **[!UICONTROL Field to select]** 可用。

* 需要选择哪个表？

   收件人表(**nms:收件人**)

* 要为输出列选择的字段

   主键、姓、名和电子邮件

* 根据筛选信息时的条件

   根据前七天前投放日志的收件人

应用以下步骤：

1. 打开通用查询编辑器并选择收件人表 **[!UICONTROL (nms:recipient)]**。
1. 在窗 **[!UICONTROL Data to extract]** 口中， **[!UICONTROL Primary key]**&#x200B;选择 **[!UICONTROL First name]**、 **[!UICONTROL Last name]** 和 **[!UICONTROL Email]**。

   ![](assets/query_editor_nveau_33.png)

1. 在排序窗口中，按字母顺序对名称排序。

   ![](assets/query_editor_nveau_34.png)

1. In the **[!UICONTROL Data filtering]** window, select **[!UICONTROL Filtering conditions]**.
1. 在窗 **[!UICONTROL Target element]** 口中，过去7天没有跟踪日志的用户档案提取过滤条件涉及两个步骤。 您需要选择的元素是多对多链接。

   * 开始，方法 **[!UICONTROL Recipient delivery logs (broadlog)]** 是为第一列选择集合元素(橙色 **[!UICONTROL Value]** 节点)。

      ![](assets/query_editor_nveau_67.png)

      选择运 **[!UICONTROL do not exist as]** 算符。 无需在此行中选择第二个值。

   * 第二过滤条件的内容取决于第一过滤条件。 此处， **[!UICONTROL Event date]** 表中直接提供该字 **[!UICONTROL Recipient delivery logs]** 段，因为有指向此表的链接。

      ![](assets/query_editor_nveau_36.png)

      使用 **[!UICONTROL Event date]** 运算符进 **[!UICONTROL greater than or equal to]** 行选择。 选择 **[!UICONTROL DaysAgo (7)]** 值。 要执行此操作，请 **[!UICONTROL Edit expression]** 单击字 **[!UICONTROL Value]** 段。 在窗 **[!UICONTROL Formula type]** 口中，选 **[!UICONTROL Process on dates]** 择 **[!UICONTROL Current date minus n days]**&#x200B;并，将“7”作为值。

      ![](assets/query_editor_nveau_37.png)

      已配置过滤条件。

      ![](assets/query_editor_nveau_38.png)

1. 在窗 **[!UICONTROL Data formatting]** 口中，将姓氏切换为大写。 单击 **[!UICONTROL Last name]** 列中的 **[!UICONTROL Transformation]** 行，然 **[!UICONTROL Switch to upper case]** 后在下拉菜单中选择。

   ![](assets/query_editor_nveau_39.png)

1. 使用函 **[!UICONTROL Add a calculated field]** 数将列插入数据预览窗口。

   在此示例中，在单个列中添加一个计算字段，其中包含收件人的名和姓。 单击该 **[!UICONTROL Add a calculated field]** 函数。 在窗口 **[!UICONTROL Export calculated field definition]** 中，输入标签和内部名称并选择类 **[!UICONTROL JavaScript Expression]** 型。 然后输入以下表达式:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   单击 **[!UICONTROL OK]**。窗 **[!UICONTROL Data formatting]** 口已配置。

   有关添加计算字段的详细信息，请参阅此部分。

1. 结果显示在窗 **[!UICONTROL Data preview]** 口中。 过去7天内未联系的收件人按字母顺序显示。 名称以大写显示，已创建具有名和姓的列。

   ![](assets/query_editor_nveau_41.png)
