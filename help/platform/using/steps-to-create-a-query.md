---
title: 创建查询的步骤
seo-title: 创建查询的步骤
description: 创建查询的步骤
seo-description: null
page-status-flag: never-activated
uuid: 9668f49c-2da7-42c8-8728-8d644c787935
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: d538f489-f1ae-4682-9c21-d0300bd42b26
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 3%

---


# 创建查询的步骤{#steps-to-create-a-query}

在Adobe Campaign中构建查询的步骤如下：

1. 选择工作表。 请参阅 [步骤1 —— 选择表](#step-1---choose-a-table)。
1. 选择要提取的数据。 请参阅 [步骤2 —— 选择要提取的数据](#step-2---choose-data-to-extract)。
1. 定义数据排序顺序。 请参阅 [步骤3 —— 对数据排序](#step-3---sort-data)。
1. 筛选数据。 请参阅 [步骤4 —— 筛选数据](#step-4---filter-data)。
1. 格式化数据。 请参阅 [步骤5 —— 格式化数据](#step-5---format-data)。
1. 显示结果。 请参阅 [步骤6 -预览数据](#step-6---preview-data)。

>[!NOTE]
>
>所有这些步骤均在通用查询编辑器中可用。 在其他上下文中创建查询时，可能会忽略一些步骤。\
>查询活动显示在 [本节中](../../workflow/using/query.md)。

## 第1步——选择表 {#step-1---choose-a-table}

选择包含要在窗口中查询的数据的 **[!UICONTROL Document type]** 表。 如有必要，请使用过滤器字段或按钮过滤 **[!UICONTROL Filters]** 数据。

![](assets/query_editor_nveau_21.png)

## 第2步——选择要提取的数据 {#step-2---choose-data-to-extract}

在窗口 **[!UICONTROL Data to extract]** 中，选择要显示的数据：这些字段将构成输出列。

例如，选 **[!UICONTROL Age]**&#x200B;择 **[!UICONTROL Primary key]**、 **[!UICONTROL Email domain]** 和 **[!UICONTROL City]**。 将根据此选择组织结果。 使用窗口右侧的蓝色箭头更改列顺序。

![](assets/query_editor_nveau_01.png)

可以通过在表达式中插入公式或对聚合函数运行进程来编辑。 为此，请单击列 **[!UICONTROL Expression]** 字段，然后选择 **[!UICONTROL Edit expression]**。

![](assets/query_editor_nveau_97.png)

可以对输出列数据进行分组：要执行此操作， **[!UICONTROL Yes]** 请检查 **[!UICONTROL Group]** 窗口的列 **[!UICONTROL Data to extract]** 中。 此函数围绕检查的分组轴生成结果。 本节提供了具有分组的查询 [的示例](../../workflow/using/querying-delivery-information.md)。

![](assets/query_editor_nveau_56.png)

* 函 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 数允许您“分组依据”并选择已分组的内容（“已分组”）。 此函数适用于输出列中的所有字段。 例如，通过此选项，您可以对输出列的所有选项进行分组，并恢复特定类型的信息，如35到50之间的收件人。

   如需详细信息，请参阅[此部分](../../workflow/using/querying-using-grouping-management.md)。

* 该函 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 数允许您删除在输出列中获得的相同结果。 例如，如果通过在输出列中选择姓氏、名字和电子邮件字段进行人口普查，则具有相同数据的字段将被删除，因为这意味着在数据库中输入了多次相同的联系人：只考虑一个结果。

## 第3步——对数据排序 {#step-3---sort-data}

在窗 **[!UICONTROL Sorting]** 口中，可以对列内容进行排序。 使用箭头更改列顺序：

* 该列 **[!UICONTROL Sorting]** 支持对列内容进行简单排序，并按从A到Z或升序排列。
* 内 **[!UICONTROL Descending sort]** 容按降序从Z排列到A。 这对于查看记录销售情况(例如：最高的数字显示在列表的顶部。

在此示例中，数据根据收件人年龄按升序排序。

![](assets/query_editor_nveau_57.png)

## 第4步——筛选数据 {#step-4---filter-data}

查询编辑器允许您过滤数据以细化搜索。

提供的过滤器取决于查询所关心的表格。

![](assets/query_editor_nveau_09.png)

选择该部分 **[!UICONTROL Filtering conditions]** 后，您将访问 **[!UICONTROL Target elements]** 该部分：这允许您定义如何过滤要收集的数据。

* 要创建新筛选器，请选择创建要验证的公式所需的字段、运算符和值，以便选择数据。 可以组合多个条件(有关详细信息，请参阅定义 [筛选条件](../../platform/using/defining-filter-conditions.md))。
* 要使用以前保存的过滤器，请通过单击按钮打开下拉 **[!UICONTROL Add]** 列表，单 **[!UICONTROL Predefined filter]** 击并选择所需的。

   ![](assets/query_editor_15.png)

* 在中创建的过滤器可 **[!UICONTROL Generic query editor]** 在其他查询应用程序中使用，反之亦然。 要保存过滤器，请单击 **[!UICONTROL Save]** 图标。

   >[!NOTE]
   >
   >有关创建和使用过滤器的详细信息，请参 [阅筛选选项](../../platform/using/filtering-options.md)。

如以下示例所示，要恢复所有讲英语的收件人，请选择：“收件人语 **等于** EN”。

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>您可以通过在“值”字段中键入以下公式直接访问 **某个选** 项： **$(options:OPTION_NAME)**。

单击选 **[!UICONTROL Preview]** 项卡以视图筛选条件的结果。 在这种情况下，所有讲英语的收件人都会显示其姓名、名字和电子邮件地址。

![](assets/query_editor_nveau_98.png)

熟悉SQL语言的用户可以单 **[!UICONTROL Generate SQL query]** 击以视图SQL中的查询。

![](assets/query_editor_nveau_99.png)

## 第5步——格式化数据 {#step-5---format-data}

配置限制过滤器后，您将访问该窗 **[!UICONTROL Data formatting]** 口。 通过此窗口可以重新排列输出列、转换数据并更改列标签的上／下大小写。 它还允许您使用计算字段将公式应用于最终结果。

>[!NOTE]
>
>有关计算字段类型的详细信息，请参阅创 [建计算字段](../../platform/using/defining-filter-conditions.md#creating-calculated-fields)。

未选中的列将不会显示在数据预览窗口中。

![](assets/query_editor_nveau_10.png)

列 **[!UICONTROL Transformation]** 允许您将列标签更改为大写或小写。 选择列，然后在列中单 **[!UICONTROL Transformation]** 击。 您可以选择：

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 第6步-预览数据 {#step-6---preview-data}

窗 **[!UICONTROL Data preview]** 口是最后一步。 单 **[!UICONTROL Start the preview of the data]** 击获取查询结果。 它以列或XML格式提供。 单击选 **[!UICONTROL Generated SQL queries]** 项卡以视图SQL格式的查询。

在此示例中，数据根据收件人年龄按升序排序。

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>默认情况下，窗口中仅显示前200行 **[!UICONTROL Data preview]** 内容。 要更改此项，请在框中输入 **[!UICONTROL Lines to display]** 数字并单击 **[!UICONTROL Start the preview of the data]**。

