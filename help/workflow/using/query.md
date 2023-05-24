---
product: campaign
title: 查询
description: 了解有关查询工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity, Query Editor
exl-id: 20d03627-cd56-46da-bc02-73b48a02a350
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1629'
ht-degree: 1%

---

# 查询{#query}



## 创建查询 {#creating-a-query}

通过查询，可根据条件选择目标。 您可以将区段代码与查询结果关联起来并在其中插入其他数据。
有关查询示例的详细信息，请参阅此 [本节](querying-recipient-table.md).

>[!NOTE]
>
>使用Oracle时，查询活动与CLOB字段不兼容。

![](assets/s_user_segmentation_wizard_9.png)

有关使用和管理附加数据的更多信息，请参阅 [添加数据](#adding-data).

此 **[!UICONTROL Edit query...]** 链接允许您通过以下方式定义群体的定位类型、限制和选择标准：

1. 选择定位和筛选维度。 默认情况下，将从收件人中选择目标。 限制筛选器的列表与用于投放定位的筛选器相同。

   定向维度与我们将处理的元素类型（例如，操作定向的群体）一致。

   利用筛选维度，可收集这些元素，例如与目标人员（合同、全部和最终结算等）相关的信息。

   有关更多信息，请参阅 [定位和筛选维度](building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   查询可以基于集客过渡的数据，如有必要，可通过选择 **[!UICONTROL Temporary schema]** 选择定位和筛选维度时。

   ![](assets/query_temporary_table.png)

1. 使用向导定义群体。 要输入的字段可以因目标类型而异。 您可以使用以下方法预览符合您当前条件的目标群体 **[!UICONTROL Preview]** 选项卡。

   有关创建和使用过滤器或查询的更多信息，请参阅此 [部分](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. 如果已选择 **[!UICONTROL Filtering conditions]** 在第1步中或使用 **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]** 选项，之后您将必须手动添加筛选条件。

   您还可以通过选中相应的框来添加数据分组条件。 要实现此目的，筛选维度必须与查询的定向维度不同。 有关分组的详细信息，请参阅此 [部分](querying-using-grouping-management.md).

   您也可以使用表达式生成器并将它与逻辑选项AND、OR和EXCEPT组合在一起，以添加更多标准。 然后，您可以预览 **[!UICONTROL Corresponding SQL query...]** （对于您的标准组合）。 有关详细信息，请参阅此 [部分](../../platform/using/defining-filter-conditions.md#building-expressions).

   如果您希望稍后重复使用过滤器，请保存该过滤器。

   ![](assets/s_user_segmentation_query_advanced.png)

## 添加数据 {#adding-data}

通过附加列，可收集有关目标群体的其他信息，例如合同编号、新闻稿订阅或来源。 此数据可以存储在Adobe Campaign数据库或外部数据库中。

此 **[!UICONTROL Add data...]** 链接允许您选择要收集的其他数据。

![](assets/wf_add_data_link.png)

首先，选择要添加的数据类型：

![](assets/wf_add_data_1st_option.png)

* 选择 **[!UICONTROL Data linked to the filtering dimension]** 以选择Adobe Campaign数据库中的数据。
* 选择 **[!UICONTROL External data]** 从外部数据库添加数据。 此选项仅当您购买了 **联合数据访问** 选项。 有关更多信息，请参阅 [访问外部数据库（联合数据访问）](accessing-an-external-database--fda-.md).
* 选择 **[!UICONTROL An offer proposition]** 用于添加一组列的选项，这些列允许您存储优惠引擎生成的最佳建议。 此选项仅当您购买了 **互动** 模块。

如果平台上未安装可选模块，则不会显示此阶段。 你将被直接带到下一个阶段。

要从Adobe Campaign数据库添加数据，请执行以下操作：

1. 选择要添加的数据类型。 这可以是属于筛选维度的数据，也可以是存储在链接表中的数据。

   ![](assets/query_add_columns.png)

1. 如果数据属于查询的筛选维度，则只需在可用字段列表中选择该数据，即可在输出列中显示该数据。

   ![](assets/wf_add_data_field_selection.png)

   您可以添加：

   * 根据从目标群体或聚合（上个月内待定购买的次数、收据的平均金额等）获取的数据计算的字段。 例如，转到 [选择数据](targeting-data.md#selecting-data).
   * 使用创建的新字段 **[!UICONTROL Add]** 按钮以将其添加到输出列列表的右侧。

      您还可以添加一系列信息，例如合同列表、最近5次投放等。 收藏集与相同用户档案可以具有多个值的字段一致（1-N关系）。 有关更多信息，请参阅 [编辑其他数据](targeting-data.md#editing-additional-data).

要添加链接到目标群体的信息集合，请执行以下操作：

1. 在向导的第一步，选择 **[!UICONTROL Data linked to the filtering dimension]** 选项：
1. 选择包含要收集信息的表，然后单击 **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. 如有必要，通过选择以下值之一，指定要保留的集合的元素数： **[!UICONTROL Data collected]** 字段。 默认情况下，将恢复集合的所有行，然后根据在后续步骤中指定的条件进行筛选。

   * 如果收藏集的单个元素与此收藏集的筛选条件一致，请选择 **[!UICONTROL Single row]** 在 **[!UICONTROL Data collected]** 字段。

      >[!IMPORTANT]
      >
      >此模式会优化由于集合元素上的直接连接而生成的SQL查询。
      >
      >如果不满足初始条件，则结果可能有缺陷（缺少线或线重叠）。

   * 如果选择恢复多行(**[!UICONTROL Limit the line count]**)您可以指定要收集的行数。
   * 如果收集的列包含聚合，例如声明的失败次数、网站上的平均支出等。 您可以使用 **[!UICONTROL Aggregates]** 值。

   ![](assets/query_add_collection_param.png)

1. 指定集合的子选择。 例如：仅过去15天的购买量。

   ![](assets/query_add_columns_collection_filter.png)

1. 如果您已选择 **[!UICONTROL Limit the line count]** 选项，定义收集的数据的过滤顺序。 一旦收集的行数超过您指定的要保留的行数，筛选顺序允许您指定要保留的行。

## 示例：基于简单收件人属性定向 {#example--targeting-on-simple-recipient-attributes}

在以下示例中，查询试图识别居住在法国的18至30岁男子。 例如，此查询将用于旨在使其成为独占选件的工作流中。

>[!NOTE]
>
>中提供了其他查询示例 [本节](querying-recipient-table.md).

1. 命名您的查询，然后选择 **[!UICONTROL Edit query...]** 链接。
1. 选择 **[!UICONTROL Filtering conditions]** 在可用的过滤器类型列表中。
1. 为建议的目标输入不同的标准。 此处使用AND选项组合标准。 要包含在选择中，收件人必须满足以下四个条件：

   * 标题为“先生”的收件人（也可以使用找到） **性别** 字段和选择 **男性** 作为值)。
   * 年龄在30岁以下的收件人。
   * 18岁以上的收件人。
   * 居住在法国的收件人。

   ![](assets/query_example.png)

   可以查看与您的条件组合匹配的SQL：

   ![](assets/query_example_sql.png)

1. 您可以通过预览在相关选项卡中与查询匹配的收件人，来检查标准是否正确：

   ![](assets/query_example_preview.png)

1. 保存您的过滤器，以便您以后可以通过单击 **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. 通过向工作流添加其他活动来继续编辑工作流。 启动该程序并完成上一个查询步骤后，将显示找到的收件人数量。 您可以使用鼠标弹出菜单显示更多详细信息(右键单击过渡> **[!UICONTROL Display the target...]**)。

   ![](assets/query_example_result.png)

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识查询所针对的群体。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms：recipient）和 **[!UICONTROL recCount]** 是表中的元素数。

此值是工作表的架构。 此参数对于具有的所有过渡都有效 **[!UICONTROL tableName]** 和 **[!UICONTROL schema]**.

## 优化查询 {#optimizing-queries}

以下部分提供了优化在Adobe Campaign上运行的查询的最佳实践，以限制数据库上的工作负载并改善用户体验。

### 联接和索引 {#joins-and-indexes}

* 高效的查询依赖于索引。
* 对所有连接使用索引。
* 在架构上定义链接将确定连接条件。 链接表应具有主键上的唯一索引，并且联接应位于此字段上。
* 通过在数字字段而不是字符串字段上定义键来执行联接。
* 避免执行外连接。 只要有可能，请使用Zero ID记录实现外部连接功能。
* 对连接使用正确的数据类型。

   确保 `where` 子句与字段的类型相同。

   一个常见的错误是： `iBlacklist='3'` 位置 `iBlacklist` 是一个数字字段，并且 `3` 表示文本值。

   确保您知道查询的执行计划。 避免进行完整的表扫描，尤其是实时查询或每分钟运行的近乎实时的查询。

   有关更多信息（取决于您的Campaign版本），请参阅以下章节：

   ![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文档](../../configuration/using/database-mapping.md)

   ![](assets/do-not-localize/v8.png)[  Campaign v8 文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/shemas-forms/database-mapping.html)

### 函数 {#functions}

* 注意以下功能 `Lower(...)`. 当使用Lower函数时，不使用Index。
* 仔细检查使用“like”指令或“upper”或“lower”指令的查询。 将“Upper”应用于用户输入，而不是应用于数据库字段。

   有关函数的更多信息，请参阅 [本节](../../platform/using/defining-filter-conditions.md#list-of-functions).

### 筛选维度 {#filtering-dimensions}

使用查询的筛选维度，而不是使用“存在方式”运算符。

![](assets/optimize-queries-filtering.png)

在查询中，过滤器中的“存在”条件无效。 它们等同于SQL中的子查询：

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

最佳实践是改用查询的筛选维度：

![](assets/optimize-queries-filtering2.png)

SQL中过滤维度的等效项是内部连接：

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

有关筛选维度的更多信息，请参阅 [本节](building-a-workflow.md#targeting-and-filtering-dimensions).

### 架构 {#architecture}

* 构建开发平台，使用与生产平台类似的卷、参数和架构。
* 对开发和生产环境使用相同的值。 请尽量使用相同的规则：

   * 操作系统,
   * 版本,
   * 数据,
   * 应用程序,
   * 卷。

   >[!NOTE]
   >
   >在开发环境中工作的功能可能无法在数据可能不同的生产环境中工作。 尝试识别主要差异以预测风险并准备解决方案。

* 进行与目标卷匹配的配置。 大型卷需要特定的配置。 适用于100,000个收件人的配置可能无法适用于10,000,000个收件人。

   考虑系统启动后的扩展方式。 仅仅因为某件东西小规模地运作并不意味着它适合更大体积。 应该使用与生产卷类似的卷进行测试。 您还应该评估在高峰时间、高峰日以及在整个项目周期内卷更改（调用数、数据库大小）的影响。
