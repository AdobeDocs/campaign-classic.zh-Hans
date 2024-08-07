---
product: campaign
title: 使用多维数据集浏览数据
description: 使用多维数据集浏览数据
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Reporting, Monitoring
hide: true
hidefromtoc: true
exl-id: 32696bbf-1415-4214-837f-5437fdb8b4d4
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 2%

---

# 使用多维数据集浏览数据{#using-cubes-to-explore-data}



Marketing Analytics使创建报告以及通过多维数据集识别和选择数据库中的数据变得更轻松。 这使您能够：

* 根据多维数据集创建报告。 此处详细介绍此过程：[浏览报告中的数据](#exploring-the-data-in-a-report)。
* 收集数据库中的数据，并将其分组到列表中，例如，识别和构建目标和投放。 有关详细信息，请参阅[生成目标群体](#building-a-target-population)。
* 将透视表插入报表中，引用其中的现有多维数据集。 有关详细信息，请参阅[将透视表插入报表](#inserting-a-pivot-table-into-a-report)。

>[!NOTE]
>
>要创建或修改多维数据集，必须使用Marketing Analytics。 有关详细信息，请参阅[关于多维数据集](../../reporting/using/ac-cubes.md)。

## 在报表中浏览数据 {#exploring-the-data-in-a-report}

### 第1步 — 基于多维数据集创建报告 {#step-1---creating-a-report-based-on-a-cube}

要基于多维数据集创建报告，请单击&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Create]**&#x200B;按钮，然后选择要使用的多维数据集。

此处详细描述了此过程：[基于多维数据集创建报告](../../reporting/using/creating-indicators.md#creating-a-report-based-on-a-cube)。

### 第2步 — 选择行和列 {#step-2---selecting-lines-and-columns}

默认显示显示多维数据集的前两个维（在本例中是年龄和城市）。

每个轴上的&#x200B;**[!UICONTROL Add]**&#x200B;按钮允许您添加维度。

![](assets/s_advuser_cube_in_report_03.png)

1. 选择要显示在表的行和列中的尺寸。 为此，请拖放可用的维度，如下所示：
1. 从列表中选择要添加到表中的维：

   ![](assets/s_advuser_cube_in_report_04.png)

1. 然后选择此尺寸的参数。

   ![](assets/s_advuser_cube_in_report_04b.png)

   参数取决于所选维的数据类型。

   例如，对于日期，可以使用多个级别。 有关详细信息，请参阅[显示度量](../../reporting/using/concepts-and-methodology.md#displaying-measures)。

   在此案例中，提供了以下选项：

   ![](assets/s_advuser_cube_in_report_config2.png)

   您可以：

   * 加载期间展开数据：默认情况下，每次更新报表时都会显示这些值（默认值：否）。
   * 在行末显示合计：当数据以列显示时，附加选项允许您在行末显示合计：向表中添加一列（默认值：是）。
   * 应用排序：列的值可以根据值、标签或度量进行排序（默认值：按值）。
   * 按升序(a-z， 0-9)或降序(z-a， 9-0)显示值。
   * 更改加载时要显示的列数（默认情况下： 200）。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;确认：该维度已添加到现有维度。

   表上方的黄色横幅显示您已进行更改：单击&#x200B;**[!UICONTROL Save]**&#x200B;按钮进行保存。

   ![](assets/s_advuser_cube_in_report_04c.png)

### 步骤3 — 配置要显示的度量 {#step-3---configuring-the-measures-to-display}

将行和列放置到位后，即指示要显示的测量及其显示模式。

默认情况下，只显示一个度量。 添加或配置度量：

1. 单击 **[!UICONTROL Measures]** 按钮。

   ![](assets/s_advuser_cube_in_report_05.png)

1. 使用&#x200B;**[!UICONTROL Use a measure]**&#x200B;按钮可选择现有度量之一。

   ![](assets/s_advuser_cube_in_report_08.png)

   选择要显示的信息和格式类型。 选项列表取决于已配置的测量类型。

   ![](assets/s_advuser_cube_in_report_09.png)

   通过标题中的&#x200B;**[!UICONTROL Edit the configuration of the pivot table]**&#x200B;图标，还可以使用整体度量值配置。

   ![](assets/s_advuser_cube_in_report_config_02.png)

   然后，您可以选择是否显示度量标签。 有关详情，请参阅[配置显示区](../../reporting/using/concepts-and-methodology.md#configuring-the-display)。

1. 可以用现有的措施建立新的措施。 为此，请单击&#x200B;**[!UICONTROL Create a measure]**&#x200B;并进行配置。

   ![](assets/s_advuser_cube_in_report_config_02a.png)

   可用的测量类型如下：

   * 测量组合：此类型的测量允许您使用现有测量构建新测量：

     可用的运算符有：和、差、乘和速率。

   * 比例：此类型的测量使您能够计算针对给定维度测量的记录数。 您可以根据维度或子维度计算比例性。
   * 变量：通过此度量，可计算某个级别值的变量。
   * 标准偏差：通过此类度量，可计算每组单元格内与平均值之间的偏差。 例如，您可以比较所有现有区段的购买量。

   创建的度量值将添加到报告中。

   ![](assets/s_advuser_cube_in_report_config_02b.png)

   创建测量后，可以对其进行编辑，并在必要时更改其配置。 为此，请单击&#x200B;**[!UICONTROL Measures]**&#x200B;按钮，然后转到要编辑的度量的选项卡。

   然后单击&#x200B;**[!UICONTROL Edit the dynamic measure]**&#x200B;以访问设置菜单。

## 构建目标群体 {#building-a-target-population}

通过使用多维数据集构建报表，您可以从表中收集数据并将其保存在列表中。

为此，请将它们添加到购物车并处理其内容。

要将群体分组到列表中，请应用以下步骤：

1. 单击包含要收集的群体的单元格以选择它们，然后单击&#x200B;**[!UICONTROL Add to cart]**&#x200B;图标。

   ![](assets/s_advuser_cube_in_report_config_02c.png)

   为此，可根据需要多次收集各种用户档案

1. 单击&#x200B;**[!UICONTROL Show cart]**&#x200B;按钮以查看其内容，然后再运行导出。

   ![](assets/s_advuser_cube_in_report_config_02d.png)

1. 通过&#x200B;**[!UICONTROL Export]**&#x200B;按钮，可将购物车中的项目分组到列表中。

   您需要指定列表名称和要执行的导出类型。

   ![](assets/s-advuser_cube_in_report_config_02e.png)

   单击&#x200B;**[!UICONTROL Start]**&#x200B;以运行导出。

1. 导出完成后，将显示一条消息，确认其执行和已处理的记录数。

   ![](assets/s_advuser_cube_in_report_config_02f.png)

   您可以保存购物车的内容或将其清空。

   通过&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;选项卡访问相关列表。

   ![](assets/s_advuser_cube_in_report_config_02g.png)

## 在报表中插入数据透视表 {#inserting-a-pivot-table-into-a-report}

要创建表并浏览多维数据集中的数据，请应用以下步骤：

1. 创建一个具有单个页面的新报表，并在其中插入数据透视表。 有关详细信息，请参见[此页面](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)。

   ![](assets/s_advuser_cube_in_report_01.png)

1. 在该页的&#x200B;**[!UICONTROL Data]**&#x200B;选项卡中，选择一个多维数据集以处理它包含的维并显示计算的度量。

   ![](assets/s_advuser_cube_in_report_02.png)

   这样，您就可以构建要显示的报表。 有关详细信息，请参阅[第2步 — 选择行和列](#step-2---selecting-lines-and-columns)。
