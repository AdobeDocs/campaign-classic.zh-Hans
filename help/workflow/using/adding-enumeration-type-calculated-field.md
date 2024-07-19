---
product: campaign
title: 添加明细列表类型计算字段
description: 了解如何添加明细列表类型计算字段
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 1%

---

# 添加明细列表类型计算字段 {#adding-an-enumeration-type-calculated-field}



在此处，我们要创建具有&#x200B;**[!UICONTROL Enumerations]**&#x200B;类型计算字段的查询。 此字段将在数据预览窗口中生成附加列。 此列将指定作为每个收件人（0、1和2）的结果返回的数值。 将为新列中的每个值指定性别：如果值等于“0”，则“1”为“男性”、“2”为“女性”或“未指示”。

* 需要选择哪个表？

  收件人表(nms：recipient)

* 要在输出列中选择的字段？

  姓氏，名字，性别

* 将基于哪些标准筛选信息？

  收件人语言

应用以下步骤：

1. 打开通用查询编辑器并选择收件人表(**[!UICONTROL nms:recipient]**)。
1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Last name]**、**[!UICONTROL First name]**&#x200B;和&#x200B;**[!UICONTROL Gender]**。

   ![](assets/query_editor_nveau_73.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**：此示例不需要排序。
1. 在 **[!UICONTROL Data filtering]** 中，选择 **[!UICONTROL Filtering conditions]**。
1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;窗口中，设置筛选条件以收集讲英语的收件人。

   ![](assets/query_editor_nveau_74.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Add a calculated field]**。

   ![](assets/query_editor_nveau_75.png)

1. 转到&#x200B;**[!UICONTROL Export calculated field definition]**&#x200B;窗口的&#x200B;**[!UICONTROL Type]**&#x200B;窗口并选择&#x200B;**[!UICONTROL Enumerations]**。

   定义新计算字段必须引用的列。 为此，请在&#x200B;**[!UICONTROL Source column]**&#x200B;字段的下拉菜单中选择&#x200B;**[!UICONTROL Gender]**&#x200B;列：目标值将与&#x200B;**[!UICONTROL Gender]**&#x200B;列一致。

   ![](assets/query_editor_nveau_76.png)

   定义&#x200B;**Source**&#x200B;和&#x200B;**目标**&#x200B;值：目标值使查询结果更易于读取。 此查询应返回收件人性别，结果将为0、1或2。

   对于要输入的每个“source-destination”行，单击&#x200B;**[!UICONTROL List of enumeration values]**&#x200B;中的&#x200B;**[!UICONTROL Add]**：

   * 在&#x200B;**[!UICONTROL Source]**&#x200B;列中，在新行中输入每个性别的源值(0,1，2)。
   * 在&#x200B;**[!UICONTROL Destination]**&#x200B;列中，输入以下值：行“0”为“未指示”，行“1”为“男性”，行“2”为“女性”。

   选择&#x200B;**[!UICONTROL Keep the source value]**&#x200B;函数。

   单击&#x200B;**[!UICONTROL OK]**&#x200B;以批准计算字段。

   ![](assets/query_editor_nveau_77.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**。
1. 在预览窗口中，**[!UICONTROL start the preview of the data]**。

   附加列定义了0、1和2的性别：

   * 0表示“未指示”
   * 1表示“男性”
   * 2表示“女”

   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在&#x200B;**[!UICONTROL List of enumeration values]**&#x200B;中输入性别“2”，并且选择了&#x200B;**[!UICONTROL In other cases]**&#x200B;字段的&#x200B;**[!UICONTROL Generate a warning and continue]**&#x200B;函数，您将获得一个警告日志。 此日志指示尚未输入性别“2”（女性）。 它显示在数据预览窗口的&#x200B;**[!UICONTROL Logs generated during export]**&#x200B;字段中。

   ![](assets/query_editor_nveau_79.png)

   再举一个例子，说明没有输入枚举值“2”。 选择&#x200B;**[!UICONTROL Generate an error and reject the line]**&#x200B;函数：所有性别“2”收件人将在行中引发异常和其他信息（名字和姓氏等） 将不会导出。 数据预览窗口的&#x200B;**[!UICONTROL Logs generated during export]**&#x200B;字段中将显示错误日志。 此日志指示未输入枚举值“2”。

   ![](assets/query_editor_nveau_80.png)
