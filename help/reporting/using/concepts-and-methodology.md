---
title: 概念和方法
seo-title: 概念和方法
description: 概念和方法
seo-description: null
page-status-flag: never-activated
uuid: 595e9183-97f5-470d-9d82-dcd756e1fc83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 4655ad65-7eba-44d5-b3f9-f4b8f44d9d5c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1494'
ht-degree: 1%

---


# 多维数据集的最佳实践{#concepts-and-methodology}

## 数据绑定 {#data-binning}

绑定使您能够根据条件对值进行分组以简化数据显示。 根据您可用的信息，您可以定义年龄组、将电子邮件域分组到一起、限制为值明细列表、明确限制数据显示和分组专用行或列中的所有其他数据，等等。

总的来说，有三种类型的绑定可用：

1. 使用手动定义的值范围。 例如，年龄、平均购物车、已打开的投放数等。) For more on this, refer to [Defining each bin](#defining-each-bin).
1. 根据明细列表的值动态调整：只显示明细列表中包含的值，所有其他值都分组在“其他”中。 有关此内容的详细信息，请参 [阅动态管理素材箱](#dynamically-managing-bins)。
1. 使用值范围，将所有其他值组合在一起。 例如，18到25岁，26到59岁，以及其他。 有关此方面的详细信息，请参 [阅创建值范围](#creating-value-ranges)。

要启用绑定，请在创建维时选中相应的框。

![](assets/s_advuser_cube_class_00.png)

您可以手动创建素材箱或将它们链接到现有明细列表。

Adobe Campaign还为自动绑定提供助手：值可分为N个组，或根据数据库中最频繁的值进行分组。

### 定义每个素材箱 {#defining-each-bin}

要单独创建每个素材箱，请选 **[!UICONTROL Define each bin]** 择选项，然后使用表创建各种素材箱。

![](assets/s_advuser_cube_class_01.png)

单击按 **[!UICONTROL Add]** 钮可创建新的素材箱，并列表将分组到素材箱中的值。

![](assets/s_advuser_cube_class_02.png)

在以下示例中，语言被分为三个类别:英语／德语／荷兰语、法语／意大利语／西班牙语和其他语种。

![](assets/s_advuser_cube_class_03.png)

您可以使用SQL掩码将多个值合并到筛选器中。 为此，请 **[!UICONTROL Yes]** 检查列 **[!UICONTROL Use an SQL mask]** 并输入要在列中应用的SQL过滤 **[!UICONTROL Value or expression]** 器。

在以下示例中，与yahoo开始的 **所** 有电子邮件域（yahoo.fr、yahoo.com、yahoo.be等）或 **ymail** （ymail.com、ymail.eu等） 将分组在标签 **YAHOO!**，以及rocketmail.com域 **的地址** 。

![](assets/s_advuser_cube_class_03b.png)

### 动态管理素材箱 {#dynamically-managing-bins}

值可以通过明细列表动态管理。 这意味着只显示明细列表中包含的值。 当明细列表值发生变化时，多维数据集的内容会自动调整。

要创建此类型的值绑定，请应用以下步骤：

1. 创建新维并启用绑定。
1. 选择选 **[!UICONTROL Dynamically link the values to an enumeration]** 项，然后选择匹配明细列表。

   ![](assets/s_advuser_cube_class_04.png)

   只要更新明细列表值，匹配素材箱就自动调整。

### 创建值范围 {#creating-value-ranges}

您可以根据所需的间隔将值分组到多个范围内。

要手动定义范围，请单击 **[!UICONTROL Add]** 按钮并选择 **[!UICONTROL Define a range]** :

![](assets/s_advuser_cube_class_05.png)

然后指定下限和上限，并单 **[!UICONTROL Ok]** 击进行确认。

### 自动生成素材箱 {#generating-bins-automatically}

还可以自动生成素材箱。 为此，请单击链 **[!UICONTROL Generate bins...]** 接。

![](assets/s_advuser_cube_class_06.png)

您可以：

* 恢复最常用的值

   在以下示例中，将显示4个最常使用的值，而其他值将被计数并分组在“其他”类别中。

* 以槽形式生成素材箱

   在以下示例中，Adobe Campaign自动创建4个大小相同的值槽，以在数据库中显示值。

在这种情况下，将忽略事实模式中选择的筛选器。

### 明细列表 {#enumerations}

为了提高报表的相关性和可读性，“Adobe Campaign”允许您创建特定明细列表，将不同值重新组合到同一个素材箱中。 这些明细列表保留为绑定，在多维数据集中引用，然后显示在报告中。

Adobe Campaign还优惠域上的明细列表，它允许您显示数据库中所有联系人的电子邮件域的列表，按ISP重新分组，如下例所示：

![](assets/nmx_report_sample.png)

它使用以下模板构建：

![](assets/nmx_enum_domain.png)

要使用此明细列表创建报表，请使用维创建 **[!UICONTROL Email domain]** 多维数据集。 Choose the **[!UICONTROL Enable binning]** option then **[!UICONTROL Dynamically link the values to an enumeration]**. 然后选择 **域明细列表** ，如上所示。 没有指定别名的所有值都将重新组合到“其 **他** ”标签下。

![](assets/nmx_add_dimension.png)

然后，根据此多维数据集创建报告以显示值。

您只需修改明细列表即可更新相关报告。 例如，创建 **Adobe** 值并添加 **adobe.com别名** ，报表将自动更新为明细列表级别的Adobe值。

![](assets/nmx_add_alias.png)

该 **[!UICONTROL Domains]** 明细列表用于生成显示域列表的内置报告。 要调整这些报表的内容，您可以编辑此列表。

您可以创建保留用于绑定的其他明细列表，并将其用于其他多维数据集:所有别名值将重新组合到第一个明细列表选项卡中指定的素材箱中。

## 计算和使用聚合 {#calculating-and-using-aggregates}

最大的数据卷可以以聚合计算。

聚合在处理大量数据时很有用。 它们会根据在专用工作流框中定义的设置自动更新，以将最近收集的数据集成到指示器中

聚合在每个多维数据集的相关标签中定义。

![](assets/s_advuser_cube_agregate_01.png)

>[!NOTE]
>
>用于更新聚合计算的工作流可以在聚合本身中配置，或者可以通过链接到相关多维数据集的外部工作流来更新聚合。

要创建新聚合，请应用以下步骤：

1. 单击多维数据集 **[!UICONTROL Aggregates]** 的选项卡，然后单击该 **[!UICONTROL Add]** 按钮。

   ![](assets/s_advuser_cube_agregate_02.png)

1. 为聚合输入标签，然后添加要计算的维。

   ![](assets/s_advuser_cube_agregate_03.png)

1. 选择维和级别。 对每个维和每个级别重复此过程。
1. 单击选 **[!UICONTROL Workflow]** 项卡以创建聚合工作流。

   ![](assets/s_advuser_cube_agregate_04.png)

   * 活动 **[!UICONTROL Scheduler]** 允许您定义计算更新的频率。 调度程序详见 [本节](../../workflow/using/scheduler.md)。
   * 该 **[!UICONTROL Aggregate update]** 活动允许您选择要应用的更新模式：完整或部分。

      默认情况下，在每次计算过程中都会执行完全更新。 要启用部分更新，请选择相关选项并定义更新条件。

      ![](assets/s_advuser_cube_agregate_05.png)

## 定义度量 {#defining-measures}

度量类型在多维数据集的选 **[!UICONTROL Measures]** 项卡中定义。 您可以计算和、平均值、偏差等。

您可以根据需要创建任意数量的度量：然后，选择要在表中显示或隐藏的度量。 For more on this, refer to [Displaying measures](#displaying-measures).

要定义新度量，请应用以下步骤：

1. 单击 **[!UICONTROL Add]** 度量列表上方的按钮，并选择度量类型和要计算的公式。

   ![](assets/s_advuser_cube_create_a_measure.png)

1. 如有必要，并根据操作符选择操作所关注的表达式。

   通过 **[!UICONTROL Advanced selection]** 该按钮可创建复杂的计算公式。 如需详细信息，请参阅[此部分](../../platform/using/about-queries-in-campaign.md)。

   ![](assets/s_advuser_cube_create_a_measure_01.png)

1. 该链 **[!UICONTROL Filter the measure data...]** 接允许您限制计算字段，并仅将其应用于数据库中的特定数据。

   ![](assets/s_advuser_cube_create_a_measure_02.png)

1. 输入度量的标签并添加描述，然后单击 **[!UICONTROL Finish]** 以创建它。

## 显示度量 {#displaying-measures}

您可以根据需要配置表中度量的显示：

* 度量的显示顺序(请参 [阅显示顺序](#display-sequence)),
* 要在报告中显示／隐藏的信息(请参 [阅配置显示](#configuring-the-display))
* 显示哪些度量：百分比、总数、小数位数等。 (请参阅 [更改显示的度量类型](#changing-the-type-of-measure-displayed))。

### 显示序列 {#display-sequence}

在多维数据集中计算的度量通过按钮进行 **[!UICONTROL Measures]** 配置。

移动行以更改显示顺序。 在以下示例中，法语数据将移至列表底部：这意味着它将显示在最后一列中。

![](assets/s_advuser_cube_in_report_config_04.png)

### 配置显示 {#configuring-the-display}

可针对每个测量或整体单独执行测量、行和列的配置。 通过特定图标可访问显示模式选择窗口。

* 单击该 **[!UICONTROL Edit the configuration of the pivot table]** 图标以访问配置窗口。

   您可以选择是否显示度量的标签以及配置其布局（行或列）。

![](assets/s_advuser_cube_in_report_config_05.png)

使用颜色选项可以突出显示重要值以便于阅读。

![](assets/s_advuser_cube_in_report_config_06.png)

### 更改显示的度量类型 {#changing-the-type-of-measure-displayed}

在每个度量中，您可以定义要应用的单位和格式。

![](assets/s_advuser_cube_in_report_config_07.png)

## 共享报告 {#sharing-a-report}

配置报告后，您可以保存报告并与其他操作员共享它。

为此，请单击图 **[!UICONTROL Show the report properties]** 标并启用选 **[!UICONTROL Share this report]** 项。

![](assets/cube_share_option.png)

指定报表所属的类别及其相关性。 有关详细信息，请参 [阅本页](../../reporting/using/configuring-access-to-the-report.md#report-display-context) 的显 **示序**&#x200B;列和定 **义筛选选项部分** 。

要确认这些更改，您需要保存报告。

![](assets/cube_share_confirm.png)

## 创建过滤器 {#creating-filters}

可以创建过滤器来查看数据的某个部分。

操作步骤：

1. 单击该 **[!UICONTROL Add a filter]** 图标。

   ![](assets/neolap_add_filter.png)

1. 选择筛选器所关注的维

   ![](assets/neolap_define_filter.png)

1. 选择滤镜类型及其精度级别。

   ![](assets/neolap_ceate_filter.png)

1. 创建过滤器后，过滤器将显示在报表上方。

   ![](assets/neolap_filter_zone.png)

   单击过滤器以编辑它。

   单击叉形以删除它。

   您可以根据需要合并任意数量的过滤器:它们都将显示在此区域。

   ![](assets/neolap_multiple_filters.png)

每次修改过滤器（添加、删除、更改）时，都必须重新计算报告。

过滤器也可以根据选择创建。 为此，请选择源单元格、行和列，然后单击图 **[!UICONTROL Add a filter]** 标。

要选择行、列或单元格，请左键单击它。 要取消选择，请再次单击。

![](assets/neolap_create_filter_from_selection.png)

过滤器将自动应用并添加到报表上方的过滤器区域。

![](assets/neolap_create_filter_display.png)

