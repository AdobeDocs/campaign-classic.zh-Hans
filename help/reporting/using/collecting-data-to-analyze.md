---
title: 收集数据以进行分析
seo-title: 收集数据以进行分析
description: 收集数据以进行分析
seo-description: null
page-status-flag: never-activated
uuid: 5a611786-6e56-4fce-b232-dd8428f3a5f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 594a333d-1fc3-49a0-b3f6-7ea8fa4321e9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# 收集数据以进行分析{#collecting-data-to-analyze}

用于构建报表的数据可以直接在报表页面中选择(有关详细信息，请参阅 [Using the context](../../reporting/using/using-the-context.md))，或通过一个或多个查询收集。

此活动提供三种不同的方法：

1. 使用数据库中的数据构建查询。
1. 处理列表中包含的数据。
1. 使用包含在现有立方中的数据。

方法的选择取决于计算类型、数据量及其耐久性等。 必须仔细检查所有这些参数，以避免Adobe Campaign数据库过载，并优化创建报告的生成和操作。 有关详细信息，请参见[此页面](../../reporting/using/best-practices.md#optimizing-report-creation)。

在所有情况下，都会通过类型活动收 **[!UICONTROL Query]** 集数据。

![](assets/reporting_query_edit.png)

当需要使用数据库中的数据收集或构建报告中的数据时，此数据选择模式是相关的。 在某些情况下，您还可以直接从报告中使用的元素中选择数据。 例如，插入图表时，您可以直接选择源数据。 有关此内容的详细信息，请参 [阅使用上下文](../../reporting/using/using-the-context.md)。

## 使用架构中的数据 {#using-the-data-from-a-schema}

要使用链接到数据库架构的数据，请在查询编辑器中选择相应的选项，并配置要应用的查询。

以下示例允许您在数据库中的配置文件中收集每个国家／地区的收件人数。 然后，它们可以以表格形式显示在报告中。

![](assets/reporting_query_from_schema.png)

## 使用导入的列表 {#using-an-imported-list}

要创建报告，您可以使用导入数据列表中的数据。

为此，请在查询框 **[!UICONTROL Use an imported list]** 中选择选项，然后选择相关列表。

![](assets/reporting_query_from_list.png)

单击链 **[!UICONTROL Edit query...]** 接以定义要在此列表中收集的数据，以便生成报告。

## 使用立方 {#using-a-cube}

可以选择用于定义查询的立方。

![](assets/reporting_query_from_cube.png)

使用多维数据集，您可以扩展数据库的探索和分析能力，同时更轻松地为最终用户配置报告和表：只需选择一个现有的完全配置的立方，然后使用其计算、度量和统计信息。 For more on creating cubes, refer to [this section](../../reporting/using/about-cubes.md).

单击链 **[!UICONTROL Edit query...]** 接，然后选择要在报表中显示或使用的指示器。

![](assets/reporting_query_from_cube_edit_query.png)

## 筛选查询中的选项 {#filtering-options-in-the-queries}

为避免对整个数据库运行查询，需要过滤数据。

### 简化的滤镜 {#simplified-filter}

您可以选择 **[!UICONTROL Filter automatically with the context]** 此选项，以通过树的特定节点（如列表、收件人或分发）访问报表。

通过 **[!UICONTROL Filter with the folder]** 此选项可指定文件夹并仅考虑其内容。 这样，您就可以过滤报告数据，以仅显示树中某个文件夹的数据，如下所示：

![](assets/reporting_control_folder.png)

### 限制收集的数据量 {#limiting-the-amount-of-data-collected}

使用结果限制选项配置要通过查询提取的记录数：

* **[!UICONTROL Limit to first record]** 提取一个结果，
* **[!UICONTROL Size]** 以提取一组记录。

