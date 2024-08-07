---
product: campaign
title: 创建指标
description: 创建指标
feature: Reporting, Monitoring
hide: true
hidefromtoc: true
exl-id: e4806bb8-de9d-47e4-8b37-d6c0565b7f5a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 2%

---

# 创建指标{#creating-indicators}



要使立方正常工作，需要标识相关的维和度量并在立方中创建它们。

要创建立方，请应用以下步骤：

1. 选择工作表。 请参阅[选择工作表](#selecting-the-work-table)。
1. 定义维度。 请参阅[定义维度](#defining-dimensions)。
1. 定义度量。 请参阅[生成指示器](#building-indicators)。
1. 创建聚合（可选）。 请参阅[计算并使用聚合](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)。

此示例说明如何在报告中快速创建简单多维数据集以导出其度量。

实施步骤详见下文。 本章其他部分提供了详尽的选项和描述。

## 选择工作表 {#selecting-the-work-table}

要创建多维数据集，请单击多维数据集列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮。

![](assets/s_advuser_cube_create.png)

选择事实架构，即包含要探索的元素的架构。 在本例中，我们将选择&#x200B;**收件人**&#x200B;表。

![](assets/s_advuser_cube_wz_02.png)

单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建多维数据集：多维数据集将出现在多维数据集列表中，然后可以使用适当的选项卡对其进行配置。

单击&#x200B;**[!UICONTROL Filter the source data...]**&#x200B;链接可将此Cube的计算应用于数据库中的选定数据。

![](assets/s_advuser_cube_wz_03.png)

## 定义维度 {#defining-dimensions}

Dimension与根据多维数据集相关事实架构为每个多维数据集定义的分析轴一致。 这些是在分析中探索的维度，如时间（年、月、日期……）、产品或合同的分类（家庭、参考资料等）、人口区段（按城市、年龄组、地位等）。

这些分析轴在Cube的&#x200B;**[!UICONTROL Dimension]**&#x200B;选项卡中定义。

单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以创建新维度，然后在&#x200B;**[!UICONTROL Expression field]**&#x200B;中，单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标以选择包含相关数据的字段。

![](assets/s_advuser_cube_wz_04.png)

* 从选择收件人&#x200B;**年龄**&#x200B;开始。 对于此字段，您可以定义对年龄进行分组，并使信息阅读更加容易。 当存在多个单独值的可能性时，我们建议使用量化。

  为此，请选中&#x200B;**[!UICONTROL Enable binning]**&#x200B;选项。 在[数据量化](../../reporting/using/concepts-and-methodology.md#data-binning)中详细介绍了量化模式。

  ![](assets/s_advuser_cube_wz_05.png)

* 添加&#x200B;**日期**&#x200B;类型维度。 此处，我们要显示收件人用户档案创建日期

  为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;并选择收件人表中的&#x200B;**[!UICONTROL Creation date]**&#x200B;字段。

  ![](assets/s_advuser_cube_wz_06.png)

  可以选择日期显示模式。 要执行此操作，请选择要使用的层次和要生成的级别：

  ![](assets/s_advuser_cube_wz_07.png)

  在我们的示例中，我们只希望显示年、月和日，因为无法同时使用周和半年/月：这些级别不兼容。

* 创建另一个维度以分析相对于收件人城市的数据

  为此，请添加新维度，然后在收件人架构的&#x200B;**[!UICONTROL Location]**&#x200B;节点中选择城市。

  ![](assets/s_advuser_cube_wz_08.png)

  您可以启用量化以使信息读取更轻松并将值链接到明细列表。

  ![](assets/s_advuser_cube_wz_09.png)

  从下拉列表中选择明细列表

  ![](assets/s_advuser_cube_wz_10.png)

  将仅显示枚举中的值。 其他人将分组到&#x200B;**[!UICONTROL Label of the other values]**&#x200B;字段中定义的标签下。

  有关详细信息，请参阅[动态管理回收站](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins)。

## 构建指标 {#building-indicators}

定义维度后，您需要为要在单元格中显示的值指定计算模式。 为此，请在&#x200B;**[!UICONTROL Measures]**&#x200B;选项卡中创建匹配指示器：创建与报告中要显示的列数一样多的度量，这些列将使用多维数据集。

要执行此操作，请应用以下步骤：

1. 单击 **[!UICONTROL Add]** 按钮。
1. 选择要应用的度量类型和公式。 这里，我们要统计一下女性在受助者中的数量。

   我们的度量值基于事实架构并使用&#x200B;**[!UICONTROL Count]**&#x200B;运算符。

   ![](assets/s_advuser_cube_wz_11.png)

   **[!UICONTROL Filter the measure data...]**&#x200B;链接允许您仅选择女性。 有关定义度量和可用选项的详细信息，请参阅[定义度量](../../reporting/using/concepts-and-methodology.md#defining-measures)。

   ![](assets/s_advuser_cube_wz_12.png)

1. 输入度量的标签并保存。

   ![](assets/s_advuser_cube_wz_13.png)

1. 保存多维数据集。

## 基于多维数据集创建报告 {#creating-a-report-based-on-a-cube}

配置多维数据集后，可将其用作创建新报告的模板。

操作步骤：

1. 单击&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡的&#x200B;**[!UICONTROL Create]**&#x200B;按钮，然后选择刚刚创建的多维数据集。

   ![](assets/s_advuser_cube_wz_14.png)

1. 单击&#x200B;**[!UICONTROL Create]**&#x200B;按钮确认：这会将您转到报告配置和查看页面。

   默认情况下，前两个可用尺寸以行和列提供，但表中不显示任何值。 要生成表，请单击主图标：

   ![](assets/s_advuser_cube_wz_15.png)

1. 可以切换尺寸的轴、删除它们、添加新测量等。 在[此页面](../../reporting/using/using-cubes-to-explore-data.md)中详细描述了可能的操作。

   要实现此目的，请使用相应的图标。

   ![](assets/s_advuser_cube_wz_16.png)
