---
product: campaign
title: 创建查询的步骤
description: 创建查询的步骤
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: cf914366-8bac-4d68-a0cc-2a43d102eef2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# 创建查询的步骤{#steps-to-create-a-query}

![](../../assets/common.svg)

在Adobe Campaign中构建查询的步骤如下：

1. 选择工作表。 请参阅[步骤1 — 选择表](#step-1---choose-a-table)。
1. 选择要提取的数据。 请参阅[步骤2 — 选择要提取的数据](#step-2---choose-data-to-extract)。
1. 定义数据排序序列。 请参阅[步骤3 — 对数据排序](#step-3---sort-data)。
1. 过滤数据。 请参阅[步骤4 — 过滤数据](#step-4---filter-data)。
1. 设置数据格式。 请参阅[步骤5 — 格式化数据](#step-5---format-data)。
1. 显示结果。 请参阅[步骤6 — 预览数据](#step-6---preview-data)。

>[!NOTE]
>
>所有这些步骤在通用查询编辑器中均可用。 在其他上下文中创建查询时，可以忽略某些步骤。\
>查询活动显示在[此部分](../../workflow/using/query.md)中。

## 步骤1 — 选择表 {#step-1---choose-a-table}

选择包含要在&#x200B;**[!UICONTROL Document type]**&#x200B;窗口中查询的数据的表。 如有必要，请使用filter字段或&#x200B;**[!UICONTROL Filters]**&#x200B;按钮过滤数据。

![](assets/query_editor_nveau_21.png)

## 步骤2 — 选择要提取的数据 {#step-2---choose-data-to-extract}

在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，选择要显示的数据：这些字段将构成输出列。

例如，选择&#x200B;**[!UICONTROL Age]**、**[!UICONTROL Primary key]**、**[!UICONTROL Email domain]**&#x200B;和&#x200B;**[!UICONTROL City]**。 结果将根据此选择进行组织。 使用窗口右侧的蓝色箭头可更改列顺序。

![](assets/query_editor_nveau_01.png)

您可以通过在表达式中插入公式或对聚合函数运行进程来编辑表达式。 要执行此操作，请单击&#x200B;**[!UICONTROL Expression]**&#x200B;列字段，然后选择&#x200B;**[!UICONTROL Edit expression]**。

![](assets/query_editor_nveau_97.png)

可以将输出列数据分组：为此，请在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口的&#x200B;**[!UICONTROL Group]**&#x200B;列中选中&#x200B;**[!UICONTROL Yes]**。 此函数围绕检查的分组轴生成结果。 [此部分](../../workflow/using/querying-delivery-information.md)中提供了具有分组的查询示例。

![](assets/query_editor_nveau_56.png)

* **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;函数允许您“按”分组并选择已分组的内容（“有”）。 此函数适用于输出列中的所有字段。 例如，此选项允许您对输出列的所有选项进行分组并恢复特定类型的信息，如35到50之间的收件人。

   如需详细信息，请参阅[此部分](../../workflow/using/querying-using-grouping-management.md)。

* 使用&#x200B;**[!UICONTROL Remove duplicate rows (DISTINCT)]**&#x200B;函数可删除在输出列中获得的相同结果的重复项。 例如，如果通过选择输出列中的姓氏、名字和电子邮件字段进行普查，则将删除具有相同数据的字段，因为这意味着在数据库中已多次输入相同联系人：只考虑一个结果。

## 步骤3 — 对数据排序 {#step-3---sort-data}

使用&#x200B;**[!UICONTROL Sorting]**&#x200B;窗口可以对列内容进行排序。 使用箭头更改列顺序：

* **[!UICONTROL Sorting]**&#x200B;列允许对列内容进行简单排序，并按升序排列从A到Z的列内容。
* **[!UICONTROL Descending sort]**&#x200B;按降序排列内容，从Z到A。 这对于查看记录销售额(例如：最高的数字显示在列表顶部。

在此示例中，数据根据收件人年龄以升序方式排序。

![](assets/query_editor_nveau_57.png)

## 步骤4 — 过滤数据 {#step-4---filter-data}

通过查询编辑器，您可以过滤数据以优化搜索。

提供的过滤器取决于查询所关注的表。

![](assets/query_editor_nveau_09.png)

选择&#x200B;**[!UICONTROL Filtering conditions]**&#x200B;后，将访问&#x200B;**[!UICONTROL Target elements]**&#x200B;部分：这可让您定义如何过滤要收集的数据。

* 要创建新过滤器，请选择创建要验证的公式所需的字段、运算符和值，以便选择要验证的数据。 可以合并多个条件（有关更多信息，请参阅[定义筛选条件](../../platform/using/defining-filter-conditions.md)）。
* 要使用之前保存的过滤器，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以打开下拉列表，单击&#x200B;**[!UICONTROL Predefined filter]**&#x200B;并选择所需的过滤器。

   ![](assets/query_editor_15.png)

* 在&#x200B;**[!UICONTROL Generic query editor]**&#x200B;中创建的过滤器可在其他查询应用程序中使用，反之亦然。 要保存过滤器，请单击&#x200B;**[!UICONTROL Save]**&#x200B;图标。

   >[!NOTE]
   >
   >有关创建和使用过滤器的更多信息，请参阅[过滤选项](../../platform/using/filtering-options.md)。

如以下示例所示，要取回所有讲英语的收件人，请选择：&quot;收件人语言&#x200B;**等于** EN&quot;。

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>通过在&#x200B;**Value**&#x200B;字段中键入以下公式，可直接访问选项：**$(options:OPTION_NAME)**。

单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以查看筛选条件的结果。 在这种情况下，所有讲英语的收件人都会显示其姓名、名字和电子邮件地址。

![](assets/query_editor_nveau_98.png)

熟悉SQL语言的用户可以单击&#x200B;**[!UICONTROL Generate SQL query]**&#x200B;查看SQL中的查询。

![](assets/query_editor_nveau_99.png)

## 步骤5 — 设置数据格式 {#step-5---format-data}

配置限制过滤器后，您将访问&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口。 利用此窗口，可重新排列输出列、转换数据，并更改列标签的大小写。 它还允许您使用计算字段将公式应用到最终结果。

>[!NOTE]
>
>有关计算字段类型的更多信息，请参阅[创建计算字段](../../platform/using/defining-filter-conditions.md#creating-calculated-fields)。

数据预览窗口中不显示未选中的列。

![](assets/query_editor_nveau_10.png)

**[!UICONTROL Transformation]**&#x200B;列允许您将列标签更改为大写或小写。 选择该列，然后单击&#x200B;**[!UICONTROL Transformation]**&#x200B;列中的。 您可以选择：

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 步骤6 — 预览数据 {#step-6---preview-data}

**[!UICONTROL Data preview]**&#x200B;窗口是最后一步。 单击&#x200B;**[!UICONTROL Start the preview of the data]**&#x200B;获取查询结果。 它以列或XML格式提供。 单击&#x200B;**[!UICONTROL Generated SQL queries]**&#x200B;选项卡以查看SQL格式的查询。

在此示例中，数据根据收件人年龄以升序排序。

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>默认情况下，**[!UICONTROL Data preview]**&#x200B;窗口中仅显示前200行。 要更改此设置，请在&#x200B;**[!UICONTROL Lines to display]**&#x200B;框中输入数字，然后单击&#x200B;**[!UICONTROL Start the preview of the data]**。
