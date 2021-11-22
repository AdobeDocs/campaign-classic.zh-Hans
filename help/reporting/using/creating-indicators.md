---
product: campaign
title: 创建指标
description: 创建指标
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
exl-id: e4806bb8-de9d-47e4-8b37-d6c0565b7f5a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 2%

---

# 创建指标{#creating-indicators}

![](../../assets/common.svg)

要使多维数据集正常工作，您需要标识相关维度和度量，并在多维数据集中创建它们。

要创建多维数据集，请应用以下步骤：

1. 选择工作表。 请参阅 [选择工作表](#selecting-the-work-table).
1. 定义维度。 请参阅 [定义维度](#defining-dimensions).
1. 定义度量。 请参阅 [建设指标](#building-indicators).
1. 创建聚合（可选）。 请参阅 [计算和使用聚合](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

此示例向您展示了如何快速在报表中创建一个简单多维数据集以导出其度量。

实施步骤详见下文。 本章其他部分中提供了详尽的选项和描述。

## 选择工作表 {#selecting-the-work-table}

要创建多维数据集，请单击 **[!UICONTROL New]** 按钮。

![](assets/s_advuser_cube_create.png)

选择事实架构，即包含要浏览的元素的架构。 在本例中，我们将选择 **收件人** 表。

![](assets/s_advuser_cube_wz_02.png)

单击 **[!UICONTROL Save]** 要创建多维数据集，请执行以下操作：它将显示在多维数据集列表中，然后可以使用相应的选项卡进行配置。

单击 **[!UICONTROL Filter the source data...]** 链接，将此多维数据集的计算应用于数据库中的数据选择。

![](assets/s_advuser_cube_wz_03.png)

## 定义维度 {#defining-dimensions}

Dimension与根据每个多维数据集的相关事实架构为其定义的分析轴一致。 这些是分析中探索的维度，如时间（年、月、日期……）、产品或合同的分类（家庭、参考等）、人口区段（按城市、年龄组、状态等）。

这些分析轴在 **[!UICONTROL Dimension]** 选项卡。

单击 **[!UICONTROL Add]** 按钮以创建新维度，然后在 **[!UICONTROL Expression field]**，请单击 **[!UICONTROL Edit expression]** 图标以选择包含相关数据的字段。

![](assets/s_advuser_cube_wz_04.png)

* 首先，选择收件人 **年龄**. 对于此字段，您可以定义绑定以对页面进行分组，并使信息阅读更轻松。 当可能存在多个单独值时，我们建议使用绑定。

   为此，请检查 **[!UICONTROL Enable binning]** 选项。 绑定模式详见 [数据绑定](../../reporting/using/concepts-and-methodology.md#data-binning).

   ![](assets/s_advuser_cube_wz_05.png)

* 添加 **日期** 类型维度。 在此，我们要显示收件人用户档案的创建日期

   为此，请单击 **[!UICONTROL Add]** ，然后选择 **[!UICONTROL Creation date]** 字段。

   ![](assets/s_advuser_cube_wz_06.png)

   可以选择日期显示模式。 要实现此目的，请选择要使用的层次结构和要生成的级别：

   ![](assets/s_advuser_cube_wz_07.png)

   在我们的示例中，我们只想显示年、月和日，因为无法同时使用周和秒/月：这些级别不兼容。

* 创建另一个维度以分析与收件人所在城市相关的数据

   为此，请添加新维度，然后在 **[!UICONTROL Location]** 收件人模式的节点。

   ![](assets/s_advuser_cube_wz_08.png)

   您可以启用绑定，以便更轻松地读取信息，并将值链接到枚举。

   ![](assets/s_advuser_cube_wz_09.png)

   从下拉列表中选择枚举

   ![](assets/s_advuser_cube_wz_10.png)

   将仅显示枚举中的值。 其他组将分组到 **[!UICONTROL Label of the other values]** 字段。

   有关更多信息，请参阅 [动态管理箱](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins).

## 建设指标 {#building-indicators}

定义维度后，您需要为要在单元格中显示的值指定计算模式。 为此，请在 **[!UICONTROL Measures]** 选项卡：创建要在将使用多维数据集的报表中显示的任意数量的度量。

要执行此操作，请应用以下步骤：

1. 单击 **[!UICONTROL Add]** 按钮。
1. 选择要应用的度量类型和公式。 在这里，我们想统计一下受助者中女性的数量。

   我们的衡量标准基于事实模式，并使用 **[!UICONTROL Count]** 运算符。

   ![](assets/s_advuser_cube_wz_11.png)

   的 **[!UICONTROL Filter the measure data...]** 链接仅允许您选择女性。 有关定义度量和可用选项的更多信息，请参阅 [定义措施](../../reporting/using/concepts-and-methodology.md#defining-measures).

   ![](assets/s_advuser_cube_wz_12.png)

1. 输入度量的标签并保存它。

   ![](assets/s_advuser_cube_wz_13.png)

1. 保存多维数据集。

## 基于多维数据集创建报告 {#creating-a-report-based-on-a-cube}

配置多维数据集后，可将其用作创建新报告的模板。

操作步骤：

1. 单击 **[!UICONTROL Create]** 按钮 **[!UICONTROL Reports]** 选项卡，然后选择您刚刚创建的多维数据集。

   ![](assets/s_advuser_cube_wz_14.png)

1. 单击 **[!UICONTROL Create]** 按钮确认：这会将您转到报表配置和查看页面。

   默认情况下，前两个可用维度以行和列的形式提供，但表中不显示任何值。 要生成表，请单击主图标：

   ![](assets/s_advuser_cube_wz_15.png)

1. 可以切换尺寸的轴、删除这些轴、添加新测量等。 此处详细介绍了可能的操作： [使用多维数据集浏览数据](../../reporting/using/using-cubes-to-explore-data.md).

   为此，请使用相应的图标。

   ![](assets/s_advuser_cube_wz_16.png)
