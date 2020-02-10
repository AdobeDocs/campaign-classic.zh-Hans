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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 创建查询的步骤{#steps-to-create-a-query}

在Adobe Campaign中构建查询的步骤如下：

1. 选择工作表。 请参阅 [步骤1 —— 选择表](#step-1---choose-a-table)。
1. 选择要提取的数据。 请参阅 [步骤2 —— 选择要提取的数据](#step-2---choose-data-to-extract)。
1. 定义数据排序顺序。 请参阅 [步骤3 —— 对数据排序](#step-3---sort-data)。
1. 过滤数据。 请参阅 [步骤4 —— 过滤数据](#step-4---filter-data)。
1. 格式化数据。 请参阅 [步骤5 —— 格式化数据](#step-5---format-data)。
1. 显示结果。 请参阅 [步骤6 —— 预览数据](#step-6---preview-data)。

>[!NOTE]
>
>所有这些步骤都在通用查询编辑器中可用。 在其他上下文中创建查询时，可能会忽略某些步骤。\
>此部分显示查询 [活动](../../workflow/using/query.md)。

## 第1步——选择表 {#step-1---choose-a-table}

选择包含要在窗口中查询的数据的 **[!UICONTROL Document type]** 表。 如有必要，请使用过滤器字段或按钮过滤数 **[!UICONTROL Filters]** 据。

![](assets/query_editor_nveau_21.png)

## 第2步——选择要提取的数据 {#step-2---choose-data-to-extract}

在窗口 **[!UICONTROL Data to extract]** 中，选择要显示的数据：这些字段将构成输出列。

例如，选择 **[!UICONTROL Age]**、 **[!UICONTROL Primary key]**&#x200B;和 **[!UICONTROL Email domain]****[!UICONTROL City]**。 将根据此选择组织结果。 使用窗口右侧的蓝色箭头更改列顺序。

![](assets/query_editor_nveau_01.png)

可以通过在表达式中插入公式或在聚合函数上运行进程来编辑表达式。 要执行此操作，请单击列 **[!UICONTROL Expression]** 字段，然后选择 **[!UICONTROL Edit expression]**。

![](assets/query_editor_nveau_97.png)

可以将输出列数据分组：为此，请 **[!UICONTROL Yes]** 检查窗 **[!UICONTROL Group]** 口的列 **[!UICONTROL Data to extract]** 中。 此函数围绕检查的分组轴生成一个结果。 本节提供了具有分组的查询 [示例](../../workflow/using/querying-delivery-information.md)。

![](assets/query_editor_nveau_56.png)

* 该函 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 数允许您“分组依据”并选择已分组的内容（“已”）。 此函数适用于输出列中的所有字段。 例如，此选项允许您对输出列的所有选项进行分组，并恢复特定类型的信息，如35到50之间的收件人。

   如需详细信息，请参阅[此部分](../../workflow/using/querying-using-grouping-management.md)。

* 该函 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 数允许您删除在输出列中获得的相同结果。 例如，如果您通过选择输出列中的姓、名和电子邮件字段进行普查，则具有相同数据的字段将被删除，因为这意味着在数据库中输入了多次相同的联系人：只有一个结果会被考虑在内。

## 第3步——对数据排序 {#step-3---sort-data}

通过 **[!UICONTROL Sorting]** 该窗口可以对列内容进行排序。 使用箭头更改列顺序：

* 该列 **[!UICONTROL Sorting]** 支持对列内容进行简单排序，并按从A到Z或升序排列。
* 内容 **[!UICONTROL Descending sort]** 按从Z到A的降序排列。 这对于查看记录销售很有用，例如：最高的数字显示在列表顶部。

在此示例中，数据会根据收件人年龄按升序排序。

![](assets/query_editor_nveau_57.png)

## 第4步——过滤数据 {#step-4---filter-data}

通过查询编辑器，您可以过滤数据以细化搜索。

提供的过滤器取决于查询所关注的表。

![](assets/query_editor_nveau_09.png)

选择该部分 **[!UICONTROL Filtering conditions]** 后，您将访问该 **[!UICONTROL Target elements]** 部分：这允许您定义如何过滤要收集的数据。

* 要创建新筛选器，请选择创建要验证的公式所需的字段、运算符和值，以便选择数据。 可以组合多个条件(有关详细信息，请参阅定义过 [滤器条件](../../platform/using/defining-filter-conditions.md))。
* 要使用以前保存的过滤器，请通过单击按钮打开下拉列 **[!UICONTROL Add]** 表，单击并 **[!UICONTROL Predefined filter]** 选择所需的过滤器。

   ![](assets/query_editor_15.png)

* 在中创建的过滤器可 **[!UICONTROL Generic query editor]** 在其他查询应用程序中使用，反之亦然。 要保存过滤器，请单击该 **[!UICONTROL Save]** 图标。

   >[!NOTE]
   >
   >有关创建和使用过滤器的详细信息，请参阅 [过滤选项](../../platform/using/filtering-options.md)。

如以下示例所示，要恢复所有讲英语的收件人，请选择：“收件人语 **言等于** EN”。

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>您可以通过在“值”字段中键入以下公式直接访问 **选项** : **$(options: OPTION_NAME)**。

单击选 **[!UICONTROL Preview]** 项卡可查看筛选条件的结果。 在这种情况下，所有讲英语的收件人都会显示姓名、名字和电子邮件地址。

![](assets/query_editor_nveau_98.png)

熟悉SQL语言的用户可以单 **[!UICONTROL Generate SQL query]** 击以在SQL中查看查询。

![](assets/query_editor_nveau_99.png)

## 第5步——设置数据格式 {#step-5---format-data}

配置限制过滤器后，您将访问该窗 **[!UICONTROL Data formatting]** 口。 通过此窗口可以重新排列输出列、转换数据并更改列标签的上／下大小写。 它还允许您使用计算字段将公式应用于最终结果。

>[!NOTE]
>
>有关计算字段类型的详细信息，请参阅创 [建计算字段](../../platform/using/defining-filter-conditions.md#creating-calculated-fields)。

数据预览窗口中不显示未选中的列。

![](assets/query_editor_nveau_10.png)

列 **[!UICONTROL Transformation]** 允许您将列标签更改为大写或小写。 选择列，然后在列中单 **[!UICONTROL Transformation]** 击。 您可以选择：

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 第6步——预览数据 {#step-6---preview-data}

窗 **[!UICONTROL Data preview]** 口是最后一步。 单击 **[!UICONTROL Start the preview of the data]** 可获取查询结果。 它以列或XML格式提供。 单击选 **[!UICONTROL Generated SQL queries]** 项卡以查看SQL格式的查询。

在此示例中，数据根据收件人年龄按升序排序。

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>默认情况下，窗口中仅显示前200行 **[!UICONTROL Data preview]** 。 要更改此设置，请在框中输入一个 **[!UICONTROL Lines to display]** 数字，然后单击 **[!UICONTROL Start the preview of the data]**。

