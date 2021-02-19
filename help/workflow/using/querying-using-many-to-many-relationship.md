---
solution: Campaign Classic
product: campaign
title: 使用多对多关系进行查询
description: 了解如何使用多对多关系执行查询
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---


# 使用多对多关系{#querying-using-a-many-to-many-relationship}进行查询

在此示例中，我们希望恢复过去7天内未联系的收件人。 此查询涉及所有投放。

此示例还说明如何配置与选择集合元素（或橙色节点）相关的筛选器。 集合元素在&#x200B;**[!UICONTROL Field to select]**&#x200B;窗口中可用。

* 需要选择哪个表？

   收件人表(**nms:收件人**)

* 要为输出列选择的字段

   主键、姓氏、名字和电子邮件

* 根据筛选的信息所依据的标准

   根据今天前7天前的投放日志收件人

应用以下步骤：

1. 打开通用查询编辑器并选择收件人表&#x200B;**[!UICONTROL (nms:recipient)]**。
1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Primary key]**、**[!UICONTROL First name]**、**[!UICONTROL Last name]**&#x200B;和&#x200B;**[!UICONTROL Email]**。

   ![](assets/query_editor_nveau_33.png)

1. 在排序窗口中，按字母顺序对名称排序。

   ![](assets/query_editor_nveau_34.png)

1. 在&#x200B;**[!UICONTROL Data filtering]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Filtering conditions]**。
1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;窗口中，用于提取过去7天没有跟踪日志的用户档案的筛选条件涉及两个步骤。 您需要选择的元素是多对多链接。

   * 开始：为第一个&#x200B;**[!UICONTROL Value]**&#x200B;列选择&#x200B;**[!UICONTROL Recipient delivery logs (broadlog)]**&#x200B;集合元素（橙色节点）。

      ![](assets/query_editor_nveau_67.png)

      选择&#x200B;**[!UICONTROL do not exist as]**&#x200B;运算符。 无需在此行中选择第二个值。

   * 第二过滤条件的内容取决于第一过滤条件。 此处，**[!UICONTROL Event date]**&#x200B;字段直接提供在&#x200B;**[!UICONTROL Recipient delivery logs]**&#x200B;表中，因为有指向此表的链接。

      ![](assets/query_editor_nveau_36.png)

      使用&#x200B;**[!UICONTROL greater than or equal to]**&#x200B;运算符选择&#x200B;**[!UICONTROL Event date]**。 选择&#x200B;**[!UICONTROL DaysAgo (7)]**&#x200B;值。 要执行此操作，请单击&#x200B;**[!UICONTROL Value]**&#x200B;字段中的&#x200B;**[!UICONTROL Edit expression]**。 在&#x200B;**[!UICONTROL Formula type]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Process on dates]**&#x200B;和&#x200B;**[!UICONTROL Current date minus n days]**，将&quot;7&quot;作为值。

      ![](assets/query_editor_nveau_37.png)

      已配置过滤条件。

      ![](assets/query_editor_nveau_38.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，将姓氏切换为大写。 单击&#x200B;**[!UICONTROL Transformation]**&#x200B;列中的&#x200B;**[!UICONTROL Last name]**&#x200B;行，并在下拉菜单中选择&#x200B;**[!UICONTROL Switch to upper case]**。

   ![](assets/query_editor_nveau_39.png)

1. 使用&#x200B;**[!UICONTROL Add a calculated field]**&#x200B;函数将列插入数据预览窗口。

   在此示例中，在单列中添加一个计算字段，其中收件人的名和姓是。 单击&#x200B;**[!UICONTROL Add a calculated field]**&#x200B;函数。 在&#x200B;**[!UICONTROL Export calculated field definition]**&#x200B;窗口中，输入标签和内部名称并选择&#x200B;**[!UICONTROL JavaScript Expression]**&#x200B;类型。 然后输入以下表达式:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   单击 **[!UICONTROL OK]**。已配置&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口。

   有关添加计算字段的详细信息，请参阅此部分。

1. 结果显示在&#x200B;**[!UICONTROL Data preview]**&#x200B;窗口中。 过去7天内未联系的收件人按字母顺序显示。 名称以大写显示，已创建具有名和姓的列。

   ![](assets/query_editor_nveau_41.png)
