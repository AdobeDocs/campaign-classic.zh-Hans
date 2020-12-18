---
solution: Campaign Classic
product: campaign
title: 收集数据进行分析
description: 收集数据进行分析
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 3%

---


# 收集数据进行分析{#collecting-data-to-analyze}

用于构建报表的数据可以直接在报表页面中进行选择（有关详细信息，请参阅[使用上下文](../../reporting/using/using-the-context.md)），或通过一个或多个查询进行收集。

本活动优惠了三种不同的方法：

1. 使用查询库中的数据构建数据。
1. 处理列表中包含的数据。
1. 使用现有多维数据集中包含的数据。

方法的选择取决于计算类型、数据量及其耐久性等。 必须仔细检查所有这些参数，以避免Adobe Campaign库过载，并优化创建报告的生成和操作。 有关详细信息，请参见[此页面](../../reporting/using/best-practices.md#optimizing-report-creation)。

在所有情况下，都通过&#x200B;**[!UICONTROL Query]**&#x200B;类型活动收集数据。

![](assets/reporting_query_edit.png)

当需要使用数据库中的数据收集或构建报告中的数据时，此数据选择模式是相关的。 在某些情况下，您还可以直接从报表中使用的元素中选择数据。 例如，插入图表时，您可以直接选择源数据。 有关详细信息，请参阅[使用上下文](../../reporting/using/using-the-context.md)。

## 使用模式{#using-the-data-from-a-schema}中的数据

要使用链接到模式库的数据，请在查询编辑器中选择相应的选项，并配置要应用的查询。

以下示例允许您收集每个国家／地区的收件人数以及用户档案库中的数。 然后，它们可以以表格形式显示在报告中。

![](assets/reporting_query_from_schema.png)

## 使用导入的列表{#using-an-imported-list}

要创建报表，您可以使用导入列表中的数据。

为此，请在查询框中选择&#x200B;**[!UICONTROL Use an imported list]**&#x200B;选项，然后选择相关列表。

![](assets/reporting_query_from_list.png)

单击&#x200B;**[!UICONTROL Edit query...]**&#x200B;链接以定义要在此列表中收集的数据，以生成报告。

## 使用多维数据集{#using-a-cube}

可以选择用于定义多维数据集的查询。

![](assets/reporting_query_from_cube.png)

多维数据集使您能够扩展数据库的分析和挖掘能力，同时为最终用户更轻松地配置报表和表：只需选择现有的完全配置多维数据集，并使用其计算、度量和统计。 有关创建多维数据集的详细信息，请参阅[此部分](../../reporting/using/about-cubes.md)。

单击&#x200B;**[!UICONTROL Edit query...]**&#x200B;链接，然后选择要在报告中显示或使用的指示器。

![](assets/reporting_query_from_cube_edit_query.png)

## 筛选查询{#filtering-options-in-the-queries}中的选项

要避免对整个查询库运行，需要过滤数据。

### 简化的过滤器{#simplified-filter}

您可以选择&#x200B;**[!UICONTROL Filter automatically with the context]**&#x200B;选项，使报表可通过树的特定节点(如列表、收件人或投放)访问。

使用&#x200B;**[!UICONTROL Filter with the folder]**&#x200B;选项可指定文件夹并只考虑其内容。 这样，您可以过滤报告数据，以仅显示树中某个文件夹中的数据，如下所示：

![](assets/reporting_control_folder.png)

### 限制收集的数据量{#limiting-the-amount-of-data-collected}

使用结果限制选项配置要通过查询提取的记录数：

* **[!UICONTROL Limit to first record]** 提取一个结果，
* **[!UICONTROL Size]** 以提取一组记录。

