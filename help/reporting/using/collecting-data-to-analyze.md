---
title: 收集数据进行分析
seo-title: 收集数据进行分析
description: 收集数据进行分析
seo-description: null
page-status-flag: never-activated
uuid: 5a611786-6e56-4fce-b232-dd8428f3a5f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 594a333d-1fc3-49a0-b3f6-7ea8fa4321e9
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 4%

---


# 收集数据进行分析{#collecting-data-to-analyze}

用于构建报表的数据可以直接在报表页面中选择(有关详细信息，请参 [阅使用上下文](../../reporting/using/using-the-context.md))，或通过一个或多个查询收集。

本活动优惠了三种不同的方法：

1. 使用查询库中的数据构建数据。
1. 处理列表中包含的数据。
1. 使用现有多维数据集中包含的数据。

方法的选择取决于计算类型、数据量及其耐久性等。 必须仔细检查所有这些参数，以避免Adobe Campaign库过载，并优化创建报告的生成和操作。 有关详细信息，请参见[此页面](../../reporting/using/best-practices.md#optimizing-report-creation)。

在所有情况下，都通过类型活动 **[!UICONTROL Query]** 收集数据。

![](assets/reporting_query_edit.png)

当需要使用数据库中的数据收集或构建报告中的数据时，此数据选择模式是相关的。 在某些情况下，您还可以直接从报表中使用的元素中选择数据。 例如，插入图表时，您可以直接选择源数据。 有关此内容的详细信息，请参 [阅使用上下文](../../reporting/using/using-the-context.md)。

## 使用模式中的数据 {#using-the-data-from-a-schema}

要使用链接到模式库的数据，请在查询编辑器中选择相应的选项，并配置要应用的查询。

以下示例允许您收集每个国家／地区的收件人数以及用户档案库中的数。 然后，它们可以以表格形式显示在报告中。

![](assets/reporting_query_from_schema.png)

## 使用导入的列表 {#using-an-imported-list}

要创建报表，您可以使用导入列表中的数据。

为此，请在查询框 **[!UICONTROL Use an imported list]** 中选择选项，然后选择相关列表。

![](assets/reporting_query_from_list.png)

单击链 **[!UICONTROL Edit query...]** 接以定义要在此列表中元素之间收集的数据，以生成报告。

## 使用多维数据集 {#using-a-cube}

可以选择用于定义多维数据集的查询。

![](assets/reporting_query_from_cube.png)

多维数据集使您能够扩展数据库的分析和挖掘能力，同时为最终用户更轻松地配置报表和表：只需选择现有的完全配置多维数据集，并使用其计算、度量和统计。 For more on creating cubes, refer to [this section](../../reporting/using/about-cubes.md).

单击链 **[!UICONTROL Edit query...]** 接，然后选择要在报表中显示或使用的指示器。

![](assets/reporting_query_from_cube_edit_query.png)

## 筛选查询中的选项 {#filtering-options-in-the-queries}

要避免对整个查询库运行，需要过滤数据。

### 简化的滤镜 {#simplified-filter}

您可以选 **[!UICONTROL Filter automatically with the context]** 择选项，使报表可通过树的特定节点(如列表、收件人或投放)访问。

通过 **[!UICONTROL Filter with the folder]** 此选项，可指定文件夹并只考虑其内容。 这样，您可以过滤报告数据，以仅显示树中某个文件夹中的数据，如下所示：

![](assets/reporting_control_folder.png)

### 限制收集的数据量 {#limiting-the-amount-of-data-collected}

使用结果限制选项配置要通过查询提取的记录数：

* **[!UICONTROL Limit to first record]** 提取一个结果，
* **[!UICONTROL Size]** 以提取一组记录。

