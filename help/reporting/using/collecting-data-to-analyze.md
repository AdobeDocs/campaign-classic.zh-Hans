---
product: campaign
title: 收集数据进行分析
description: 收集数据进行分析
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
exl-id: cf621374-88f9-4def-8bea-87e0ea69ecd3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 5%

---

# 收集数据进行分析{#collecting-data-to-analyze}



可以直接在报告页面中选择用于生成报告的数据（有关更多信息，请参阅[使用上下文](../../reporting/using/using-the-context.md)），或通过一个或多个查询收集这些数据。

本活动提供了三种不同的方法：

1. 使用数据库中的数据构建查询。
1. 处理列表中包含的数据。
1. 使用现有多维数据集中包含的数据。

方法的选择取决于计算类型、数据量及其耐久性等。 必须仔细检查所有这些参数，以避免Adobe Campaign数据库过载并优化所创建报告的生成和操作。 有关详细信息，请参见[此页面](../../reporting/using/best-practices.md#optimizing-report-creation)。

在所有情况下，都是通过&#x200B;**[!UICONTROL Query]**&#x200B;类型活动收集数据。

![](assets/reporting_query_edit.png)

当需要使用数据库中的数据来收集或构建报表中的数据时，此数据选择模式相关。 在某些情况下，您还可以直接从报表中使用的元素中选择数据。 例如，在插入图表时，您可以直接选择源数据。 有关详细信息，请参阅[使用上下文](../../reporting/using/using-the-context.md)。

## 使用来自架构的数据 {#using-the-data-from-a-schema}

要使用链接到数据库模式的数据，请在查询编辑器中选择适当的选项，并配置要应用的查询。

以下示例允许您在数据库中的用户档案中收集每个国家/地区的收件人数量。 然后，它们能够以表格的形式显示在报表中。

![](assets/reporting_query_from_schema.png)

## 使用导入的列表 {#using-an-imported-list}

要创建报表，您可以使用导入数据列表中的数据。

为此，请在查询框中选择&#x200B;**[!UICONTROL Use an imported list]**&#x200B;选项，然后选择相关列表。

![](assets/reporting_query_from_list.png)

单击&#x200B;**[!UICONTROL Edit query...]**&#x200B;链接可定义此列表中元素间要收集的数据以生成报告。

## 使用多维数据集 {#using-a-cube}

可以选择用于定义查询的多维数据集。

![](assets/reporting_query_from_cube.png)

多维数据集使您可以扩展数据库的探索和分析能力，同时更轻松地为最终用户配置报告和表：只需选择已完全配置的现有多维数据集，并使用其计算、度量和统计信息。 有关创建多维数据集的更多信息，请参阅[此章节](../../reporting/using/ac-cubes.md)。

单击&#x200B;**[!UICONTROL Edit query...]**&#x200B;链接，然后选择要显示在报表中或要在报表中使用的指示器。

![](assets/reporting_query_from_cube_edit_query.png)

## 筛选查询中的选项 {#filtering-options-in-the-queries}

为了避免在整个数据库上运行查询，需要过滤数据。

### 简化的过滤器 {#simplified-filter}

您可以选择&#x200B;**[!UICONTROL Filter automatically with the context]**&#x200B;选项，以使报表可通过树的特定节点（如列表、收件人或投放）访问。

**[!UICONTROL Filter with the folder]**&#x200B;选项允许您指定文件夹并仅考虑其内容。 这样，您就可以筛选报表数据，以仅显示树中某个文件夹的数据，如下所示：

![](assets/reporting_control_folder.png)

### 限制收集的数据量 {#limiting-the-amount-of-data-collected}

使用结果限制选项配置要通过查询提取的记录数：

* **[!UICONTROL Limit to first record]**&#x200B;以提取一个结果，
* **[!UICONTROL Size]**&#x200B;以提取设置的记录数。
