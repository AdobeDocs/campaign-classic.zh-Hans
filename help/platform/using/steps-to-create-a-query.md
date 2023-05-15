---
product: campaign
title: 创建查询的步骤
description: 创建查询的步骤
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: cf914366-8bac-4d68-a0cc-2a43d102eef2
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# 创建查询的步骤{#steps-to-create-a-query}



在Adobe Campaign中构建查询的步骤如下：

1. 选择工作表。 请参阅 [步骤1 — 选择表](#step-1---choose-a-table).
1. 选择要提取的数据。 请参阅 [步骤2 — 选择要提取的数据](#step-2---choose-data-to-extract).
1. 定义数据排序序列。 请参阅 [步骤3 — 对数据排序](#step-3---sort-data).
1. 过滤数据。 请参阅 [步骤4 — 过滤数据](#step-4---filter-data).
1. 设置数据格式。 请参阅 [步骤5 — 设置数据格式](#step-5---format-data).
1. 显示结果。 请参阅 [步骤6 — 预览数据](#step-6---preview-data).

>[!NOTE]
>
>所有这些步骤在通用查询编辑器中均可用。 在其他上下文中创建查询时，可以忽略某些步骤。\
>查询活动在 [此部分](../../workflow/using/query.md).

## 步骤1 — 选择表 {#step-1---choose-a-table}

选择包含要在 **[!UICONTROL Document type]** 窗口。 如有必要，请使用过滤器字段或 **[!UICONTROL Filters]** 按钮。

![](assets/query_editor_nveau_21.png)

## 步骤2 — 选择要提取的数据 {#step-2---choose-data-to-extract}

在 **[!UICONTROL Data to extract]** 窗口中，选择要显示的数据：这些字段将构成输出列。

例如，选择 **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** 和 **[!UICONTROL City]**. 结果将根据此选择进行组织。 使用窗口右侧的蓝色箭头可更改列顺序。

![](assets/query_editor_nveau_01.png)

您可以通过在表达式中插入公式或对聚合函数运行进程来编辑表达式。 为此，请单击 **[!UICONTROL Expression]** 列字段，然后选择 **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

可以将输出列数据分组：为此，请检查 **[!UICONTROL Yes]** 在 **[!UICONTROL Group]** 列 **[!UICONTROL Data to extract]** 窗口。 此函数围绕检查的分组轴生成结果。 有关具有分组的查询的示例，请参阅 [此部分](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* 的 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 函数允许您“按”分组并选择已分组的内容（“有”）。 此函数适用于输出列中的所有字段。 例如，此选项允许您对输出列的所有选项进行分组并恢复特定类型的信息，如35到50之间的收件人。

   如需详细信息，请参阅[此部分](../../workflow/using/querying-using-grouping-management.md)。

* 的 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 函数可删除在输出列中获得的重复相同结果。 例如，如果通过选择输出列中的姓氏、名字和电子邮件字段进行普查，则将删除具有相同数据的字段，因为这意味着在数据库中已多次输入相同联系人：只考虑一个结果。

## 步骤3 — 对数据排序 {#step-3---sort-data}

的 **[!UICONTROL Sorting]** 窗口允许您对列内容进行排序。 使用箭头更改列顺序：

* 的 **[!UICONTROL Sorting]** 列允许对列内容进行简单排序，并按升序排列从A到Z的内容。
* 的 **[!UICONTROL Descending sort]** 按降序将内容从Z排列到A。 这对于查看记录销售额(例如：最高的数字显示在列表顶部。

在此示例中，数据根据收件人年龄以升序方式排序。

![](assets/query_editor_nveau_57.png)

## 步骤4 — 过滤数据 {#step-4---filter-data}

通过查询编辑器，您可以过滤数据以优化搜索。

提供的过滤器取决于查询所关注的表。

![](assets/query_editor_nveau_09.png)

选择 **[!UICONTROL Filtering conditions]** 您将访问 **[!UICONTROL Target elements]** 部分：这可让您定义如何过滤要收集的数据。

* 要创建新过滤器，请选择创建要验证的公式所需的字段、运算符和值，以便选择要验证的数据。 可以合并多个条件(有关更多信息，请参阅 [定义筛选条件](../../platform/using/defining-filter-conditions.md))。
* 要使用之前保存的过滤器，请通过单击 **[!UICONTROL Add]** 按钮，单击 **[!UICONTROL Predefined filter]** 然后选择您想要的。

   ![](assets/query_editor_15.png)

* 在 **[!UICONTROL Generic query editor]** 在其他查询应用程序中可用，反之亦然。 要保存过滤器，请单击 **[!UICONTROL Save]** 图标。

   >[!NOTE]
   >
   >有关创建和使用过滤器的更多信息，请参阅 [筛选选项](../../platform/using/filtering-options.md).

如以下示例所示，要取回所有讲英语的收件人，请选择：“收件人语言” **等于** EN”。

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>您可以在 **值** 字段： **$(options:OPTION_NAME)**.

单击 **[!UICONTROL Preview]** 选项卡来查看筛选条件的结果。 在这种情况下，所有讲英语的收件人都会显示其姓名、名字和电子邮件地址。

![](assets/query_editor_nveau_98.png)

熟悉SQL语言的用户可以单击 **[!UICONTROL Generate SQL query]** 以在SQL中查看查询。

![](assets/query_editor_nveau_99.png)

## 步骤5 — 设置数据格式 {#step-5---format-data}

配置限制过滤器后，您将访问 **[!UICONTROL Data formatting]** 窗口。 利用此窗口，可重新排列输出列、转换数据，并更改列标签的大小写。 它还允许您使用计算字段将公式应用到最终结果。

>[!NOTE]
>
>有关计算字段类型的更多信息，请参阅 [创建计算字段](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

数据预览窗口中不显示未选中的列。

![](assets/query_editor_nveau_10.png)

的 **[!UICONTROL Transformation]** 列可将列标签更改为大写或小写。 选择列，然后在 **[!UICONTROL Transformation]** 列。 您可以选择：

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 步骤6 — 预览数据 {#step-6---preview-data}

的 **[!UICONTROL Data preview]** 窗口是最后一步。 单击 **[!UICONTROL Start the preview of the data]** 以获取查询结果。 它以列或XML格式提供。 单击 **[!UICONTROL Generated SQL queries]** 选项卡，以查看SQL格式的查询。

在此示例中，数据根据收件人年龄以升序排序。

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>默认情况下，仅在 **[!UICONTROL Data preview]** 窗口。 要更改此值，请在 **[!UICONTROL Lines to display]** 框，单击 **[!UICONTROL Start the preview of the data]**.
