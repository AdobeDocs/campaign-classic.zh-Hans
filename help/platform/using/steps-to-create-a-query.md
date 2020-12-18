---
solution: Campaign Classic
product: campaign
title: 创建查询的步骤
description: 创建查询的步骤
audience: platform
content-type: reference
topic-tags: creating-queries
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---


# 创建查询的步骤{#steps-to-create-a-query}

在Adobe Campaign中构建查询的步骤如下：

1. 选择工作表。 请参阅[步骤1 —— 选择表](#step-1---choose-a-table)。
1. 选择要提取的数据。 请参阅[步骤2 —— 选择要提取的数据](#step-2---choose-data-to-extract)。
1. 定义数据排序顺序。 请参阅[步骤3 —— 对数据排序](#step-3---sort-data)。
1. 筛选数据。 请参阅[步骤4 —— 筛选数据](#step-4---filter-data)。
1. 格式化数据。 请参阅[步骤5 —— 格式化数据](#step-5---format-data)。
1. 显示结果。 请参阅[步骤6 -预览数据](#step-6---preview-data)。

>[!NOTE]
>
>所有这些步骤均在通用查询编辑器中可用。 在其他上下文中创建查询时，可能会忽略一些步骤。\
>查询活动显示在[此部分](../../workflow/using/query.md)中。

## 步骤1 —— 选择表{#step-1---choose-a-table}

在&#x200B;**[!UICONTROL Document type]**&#x200B;窗口中选择包含要查询的数据的表。 如有必要，请使用过滤器字段或&#x200B;**[!UICONTROL Filters]**&#x200B;按钮过滤数据。

![](assets/query_editor_nveau_21.png)

## 第2步——选择要提取{#step-2---choose-data-to-extract}的数据

在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，选择要显示的数据：这些字段将构成输出列。

例如，选择&#x200B;**[!UICONTROL Age]**、**[!UICONTROL Primary key]**、**[!UICONTROL Email domain]**&#x200B;和&#x200B;**[!UICONTROL City]**。 将根据此选择组织结果。 使用窗口右侧的蓝色箭头更改列顺序。

![](assets/query_editor_nveau_01.png)

可以通过在表达式中插入公式或对聚合函数运行进程来编辑。 为此，单击&#x200B;**[!UICONTROL Expression]**&#x200B;列字段，然后选择&#x200B;**[!UICONTROL Edit expression]**。

![](assets/query_editor_nveau_97.png)

可以对输出列数据进行分组：为此，请检查&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口的&#x200B;**[!UICONTROL Group]**&#x200B;列中的&#x200B;**[!UICONTROL Yes]**。 此函数围绕检查的分组轴生成结果。 [此部分](../../workflow/using/querying-delivery-information.md)中提供了具有分组的查询的示例。

![](assets/query_editor_nveau_56.png)

* **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;函数允许您“分组依据”并选择已分组的内容（“有”）。 此函数适用于输出列中的所有字段。 例如，通过此选项，您可以对输出列的所有选项进行分组，并恢复特定类型的信息，如35到50之间的收件人。

   如需详细信息，请参阅[此部分](../../workflow/using/querying-using-grouping-management.md)。

* 使用&#x200B;**[!UICONTROL Remove duplicate rows (DISTINCT)]**&#x200B;函数可以删除在输出列中获得的相同结果。 例如，如果通过在输出列中选择姓氏、名字和电子邮件字段进行人口普查，则具有相同数据的字段将被删除，因为这意味着在数据库中输入了多次相同的联系人：只考虑一个结果。

## 步骤3 —— 对数据{#step-3---sort-data}排序

在&#x200B;**[!UICONTROL Sorting]**&#x200B;窗口中，可以对列内容进行排序。 使用箭头更改列顺序：

* **[!UICONTROL Sorting]**&#x200B;列启用简单排序，并按升序排列列内容（从A到Z）。
* **[!UICONTROL Descending sort]**&#x200B;按降序排列内容，从Z到A。 这对于查看记录销售情况(例如：最高的数字显示在列表的顶部。

在此示例中，数据根据收件人年龄按升序排序。

![](assets/query_editor_nveau_57.png)

## 第4步——筛选数据{#step-4---filter-data}

查询编辑器允许您过滤数据以细化搜索。

提供的过滤器取决于查询所关心的表格。

![](assets/query_editor_nveau_09.png)

选择&#x200B;**[!UICONTROL Filtering conditions]**&#x200B;后，您将访问&#x200B;**[!UICONTROL Target elements]**&#x200B;部分：这允许您定义如何过滤要收集的数据。

* 要创建新筛选器，请选择创建要验证的公式所需的字段、运算符和值，以便选择数据。 可以组合多个条件（有关详细信息，请参阅[定义过滤条件](../../platform/using/defining-filter-conditions.md)）。
* 要使用以前保存的过滤器，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮打开下拉列表，单击&#x200B;**[!UICONTROL Predefined filter]**&#x200B;并选择所需的。

   ![](assets/query_editor_15.png)

* 在&#x200B;**[!UICONTROL Generic query editor]**&#x200B;中创建的过滤器在其他查询应用程序中可用，反之亦然。 要保存过滤器，请单击&#x200B;**[!UICONTROL Save]**&#x200B;图标。

   >[!NOTE]
   >
   >有关创建和使用过滤器的详细信息，请参阅[筛选选项](../../platform/using/filtering-options.md)。

如以下示例所示，要恢复所有讲英语的收件人，请选择：&quot;收件人语言&#x200B;**等于** EN&quot;。

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>您可以在&#x200B;**Value**&#x200B;字段中键入以下公式直接访问某个选项：**$(options:OPTION_NAME)**。

单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以视图过滤条件的结果。 在这种情况下，所有讲英语的收件人都会显示其姓名、名字和电子邮件地址。

![](assets/query_editor_nveau_98.png)

熟悉SQL语言的用户可以单击&#x200B;**[!UICONTROL Generate SQL query]**&#x200B;视图SQL中的查询。

![](assets/query_editor_nveau_99.png)

## 步骤5 —— 格式化数据{#step-5---format-data}

配置限制过滤器后，您将访问&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口。 通过此窗口可以重新排列输出列、转换数据并更改列标签的上／下大小写。 它还允许您使用计算字段将公式应用于最终结果。

>[!NOTE]
>
>有关计算字段类型的详细信息，请参阅[创建计算字段](../../platform/using/defining-filter-conditions.md#creating-calculated-fields)。

未选中的列将不会显示在数据预览窗口中。

![](assets/query_editor_nveau_10.png)

使用&#x200B;**[!UICONTROL Transformation]**&#x200B;列可将列标签更改为大写或小写。 选择该列并单击&#x200B;**[!UICONTROL Transformation]**&#x200B;列。 您可以选择：

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 步骤6 -预览数据{#step-6---preview-data}

**[!UICONTROL Data preview]**&#x200B;窗口是最后一个阶段。 单击&#x200B;**[!UICONTROL Start the preview of the data]**&#x200B;获取查询结果。 它以列或XML格式提供。 单击&#x200B;**[!UICONTROL Generated SQL queries]**&#x200B;选项卡以视图SQL格式的查询。

在此示例中，数据根据收件人年龄按升序排序。

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>默认情况下，**[!UICONTROL Data preview]**&#x200B;窗口中只显示前200行。 要更改此设置，请在&#x200B;**[!UICONTROL Lines to display]**&#x200B;框中输入数字，然后单击&#x200B;**[!UICONTROL Start the preview of the data]**。

