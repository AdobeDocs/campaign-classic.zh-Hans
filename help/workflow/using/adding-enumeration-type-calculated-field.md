---
solution: Campaign Classic
product: campaign
title: 添加明细列表类型计算字段
description: 了解如何添加明细列表类型计算字段
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---


# 添加明细列表类型计算字段{#adding-an-enumeration-type-calculated-field}

此处，我们要创建一个具有&#x200B;**[!UICONTROL Enumerations]**&#x200B;类型计算字段的查询。 此字段将在数据预览窗口中生成其他列。 此列将指定作为每个收件人（0、1和2）的结果返回的数值。 新列中的每个值将分配一个性别：“Male”表示“1”,“Male”表示“2”，或“Not issided”（如果值等于“0”）。

* 需要选择哪个表？

   收件人表(nms:收件人)

* 要在输出列中选择的字段？

   姓氏、名字、性别

* 要根据哪个标准筛选信息？

   收件人语言

应用以下步骤：

1. 打开通用查询编辑器并选择收件人表(**[!UICONTROL nms:recipient]**)。
1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Last name]**、**[!UICONTROL First name]**&#x200B;和&#x200B;**[!UICONTROL Gender]**。

   ![](assets/query_editor_nveau_73.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**:此示例无需排序。
1. 在 **[!UICONTROL Data filtering]** 中，选择 **[!UICONTROL Filtering conditions]**。
1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;窗口中，设置过滤条件以收集说英语的收件人。

   ![](assets/query_editor_nveau_74.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Add a calculated field]**。

   ![](assets/query_editor_nveau_75.png)

1. 转到&#x200B;**[!UICONTROL Export calculated field definition]**&#x200B;窗口的&#x200B;**[!UICONTROL Type]**&#x200B;窗口，然后选择&#x200B;**[!UICONTROL Enumerations]**。

   定义新计算字段必须引用的列。 为此，请在&#x200B;**[!UICONTROL Source column]**&#x200B;字段的下拉菜单中选择&#x200B;**[!UICONTROL Gender]**&#x200B;列：目标值将与&#x200B;**[!UICONTROL Gender]**&#x200B;列一致。

   ![](assets/query_editor_nveau_76.png)

   定义&#x200B;**源**&#x200B;和&#x200B;**目标**&#x200B;值：目标值使查询结果更易于阅读。 此查询应返回收件人性别，结果为0、1或2。

   对于要输入的每行“source-destination”，单击&#x200B;**[!UICONTROL List of enumeration values]**&#x200B;中的&#x200B;**[!UICONTROL Add]**:

   * 在&#x200B;**[!UICONTROL Source]**&#x200B;列中，在新行中输入每个性别(0,1,2)的源值。
   * 在&#x200B;**[!UICONTROL Destination]**&#x200B;列中，输入以下值：行“0”的“未指明”、行“1”的“Male”和行“2”的“Male”。

   选择&#x200B;**[!UICONTROL Keep the source value]**&#x200B;函数。

   单击&#x200B;**[!UICONTROL OK]**&#x200B;以批准计算字段。

   ![](assets/query_editor_nveau_77.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Next]**。
1. 在预览窗口中， **[!UICONTROL start the preview of the data]**。

   附加一栏定义0、1和2的性别：

   * 0表示“未指明”
   * 1表示“男性”
   * 2表示“女性”

   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在&#x200B;**[!UICONTROL List of enumeration values]**&#x200B;中输入性别“2”，并且选择了&#x200B;**[!UICONTROL In other cases]**&#x200B;字段的&#x200B;**[!UICONTROL Generate a warning and continue]**&#x200B;函数，您将收到一个警告日志。 此日志表示未输入性别“2”（女性）。 它显示在数据预览窗口的&#x200B;**[!UICONTROL Logs generated during export]**&#x200B;字段中。

   ![](assets/query_editor_nveau_79.png)

   我们再举一个例子，说明细列表值“2”未输入。 选择&#x200B;**[!UICONTROL Generate an error and reject the line]**&#x200B;函数：所有性别“2”收件人都将引起异常和行中的其他信息（名字和姓氏等） 将不导出。 数据预览窗口的&#x200B;**[!UICONTROL Logs generated during export]**&#x200B;字段中显示错误日志。 此日志指示未输入明细列表值“2”。

   ![](assets/query_editor_nveau_80.png)
