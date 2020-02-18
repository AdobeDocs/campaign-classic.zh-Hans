---
title: 定位数据
seo-title: 定位数据
description: 定位数据
seo-description: null
page-status-flag: never-activated
uuid: 90c46ae9-8f9d-4538-a0fe-92fb3373f863
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 79f1e85a-b5e6-4875-ac57-ab979fc57079
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# 定位数据{#targeting-data}

## 创建查询 {#creating-queries}

### 选择数据 {#selecting-data}

活动 **[!UICONTROL Query]** 允许您选择基本数据以构建目标人群。 有关详细信息，请参阅 [创建查询](../../workflow/using/query.md#creating-a-query)。

您还可以使用以下活动查询和优化数据库中的数据：增量 [查询](../../workflow/using/incremental-query.md), [读取列表](../../workflow/using/read-list.md)。

可以收集要在整个工作流生命周期中转发和处理的其他数据。 有关详细信息，请参阅添 [加数据](../../workflow/using/query.md#adding-data)[和编辑其他数据](#editing-additional-data)。

### 编辑其他数据 {#editing-additional-data}

添加其他数据后，您可以编辑它或使用它来调整在查询活动中定义的目标。

通过 **[!UICONTROL Edit additional data...]** 该链接可以查看添加的数据，并对其进行修改或添加。

![](assets/wf_add_data_edit_link.png)

要向先前定义的输出列添加数据，请在可用字段列表中选择它。 要创建新的输出列，请单击图 **[!UICONTROL Add]** 标，然后选择字段并单击 **[!UICONTROL Edit expression]**。

![](assets/query_add_an_output_column.png)

为要添加的字段定义计算模式，例如聚合。

![](assets/query_add_an_output_column_formula.png)

通过 **[!UICONTROL Add a sub-item]** 此选项，可将计算数据附加到集合。 这允许您从集合中选择其他数据，或定义集合元素的聚合计算。

![](assets/query_add_columns_subscription_sub-element.png)

子元素将在其映射到的集合的子树中表示。

集合显示在 **[!UICONTROL Collections]** 子选项卡中。 可以通过单击所选集合的图标来过 **[!UICONTROL Detail]** 滤收集的元素。 过滤器向导允许您选择收集的数据并指定要应用于集合中数据的过滤条件。

![](assets/query_add_columns_collection.png)

### 使用其他数据优化目标 {#refining-the-target-using-additional-data}

收集的其他数据使您能够调整数据库中的数据过滤。 要执行此操作，请单击链 **[!UICONTROL Refine the target using additional data...]** 接：这样，您就可以对添加的数据进行过滤。

![](assets/wf_add_data_use_additional_data.png)

### 均化数据 {#homogenizing-data}

在活 **[!UICONTROL Union]** 动或 **[!UICONTROL Intersection]** 键入活动中，您可以选择仅保留共享的其他数据以保持数据的一致性。 在这种情况下，此活动的临时输出工作台将仅包含所有入站集中找到的其他数据。

![](assets/option-common_additionnal_col_only.png)

### 与其他数据协调 {#reconciliation-with-additional-data}

在数据协调阶段(**[!UICONTROL Union]**、 **[!UICONTROL Intersection]**&#x200B;等)中 活动)，则可以从其他列中选择要用于数据协调的列。 为此，请针对所选列配置对帐并指定主集。 然后，选择窗口下列中的列，如下例所示：

![](assets/select-column-and-join.png)

### 创建子集 {#creating-subsets}

通过 **[!UICONTROL Split]** 该活动，您可以根据通过提取查询定义的条件创建子集。 对于每个子集，在编辑群体上的筛选条件时，您随后将访问标准查询活动，该活动允许您定义目标分段条件。

您可以将目标拆分为多个子集，只使用附加数据作为筛选条件，或除目标数据之外。 如果您已购买Federated Data Access选项，则还可以使用 **外部数据** 。

有关详细信息，请参阅使 [用拆分活动创建子集](#creating-subsets-using-the-split-activity)。

## 细分数据 {#segmenting-data}

### 组合多个目标（联合） {#combining-several-targets--union-}

联合活动允许您在一个过渡中合并多个活动的结果。 集合不一定必须是同质的。

![](assets/join_reconciliation_options.png)

以下数据协调选项可用：

* **[!UICONTROL Keys only]**

   如果输入总体是同质的，则可以使用此选项。

* **[!UICONTROL All columns in common]**

   通过此选项，您可以根据目标各种人群通用的所有列协调数据。

   Adobe Campaign根据列的名称来标识列。 接受容差阈值：例如，“电子邮件”列可以识别为与“@email”列相同。

* **[!UICONTROL A selection of columns]**

   选择此选项可定义要应用数据协调的列列表。

   首先选择主集（包含源数据的集），然后选择要用于连接的列。

   ![](assets/join_reconciliation_options_01.png)

   >[!CAUTION]
   >
   >在数据协调过程中，不会消除重复人群。

   您可以将人口大小限制为给定数量的记录。 为此，请单击相应的选项并指定要保存的记录数。

   此外，指定入站人群的优先级：窗口的下部列出联合活动的入站过渡，并允许您使用窗口右侧的蓝色箭头对它们进行排序。

   记录将首先从列表中第一入站过渡的人口中获取，如果未达到最大，则从第二入站过渡的人口中获取。

   ![](assets/join_limit_nb_priority.png)

### 提取关节数据（交集） {#extracting-joint-data--intersection-}

![](assets/traitements.png)

该交叉点允许您仅恢复入站过渡总体共享的线。 此活动的配置应与工会活动类似。

此外，可以只保留一系列列，或仅保留入站人群共享的列。

交叉点活动在“交叉点”部分 [中详细](../../workflow/using/intersection.md) 。

### 排除人口（排除） {#excluding-a-population--exclusion-}

排除活动允许您从其他目标人群中排除目标元素。 此活动的输出定位维度将是主集合的输出定位维度。

必要时，可以处理入站表。 事实上，要从其他维中排除目标，此目标必须返回到与主目标相同的目标维。 为此，请单击按 **[!UICONTROL Add]** 钮并指定维更改条件。

通过标识符、更改轴或连接执行数据协调。 使用列表中的 [数据中提供了示例：阅读列表](../../workflow/using/importing-data.md#using-data-from-a-list--read-list)。

![](assets/exclusion_edit_add_rule_01.png)

### 使用拆分活动创建子集 {#creating-subsets-using-the-split-activity}

活动 **[!UICONTROL Split]** 是一个标准活动，它允许您通过一个或多个筛选维度创建任意数量的集合，以及为每个子集生成一个输出过渡或唯一过渡。

由入站过渡所传送的附加数据可以被用于过滤标准中。

要进行配置，您首先需要选择条件：

1. 在您的工作流程中，拖放活 **[!UICONTROL Split]** 动。
1. 在选项卡 **[!UICONTROL General]** 中，选择所需的选项： **[!UICONTROL Use data from the target and additional data]**, **[!UICONTROL Use the additional data only]** 或 **[!UICONTROL Use external data]**。
1. 如果选 **[!UICONTROL Use data from the target and additional data]** 择此选项，则定位维允许您使用入站过渡传送的所有数据。

   ![](assets/split-general-tab-options.png)

   当创建子集时，使用上述过滤参数。

   要定义筛选条件，请选择选 **[!UICONTROL Add a filtering condition on the inbound population]** 项并单击链 **[!UICONTROL Edit...]** 接。 然后指定用于创建此子集的过滤条件。

   ![](assets/split-subset-config-all-data.png)

   本节介绍如何使用活动中的过滤条 **[!UICONTROL Split]** 件将目标细分为不同人群的示 [例](../../workflow/using/cross-channel-delivery-workflow.md)。

   该字 **[!UICONTROL Label]** 段允许您为新创建的子集指定一个名称，该名称将匹配出站过渡。

   您还可以为子集分配区段代码，以识别该子集并使用它定位其人群。

   如有必要，您可以针对要创建的每个子集分别更改定位和筛选维度。 为此，请编辑子集的筛选条件并选中该选 **[!UICONTROL Use a specific filtering dimension]** 项。

   ![](assets/split-subset-config-specific-filtering.png)

1. 如果选 **[!UICONTROL Use the additional data only]** 择了此选项，则仅为子集筛选提供其他数据。

   ![](assets/split-subset-config-additional-data-only.png)

1. 如果启 **用了“联合数据访问****[!UICONTROL Use external data]** ”选项，则允许您处理已配置的外部数据库中的数据，或创建新的数据库连接。

   ![](assets/split-subset-config-add_external_data.png)

   For more on this, refer to this [section](../../platform/using/about-fda.md).

然后，我们需要添加新子集：

1. 单击该 **[!UICONTROL Add]** 按钮并定义筛选条件。

   ![](assets/wf_split_add_a_tab.png)

1. 在活动的选项卡中定 **[!UICONTROL General]** 义筛选维（请参阅上文）。默认情况下，该维应用于所有子集。

   ![](assets/wf_split_edit_filtering.png)

1. 如有必要，您可以单独更改每个子集的筛选维度。 这样，您可以为所有金卡持有者构建一个集，其中一个适用于点击了最新新闻稿的所有收件人，第三个适用于在过去30天内进行店内购买的18到25岁用户，所有这些用户都使用相同的拆分活动。 为此，请选择选项， **[!UICONTROL Use a specific filtering dimension]** 然后选择数据筛选上下文。

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >如果您已获得“联 **合数据访问”选项** ，则可以根据外部基础中的信息创建子集。 为此，请在字段中选择外部表的架 **[!UICONTROL Targeting dimension]** 构。 有关详细信息，请参阅 [访问外部数据库(FDA)](../../workflow/using/accessing-an-external-database--fda-.md)。

创建子集后，默认情况下，拆分活动显示的输出过渡与有子集的输出过渡一样多：

![](assets/wf_split_multi_outputs.png)

您可以将所有这些子集分组到单个输出过渡中。 在这种情况下，指向各个子集的链接将例如在段代码中可见。 为此，请选择选 **[!UICONTROL Generate all subsets in the same table]** 项。

![](assets/wf_split_select_option_single_output.png)

例如，您可以放置单个交付活动并根据每个收件人集的区段代码个性化交付内容：

![](assets/wf_split_single_output.png)

也可以使用活动创建子 **[!UICONTROL Cells]** 集。 For more on this, refer to the [Cells](../../workflow/using/cells.md) section.

### 使用目标数据 {#using-targeted-data}

在识别和准备数据后，它便可以在以下上下文中使用：

* 您可以在不同工作流程阶段中进行数据操作之后更新数据库中的数据。

   有关详细信息，请更 [新数据](../../workflow/using/update-data.md)。

* 您还可以刷新现有列表的内容。

   For more on this, refer to [List update](../../workflow/using/list-update.md).

* 您可以直接在工作流中准备或开始提交。

   有关详细信息，请参 [阅交付](../../workflow/using/delivery.md)、交 [付控制](../../workflow/using/delivery-control.md)[和连续交付](../../workflow/using/continuous-delivery.md)。

## 数据管理 {#data-management}

在Adobe Campaign中，数据管理通过提供更高效、更灵活的工具组合了一系列活动来解决复杂的定位问题。 这样，您就可以使用与联系人的合同、订阅、交付反应等相关的信息，对联系人的所有通信实施一致的管理。 数据管理允许您在细分操作期间跟踪数据生命周期，特别是：

* 通过包括未在数据集市中建模的数据，简化及优化定位流程（创建新表：根据设定，对每个定位工作流进行本地扩展）。
* 保留和传送缓冲区计算内容，尤其是在目标建构阶段或进行数据库管理时。
* 访问外部数据库（可选）：在定位过程中考虑异构数据库。

为了实施这些操作，Adobe Campaign提供了以下功能：

* 数据收集活动：文 [件传输](../../workflow/using/file-transfer.md), [数据加载（文件）](../../workflow/using/data-loading--file-.md), [数据加载(RDBMS)](../../workflow/using/data-loading--rdbms-.md)，更 [](../../workflow/using/update-data.md)新数据。 收集数据的第一步是准备数据，以便在其他活动中处理它。 需要监视多个参数，以确保工作流正确执行并给出预期结果。 例如，在导入数据时，此数据的主键(Pkey)必须对于每个记录都是唯一的。
* 使用数据管理选项丰富了定位活动：查询 [](../../workflow/using/query.md)、联合 [](../../workflow/using/union.md)、 [交集](../../workflow/using/intersection.md)、 [](../../workflow/using/split.md)拆分。 这允许您配置多个不同定位维度的数据之间的联合或交集，只要能够进行数据协调。
* 数据转换活动：丰 [富](../../workflow/using/enrichment.md), [改变维度](../../workflow/using/change-dimension.md)。

>[!CAUTION]
>
>当链接了两个工作流时，删除源表元素并不表示将删除与它链接的所有数据。
>  
>例如，通过工作流删除收件人不会导致删除收件人的所有交付历史记录。 但是，直接在“收件人”文件夹中删除收件人确实会导致删除此收件人链接的所有数据。

### 丰富和修改数据 {#enriching-and-modifying-data}

除了定位维之外，筛选维还允许您指定所收集数据的性质。 请参阅定 [位和筛选维](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions)。

可以丰富、聚集和操作所识别和收集的数据以优化目标构造。 为此，除了细分数据部分中详细介绍的数据操 [作活动](#segmenting-data) ，还应使用以下功能：

* 通过 **[!UICONTROL Enrichment]** 该活动，您可以立即向架构添加列，并向某些元素添加信息。 活动库的丰富 [化部分](../../workflow/using/enrichment.md) ，对此作了详细介绍。
* 通过 **[!UICONTROL Edit schema]** 该活动，您可以修改架构的结构。 活动存储库的“编 [辑架构](../../workflow/using/edit-schema.md) ”部分详细介绍了此步骤。
* 通过 **[!UICONTROL Change dimension]** 此活动，您可以在目标构建周期中更改定位维。 在“更改”(Change)维部分 [中详细介绍](../../workflow/using/change-dimension.md) 。

