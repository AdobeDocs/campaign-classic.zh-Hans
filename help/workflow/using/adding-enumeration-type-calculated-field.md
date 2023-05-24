---
product: campaign
title: 添加明细列表类型计算字段
description: 了解如何添加明细列表类型计算字段
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---

# 添加明细列表类型计算字段 {#adding-an-enumeration-type-calculated-field}



在此，我们希望使用 **[!UICONTROL Enumerations]** 键入计算字段。 此字段将在数据预览窗口中生成附加列。 此列将指定作为每个收件人（0、1和2）的结果返回的数值。 将为新列中的每个值指定性别：如果值等于“0”，则“1”为“男性”、“2”为“女性”或“未指示”。

* 需要选择哪个表？

   收件人表(nms：recipient)

* 要在输出列中选择的字段？

   姓氏，名字，性别

* 信息过滤所依据的标准？

   收件人语言

应用以下步骤：

1. 打开通用查询编辑器并选择收件人表(**[!UICONTROL nms:recipient]**)。
1. 在 **[!UICONTROL Data to extract]** 窗口，选择 **[!UICONTROL Last name]**， **[!UICONTROL First name]** 和 **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. 在 **[!UICONTROL Sorting]** 窗口，单击 **[!UICONTROL Next]**：此示例无需排序。
1. 在 **[!UICONTROL Data filtering]** 中，选择 **[!UICONTROL Filtering conditions]**。
1. 在 **[!UICONTROL Target element]** 窗口中，设置筛选条件以收集讲英语的收件人。

   ![](assets/query_editor_nveau_74.png)

1. 在 **[!UICONTROL Data formatting]** 窗口，单击 **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. 转到 **[!UICONTROL Type]** 窗口 **[!UICONTROL Export calculated field definition]** 窗口并选择 **[!UICONTROL Enumerations]**.

   定义新计算字段必须引用的列。 要执行此操作，请选择 **[!UICONTROL Gender]** 的下拉菜单中的列 **[!UICONTROL Source column]** 字段：目标值将与 **[!UICONTROL Gender]** 列。

   ![](assets/query_editor_nveau_76.png)

   定义 **来源** 和 **目标** 值：目标值使查询结果更易于读取。 此查询应返回收件人性别，结果将为0、1或2。

   对于要输入的每个“source-destination”行，单击 **[!UICONTROL Add]** 在 **[!UICONTROL List of enumeration values]**：

   * 在 **[!UICONTROL Source]** 列，在新行中输入每个性别(0、1、2)的源值。
   * 在 **[!UICONTROL Destination]** 列，输入以下值：行“0”为“未指示”，行“1”为“男性”，行“2”为“女性”。

   选择 **[!UICONTROL Keep the source value]** 函数。

   单击 **[!UICONTROL OK]** 以批准计算字段。

   ![](assets/query_editor_nveau_77.png)

1. 在 **[!UICONTROL Data formatting]** 窗口，单击 **[!UICONTROL Next]**.
1. 在预览窗口中， **[!UICONTROL start the preview of the data]**.

   附加列定义了0、1和2的性别：

   * 0表示“未指示”
   * 1表示“男性”
   * 2表示“女性”

   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在 **[!UICONTROL List of enumeration values]**，以及 **[!UICONTROL Generate a warning and continue]** 的功能 **[!UICONTROL In other cases]** 字段时，您将获得一个警告日志。 此日志指示尚未输入性别“2”（女性）。 它显示在 **[!UICONTROL Logs generated during export]** 数据预览窗口的字段。

   ![](assets/query_editor_nveau_79.png)

   让我们再举一个例子，说明没有输入枚举值“2”。 选择 **[!UICONTROL Generate an error and reject the line]** 函数：所有性别“2”的收件人将引发异常信息以及行中的其他信息（名字和姓氏等） 将不会导出。 错误日志显示在 **[!UICONTROL Logs generated during export]** 数据预览窗口的字段。 此日志指示未输入枚举值“2”。

   ![](assets/query_editor_nveau_80.png)
