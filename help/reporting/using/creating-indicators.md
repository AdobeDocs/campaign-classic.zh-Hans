---
title: 创建指示器
seo-title: 创建指示器
description: 创建指示器
seo-description: null
page-status-flag: never-activated
uuid: 3caaba6b-b6c8-4b64-b123-d7098e9ddc7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: a5fc6c78-b4fb-41fd-a072-7be4ece3c554
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 创建指示器{#creating-indicators}

要使立方体正常工作，您需要识别相关的维和度量并在立方中创建它们。

要创建立方，请应用以下步骤：

1. 选择工作表。 请参阅 [选择工作表](#selecting-the-work-table)。
1. 定义维。 请参阅定 [义维](#defining-dimensions)。
1. 定义度量。 请参阅构 [建指标](#building-indicators)。
1. 创建聚合（可选）。 请参阅计 [算和使用聚合](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)。

此示例向您展示如何在报表中快速创建一个简单的立方体以导出其度量。

实施步骤详见下文。 本章的其他部分提供详尽的选项和说明。

## 选择工作表 {#selecting-the-work-table}

要创建立方，请单击 **[!UICONTROL New]** 立方列表上方的按钮。

![](assets/s_advuser_cube_create.png)

选择事实架构，即包含要浏览的元素的架构。 在此示例中，我们将选择“收件人 **”(Recipient** )表。

![](assets/s_advuser_cube_wz_02.png)

单击 **[!UICONTROL Save]** 以创建立方：它将显示在多维数据集列表中，然后可以使用相应的选项卡进行配置。

单击链 **[!UICONTROL Filter the source data...]** 接，将此多维数据集的计算应用到数据库中的选定数据。

![](assets/s_advuser_cube_wz_03.png)

## 定义维 {#defining-dimensions}

维与根据每个立方的相关数值架构为其定义的分析轴一致。 这些是分析中探索的维度，如时间（年、月、日……）、产品或合同的分类（家庭、参考等）、人口细分（按城市、年龄组、状态等）。

这些分析轴在立方的选 **[!UICONTROL Dimension]** 项卡中定义。

单击 **[!UICONTROL Add]** 按钮以创建新维，然后在中单击 **[!UICONTROL Expression field]**&#x200B;图标 **[!UICONTROL Edit expression]** 以选择包含相关数据的字段。

![](assets/s_advuser_cube_wz_04.png)

* 首先选择收件人 **年龄**。 对于此字段，您可以定义绑定以分组页面并使信息阅读更简单。 我们建议在可能有多个单独值时使用绑定。

   要执行此操作，请选中该 **[!UICONTROL Enable binning]** 选项。 绑定模式在数据绑定中 [有详细介绍](../../reporting/using/concepts-and-methodology.md#data-binning)。

   ![](assets/s_advuser_cube_wz_05.png)

* 添加 **日期** 类型维。 此处，我们要显示收件人个人资料的创建日期

   要执行此操作，请单 **[!UICONTROL Add]** 击并选择收 **[!UICONTROL Creation date]** 件人表中的字段。

   ![](assets/s_advuser_cube_wz_06.png)

   可以选择日期显示模式。 为此，请选择要使用的层次结构和要生成的级别：

   ![](assets/s_advuser_cube_wz_07.png)

   在我们的示例中，我们只希望显示年份、月份和日期，因为不能同时使用周和学期／月：这些级别不兼容。

* 创建另一个维度以分析与接收城市相关的数据

   为此，请添加新维，然后在收件人架构的节 **[!UICONTROL Location]** 点中选择城市。

   ![](assets/s_advuser_cube_wz_08.png)

   您可以启用绑定，以便更轻松地读取信息，并将这些值链接到枚举。

   ![](assets/s_advuser_cube_wz_09.png)

   从下拉列表中选择枚举

   ![](assets/s_advuser_cube_wz_10.png)

   将仅显示枚举中的值。 其他组将分组在字段中定义的标签下 **[!UICONTROL Label of the other values]** 面。

   有关详细信息，请参阅动态 [管理素材箱](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins)。

## 建筑指标 {#building-indicators}

定义维后，您需要为要显示在单元格中的值指定计算模式。 为此，请在选项卡中创建匹配的指 **[!UICONTROL Measures]** 示符：创建将使用立方的报表中显示的列数量。

为此，请应用以下步骤：

1. Click the **[!UICONTROL Add]** button.
1. 选择要应用的度量类型和公式。 这里我们想统计一下受助者中的妇女人数。

   我们的度量基于事实图，并使用运算 **[!UICONTROL Count]** 符。

   ![](assets/s_advuser_cube_wz_11.png)

   该链 **[!UICONTROL Filter the measure data...]** 接允许您仅选择女性。 有关定义度量和可用选项的详细信息，请参阅定 [义度量](../../reporting/using/concepts-and-methodology.md#defining-measures)。

   ![](assets/s_advuser_cube_wz_12.png)

1. 输入度量的标签并保存它。

   ![](assets/s_advuser_cube_wz_13.png)

1. 保存立方。

## 创建基于立方的报表 {#creating-a-report-based-on-a-cube}

配置多维数据集后，可将其用作创建新报表的模板。

操作步骤：

1. 单击 **[!UICONTROL Create]** 宇宙的按 **[!UICONTROL Reports]** 钮，然后选择您刚刚创建的立方。

   ![](assets/s_advuser_cube_wz_14.png)

1. 单击按 **[!UICONTROL Create]** 钮以确认：此操作将带您进入报表配置和查看页面。

   默认情况下，前两个可用尺寸以行和列的形式提供，但表中不显示任何值。 要生成表，请单击主图标：

   ![](assets/s_advuser_cube_wz_15.png)

1. 您可以切换维的轴、删除它们、添加新测量等。 可能的操作详见：使 [用多维数据集探索数据](../../reporting/using/using-cubes-to-explore-data.md)。

   为此，请使用相应的图标。

   ![](assets/s_advuser_cube_wz_16.png)

