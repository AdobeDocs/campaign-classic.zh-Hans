---
product: campaign
title: 使用分析报表
description: 使用分析报表
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Reporting, Monitoring
exl-id: d133efec-33e1-4711-a90f-e40385059386
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 2%

---

# 使用分析报表{#processing-a-report}



## 保存分析报告 {#saving-an-analysis-report}

如果您具有相应的权限，则可以保存从模板创建的分析报告，或将其导出为Excel、PDF或OpenOffice格式。

要保存报表，请单击 **[!UICONTROL Save]** 并为您的报告设置一个标签。

选择 **[!UICONTROL Also save data]** 如果您希望创建报表的历史记录，并在保存时查看报表的值。 有关详细信息，请参见 [存档分析报告](#archiving-analysis-reports).

此 **[!UICONTROL Share this report]** 选项允许其他操作员访问报表。

![](assets/s_ncs_user_report_wizard_010.png)

保存后，此报告可以重复用于生成其他分析报告：

![](assets/s_ncs_user_report_wizard_08a.png)

要对此报告进行更改，请编辑 **[!UICONTROL Administration > Configuration > Adobe Campaign tree reports]** Adobe Campaign树的节点（或操作员具有编辑权限的第一个“报表”类型文件夹）。 有关详细信息，请参见 [配置描述性分析报告的布局](#configuring-the-layout-of-a-descriptive-analysis-report).

## 分析报告其他设置 {#analysis-report-additional-settings}

保存描述性分析报告后，可以编辑其属性并访问其他选项。

![](assets/s_ncs_user_report_wizard_08b.png)

这些选项与标准报告相同，详见 [此页面](../../reporting/using/properties-of-the-report.md).

## 配置描述性分析报告的布局 {#configuring-the-layout-of-a-descriptive-analysis-report}

您可以在描述性分析的图表和表格中个性化数据的显示和布局。 所有选项均可通过以下位置的Adobe Campaign树进行访问： **[!UICONTROL Edit]** 选项卡中。

### 分析报表显示模式 {#analysis-report-display-mode}

在使用创建报告时 **[!UICONTROL qualitative distribution]** 默认情况下会选择模板、表格和图表显示模式。 如果只需要一种显示模式，请取消选中相应的复选框。 这意味着只有选中显示模式的选项卡可用。

![](assets/s_ncs_advuser_report_display_01.png)

要更改报表的架构，请单击 **[!UICONTROL Select the link]** 并从数据库中选择另一个表。

![](assets/s_ncs_advuser_report_display_02.png)

### 分析报表显示设置 {#analysis-report-display-settings}

可以隐藏或显示统计和小计，还可以选择统计的方向。

![](assets/s_ncs_advuser_report_display_05.png)

在创建统计数据时，您可以个性化其标签。

![](assets/s_ncs_advuser_report_display_06.png)

其名称将显示在报表中。

![](assets/s_ncs_advuser_report_display_07.png)

但是，如果您取消选中标签和小计显示选项，则这些标签和小计在报表中不可见。 当您将鼠标悬停在表的单元格上时，该名称将显示在工具提示中。

![](assets/s_ncs_advuser_report_display_08.png)

默认情况下，统计信息在线显示。 要更改方向，请从下拉列表中选择相应的选项。

![](assets/s_ncs_advuser_report_wizard_035a.png)

在以下示例中，统计信息以列显示。

![](assets/s_ncs_advuser_report_wizard_035.png)

### 分析报表数据布局 {#analysis-report-data-layout}

您可以直接在描述性分析表中将数据布局个性化。 要实现此目的，请右键单击要使用的变量。 从下拉菜单中选择可用的选项：

* **[!UICONTROL Pivot]** 以更改变量的轴。
* **[!UICONTROL Up]** / **[!UICONTROL Down]** 以换行变量。
* **[!UICONTROL Move to the right]** / **[!UICONTROL Move to the left]** 以交换列中的变量。
* **[!UICONTROL Turn]** 反转变量轴。
* **[!UICONTROL Sort from A to Z]** 对变量值进行低到高的排序。
* **[!UICONTROL Sort from Z to A]** 对变量值进行高到低的排序。

  ![](assets/s_ncs_advuser_report_wizard_016.png)

要返回到初始显示，请刷新视图。

### 分析报表图表选项 {#analysis-report-chart-options}

可以在图表中个性化显示数据。 要执行此操作，请单击 **[!UICONTROL Variables...]** 在图表类型选择阶段可用的链接。

![](assets/s_ncs_advuser_report_wizard_3c.png)

可以使用以下选项：

* 窗口的上半部分允许您修改图表显示区域。
* 默认情况下，标签显示在图表中。 您可以通过取消选中以隐藏它们 **[!UICONTROL Show values]** 选项。
* 此 **[!UICONTROL Accumulate values]** 选项允许您将一个系列中的值累加到另一个系列。
* 您可以决定是否要显示图表图例：要隐藏图表图例，请取消选中相应的选项。 默认情况下，图例显示在图表右上角的外部。

  图例也可以显示在图表的顶部，以节省显示空间。 要实现此目的，请选择选项 **[!UICONTROL Include in the chart]**

  选择中的垂直和水平对齐方式 **[!UICONTROL Caption position]** 下拉列表。

  ![](assets/s_ncs_advuser_report_wizard_3d.png)

## 导出分析报告 {#exporting-an-analysis-report}

要从分析报表中导出数据，请单击下拉列表并选择所需的输出格式。

![](assets/s_ncs_user_report_wizard_09.png)

有关详细信息，请参见[此页面](../../reporting/using/actions-on-reports.md)。

## 重复利用现有报告和分析 {#re-using-existing-reports-and-analyses}

您可以使用已存储在Adobe Campaign中的现有报表创建关于数据的描述性分析报表。 在保存分析或创建报告并将其配置为可通过描述性分析向导访问时，可以使用此模式。

要了解如何保存描述性分析，请参阅 [保存分析报告](#saving-an-analysis-report).

要创建描述性分析报表，必须通过工作流过渡或通过 **[!UICONTROL Tools > Descriptive analysis]** 菜单。

1. 选择 **[!UICONTROL Existing analyses and reports]** 并单击 **[!UICONTROL Next]**。
1. 通过此选项可访问可用报告的列表。 选择要生成的报告。

   ![](assets/s_ncs_user_report_wizard_01.png)

## 存档分析报告 {#archiving-analysis-reports}

在基于现有分析创建描述性分析时，可以创建存档来存储数据和比较报告结果。

要创建历史记录，请应用以下步骤：

1. 打开现有的分析或创建新的描述性分析向导。
1. 在报表显示页面中，单击按钮以在工具栏中创建历史记录，然后进行确认，如下所示：

   ![](assets/reporting_descriptive_historize_icon.png)

1. 使用“存档访问”按钮可显示以前的分析。

   ![](assets/reporting_descriptive_historize_access.png)
