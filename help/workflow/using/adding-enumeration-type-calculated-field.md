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


# Adding an Enumeration type calculated field {#adding-an-enumeration-type-calculated-field}

在此，我们要创建一个带有类型计算字 **[!UICONTROL Enumerations]** 段的查询。 此字段将在数据预览窗口中生成其他列。 此列将指定作为每个收件人（0、1和2）的结果返回的数值。 新列中的每个值将分配一个性别：“Male”表示“1”,“Male”表示“2”，或“Not issided”（如果值等于“0”）。

* 需要选择哪个表？

   收件人表(nms:收件人)

* 要在输出列中选择的字段？

   姓氏、名字、性别

* 要根据哪个标准筛选信息？

   收件人语言

应用以下步骤：

1. 打开通用查询编辑器并选择收件人表(**[!UICONTROL nms:recipient]**)。
1. 在窗 **[!UICONTROL Data to extract]** 口中，选 **[!UICONTROL Last name]**&#x200B;择 **[!UICONTROL First name]** 和 **[!UICONTROL Gender]**。

   ![](assets/query_editor_nveau_73.png)

1. 在窗口 **[!UICONTROL Sorting]** 中，单击 **[!UICONTROL Next]**:此示例无需排序。
1. 在 **[!UICONTROL Data filtering]** 中，选择 **[!UICONTROL Filtering conditions]**。
1. 在窗口 **[!UICONTROL Target element]** 中，设置过滤条件以收集说英语的收件人。

   ![](assets/query_editor_nveau_74.png)

1. In the **[!UICONTROL Data formatting]** window, click **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. 转到窗 **[!UICONTROL Type]** 口并选 **[!UICONTROL Export calculated field definition]** 择该窗口 **[!UICONTROL Enumerations]**。

   定义新计算字段必须引用的列。 为此，请在字 **[!UICONTROL Gender]** 段的下拉菜单中选择列 **[!UICONTROL Source column]** :目标值将与列重 **[!UICONTROL Gender]** 合。

   ![](assets/query_editor_nveau_76.png)

   定义 **源** 和 **目标值** :目标值使查询结果更易于阅读。 此查询应返回收件人性别，结果为0、1或2。

   对于要输入的每个“源——目标”行，请在 **[!UICONTROL Add]** 以下位置单 **[!UICONTROL List of enumeration values]**&#x200B;击：

   * 在列 **[!UICONTROL Source]** 中，在新行中输入每个性别(0,1,2)的源值。
   * 在列 **[!UICONTROL Destination]** 中，输入以下值：行“0”的“未指明”、行“1”的“Male”和行“2”的“Male”。

   选择函 **[!UICONTROL Keep the source value]** 数。

   单击 **[!UICONTROL OK]** 以批准计算字段。

   ![](assets/query_editor_nveau_77.png)

1. In the **[!UICONTROL Data formatting]** window, click **[!UICONTROL Next]**.
1. 在预览窗口 **[!UICONTROL start the preview of the data]**。

   附加一栏定义0、1和2的性别：

   * 0表示“未指明”
   * 1表示“男性”
   * 2表示“女性”

   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在中输入性别“2” **[!UICONTROL List of enumeration values]**，并且选 **[!UICONTROL Generate a warning and continue]** 择了 **[!UICONTROL In other cases]** 字段的函数，您将收到警告日志。 此日志表示未输入性别“2”（女性）。 它显示在数据 **[!UICONTROL Logs generated during export]** 预览窗口的字段中。

   ![](assets/query_editor_nveau_79.png)

   我们再举一个例子，说明细列表值“2”未输入。 选择函 **[!UICONTROL Generate an error and reject the line]** 数：所有性别“2”收件人都将引起异常和行中的其他信息（名字和姓氏等） 将不导出。 数据预览窗口的字 **[!UICONTROL Logs generated during export]** 段中显示错误日志。 此日志指示未输入明细列表值“2”。

   ![](assets/query_editor_nveau_80.png)
