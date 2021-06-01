---
product: campaign
title: 使用多对多关系进行查询
description: 了解如何使用多对多关系执行查询
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---

# 使用多对多关系进行查询{#querying-using-a-many-to-many-relationship}

在本例中，我们希望恢复过去7天内未联系的收件人。 此查询涉及所有投放。

此示例还显示如何配置与选择收藏集元素（或橙色节点）相关的过滤器。 集合元素在&#x200B;**[!UICONTROL Field to select]**&#x200B;窗口中可用。

* 需要选择哪个表？

   收件人表(**nms:recipient**)

* 要为输出列选择的字段

   主键、姓氏、名字和电子邮件

* 根据过滤的信息所依据的条件

   基于今天之前7天收件人的投放日志

应用以下步骤：

1. 打开通用查询编辑器并选择收件人表&#x200B;**[!UICONTROL (nms:recipient)]**。
1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Primary key]**、**[!UICONTROL First name]**、**[!UICONTROL Last name]**&#x200B;和&#x200B;**[!UICONTROL Email]**。

   ![](assets/query_editor_nveau_33.png)

1. 在排序窗口中，按字母顺序对名称进行排序。

   ![](assets/query_editor_nveau_34.png)

1. 在&#x200B;**[!UICONTROL Data filtering]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Filtering conditions]**。
1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;窗口中，用于提取过去7天内没有跟踪日志的用户档案的筛选条件包含两个步骤。 您需要选择的元素是一个多对多链接。

   * 首先，为第一个&#x200B;**[!UICONTROL Value]**&#x200B;列选择&#x200B;**[!UICONTROL Recipient delivery logs (broadlog)]**&#x200B;收集元素（橙色节点）。

      ![](assets/query_editor_nveau_67.png)

      选择&#x200B;**[!UICONTROL do not exist as]**&#x200B;运算符。 无需在此行中选择第二个值。

   * 第二个筛选条件的内容取决于第一个筛选条件。 在此，**[!UICONTROL Event date]**&#x200B;字段直接提供在&#x200B;**[!UICONTROL Recipient delivery logs]**&#x200B;表中，因为有指向此表的链接。

      ![](assets/query_editor_nveau_36.png)

      使用&#x200B;**[!UICONTROL greater than or equal to]**&#x200B;运算符选择&#x200B;**[!UICONTROL Event date]**。 选择&#x200B;**[!UICONTROL DaysAgo (7)]**&#x200B;值。 要实现此目的，请单击&#x200B;**[!UICONTROL Value]**&#x200B;字段中的&#x200B;**[!UICONTROL Edit expression]**。 在&#x200B;**[!UICONTROL Formula type]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Process on dates]**&#x200B;和&#x200B;**[!UICONTROL Current date minus n days]**，将&quot;7&quot;作为值。

      ![](assets/query_editor_nveau_37.png)

      已配置筛选条件。

      ![](assets/query_editor_nveau_38.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，将姓氏切换为大写。 单击&#x200B;**[!UICONTROL Transformation]**&#x200B;列中的&#x200B;**[!UICONTROL Last name]**&#x200B;行，然后在下拉菜单中选择&#x200B;**[!UICONTROL Switch to upper case]**。

   ![](assets/query_editor_nveau_39.png)

1. 使用&#x200B;**[!UICONTROL Add a calculated field]**&#x200B;函数将列插入数据预览窗口。

   在此示例中，在单列中添加一个包含收件人名字和姓氏的计算字段。 单击&#x200B;**[!UICONTROL Add a calculated field]**&#x200B;函数。 在&#x200B;**[!UICONTROL Export calculated field definition]**&#x200B;窗口中，输入标签和内部名称，然后选择&#x200B;**[!UICONTROL JavaScript Expression]**&#x200B;类型。 然后输入以下表达式：

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   单击 **[!UICONTROL OK]**。**[!UICONTROL Data formatting]**&#x200B;窗口已配置。

   有关添加计算字段的更多信息，请参阅此章节。

1. 结果显示在&#x200B;**[!UICONTROL Data preview]**&#x200B;窗口中。 过去7天内未联系的收件人按字母顺序显示。 名称以大写显示，并且已创建具有名字和姓氏的列。

   ![](assets/query_editor_nveau_41.png)
