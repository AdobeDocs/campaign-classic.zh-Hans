---
product: campaign
title: 收集数据进行分析
description: 收集数据进行分析
badge: label="v7" type="信息性" tooltip="仅适用于Campaign Classicv7"
feature: Reporting
exl-id: cf621374-88f9-4def-8bea-87e0ea69ecd3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 3%

---

# 收集数据进行分析{#collecting-data-to-analyze}



可直接在报表页面中选择用于生成报表的数据(有关更多信息，请参阅 [使用上下文](../../reporting/using/using-the-context.md))，或通过一个或多个查询收集而得。

此活动提供三种不同的方法：

1. 使用数据库中的数据构建查询。
1. 处理列表中包含的数据。
1. 使用现有多维数据集中包含的数据。

方法的选择取决于计算类型、数据量及其耐久性等。 必须仔细检查所有这些参数，以避免Adobe Campaign数据库过载并优化所创建报告的生成和操作。 有关详细信息，请参见[此页面](../../reporting/using/best-practices.md#optimizing-report-creation)。

在所有情况下，数据都是通过 **[!UICONTROL Query]** 键入activity。

![](assets/reporting_query_edit.png)

当需要使用数据库中的数据来收集或构建报表中的数据时，此数据选择模式是相关的。 在某些情况下，您还可以直接从报告中使用的元素中选择数据。 例如，在插入图表时，您可以直接选择源数据。 有关更多信息，请参阅 [使用上下文](../../reporting/using/using-the-context.md).

## 使用来自架构的数据 {#using-the-data-from-a-schema}

要使用链接到数据库模式的数据，请在查询编辑器中选择适当的选项，并配置要应用的查询。

以下示例允许您在数据库中的用户档案中收集每个国家/地区的收件人数量。 然后，它们可以表格形式显示在报表中。

![](assets/reporting_query_from_schema.png)

## 使用导入的列表 {#using-an-imported-list}

要创建报表，您可以使用导入数据列表中的数据。

要执行此操作，请选择 **[!UICONTROL Use an imported list]** 选项，然后选择相关列表。

![](assets/reporting_query_from_list.png)

单击 **[!UICONTROL Edit query...]** 此链接用于定义要在此列表中的元素中收集的数据以生成报告。

## 使用多维数据集 {#using-a-cube}

可以选择用于定义查询的多维数据集。

![](assets/reporting_query_from_cube.png)

多维数据集使您能够扩展数据库的探索和分析能力，同时使最终用户更容易配置报告和表：只需选择已完全配置的现有多维数据集，并使用其计算、度量和统计信息。 有关创建多维数据集的更多信息，请参阅 [本节](../../reporting/using/ac-cubes.md).

单击 **[!UICONTROL Edit query...]** 链接并选择要在报告中显示或使用的指标。

![](assets/reporting_query_from_cube_edit_query.png)

## 筛选查询中的选项 {#filtering-options-in-the-queries}

为了避免在整个数据库上运行查询，需要筛选数据。

### 简化的筛选器 {#simplified-filter}

您可以选择 **[!UICONTROL Filter automatically with the context]** 用于通过树的特定节点（如列表、收件人或投放）访问报告的选项。

此 **[!UICONTROL Filter with the folder]** 选项允许您指定文件夹，并仅考虑其内容。 这样，您就可以筛选报表数据，以仅显示树中某个文件夹的数据，如下所示：

![](assets/reporting_control_folder.png)

### 限制收集的数据量 {#limiting-the-amount-of-data-collected}

使用结果限制选项配置要通过查询提取的记录数：

* **[!UICONTROL Limit to first record]** 要提取一个结果，
* **[!UICONTROL Size]** 以提取一组记录。
