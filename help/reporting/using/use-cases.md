---
product: campaign
title: 用例
description: 报表用例
feature: Reporting
exl-id: e326e32e-7bb0-46ff-9ba5-94ccd1169af2
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 0%

---

# 用例{#use-cases}

![](../../assets/common.svg)

## 分析群体 {#analyzing-a-population}

以下示例允许您使用描述性分析向导来探索一组新闻稿所定向的群体。

下面详细介绍了实施步骤，本章的其他部分提供了详尽的选项和说明列表。

### 确定要分析的群体 {#identifying-the-population-to-analyze}

在本例中，我们希望了解 **新闻稿** 文件夹。

要执行此操作，请选择相关投放，然后右键单击并选择 **[!UICONTROL Action > Explore the target...]**.

![](assets/reporting_quick_start_1.png)

### 选择分析类型 {#selecting-a-type-of-analysis}

在助手的第一步中，您可以选择要使用的描述性分析模板。 默认情况下，Adobe Campaign提供了两个模板： **[!UICONTROL Qualitative distribution]** 和 **[!UICONTROL Quantitative distribution]**. 有关更多信息，请参阅 [配置定性分发模板](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-qualitative-distribution-template) 中。 有关各种渲染，请参见 [关于描述性分析](../../reporting/using/about-descriptive-analysis.md) 中。

在本例中，选择 **[!UICONTROL Qualitative distribution]** 模板，并选择具有图表和表（数组）的显示屏。 为报表命名（“描述性分析”），然后单击 **[!UICONTROL Next]**.

![](assets/reporting_descriptive_quickstart_step_1.png)

### 选择要显示的变量 {#selecting-the-variables-to-display}

下一步允许您选择要在表格中显示的数据。

单击 **[!UICONTROL Add...]** 链接以选择包含要显示数据的变量。 在此，我们希望在一行中显示投放收件人所在的城市：

![](assets/reporting_descriptive_quickstart_step_2.png)

列将显示每家公司的购买次数。 在本例中，金额在 **Web购买** 字段。

在此，我们要定义结果绑定以阐明其显示。 为此，请选择 **[!UICONTROL Manual]** 并设置要显示的区段的计算类：

![](assets/reporting_descriptive_quickstart_step_2a.png)

然后，单击 **[!UICONTROL Ok]** 以批准配置。

定义行和列后，可以使用工具栏更改、移动或删除它们。

![](assets/reporting_descriptive_quickstart_step_2b.png)

### 定义显示格式 {#defining-the-display-format}

在向导的下一步中，您可以选择要生成的图表类型。

在这种情况下，选择直方图。

![](assets/reporting_descriptive_quickstart_step_3.png)

不同图形的可能配置详见 [分析报表图表选项](../../reporting/using/processing-a-report.md#analysis-report-chart-options) 中。

### 配置统计量以计算 {#configuring-the-statistic-to-calculate}

然后，指定要应用于收集数据的计算。 默认情况下，描述性分析向导会执行简单的值计数。

利用此窗口可定义要计算的统计信息列表。

![](assets/reporting_descriptive_quickstart_step_4.png)

要创建新统计信息，请单击 **[!UICONTROL Add]** 按钮。 有关更多信息，请参阅 [统计计算](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).

### 查看和使用报表 {#viewing-and-using-the-report}

向导的最后一步是显示表格和图表。

您可以使用表格上方的工具栏存储、导出或打印数据。 有关更多信息，请参阅 [处理报表](../../reporting/using/processing-a-report.md).

![](assets/reporting_descriptive_quickstart_step_5.png)

## 定性数据分析 {#qualitative-data-analysis}

### 图表显示示例 {#example-of-a-chart-display}

**Target**:生成潜在客户或客户位置的分析报告。

1. 打开描述性分析向导，然后选择 **[!UICONTROL Chart]** 仅。

   ![](assets/s_ncs_user_report_wizard_05a.png)

   单击 **[!UICONTROL Next]** 以批准此步骤。

1. 然后，选择 **[!UICONTROL 2 variables]** 选项，并指定 **[!UICONTROL First variable (abscissa)]** 将指代收件人状态（潜在客户/客户），而第二个变量将指代国家/地区。
1. 选择 **[!UICONTROL Cylinders]** 类型。

   ![](assets/s_ncs_user_report_wizard_05.png)

1. 单击 **[!UICONTROL Next]** 并保留默认值 **[!UICONTROL Simple count]** 统计。
1. 单击 **[!UICONTROL Next]** 以显示报表。

   ![](assets/s_ncs_user_report_wizard_04.png)

   将鼠标悬停在条形图上可查看此国家/地区的确切客户或潜在客户数量。

1. 根据图例启用或禁用其中一个国家/地区的显示。

   ![](assets/s_ncs_user_report_wizard_06png.png)

### 表格显示示例 {#example-of-a-table-display}

**Target**:分析公司电子邮件域。

1. 打开描述性分析向导，然后选择 **[!UICONTROL Array]** 仅显示模式。

   ![](assets/s_ncs_user_report_wizard_03a.png)

   单击 **[!UICONTROL Next]** 按钮以批准此步骤。

1. 选择 **[!UICONTROL Company]** 变量作为列， **[!UICONTROL Email domain]** 变量。
1. 保留 **[!UICONTROL By rows]** 统计方向选项：统计计算将显示在 **[!UICONTROL Email domain]** 变量。

   ![](assets/s_ncs_user_report_wizard_03b.png)

   单击 **[!UICONTROL Next]** 以批准此步骤。

1. 然后，输入要计算的统计信息：保留默认计数并创建新统计资料。 为此，请单击 **[!UICONTROL Add]** 选择 **[!UICONTROL Total percentage distribution]** 作为运算符。

   ![](assets/s_ncs_user_report_wizard_03.png)

1. 为统计信息输入标签，以便在显示报表时不会显示空白字段。

   ![](assets/s_ncs_user_report_wizard_014.png)

1. 单击 **[!UICONTROL Next]** 以显示报表。

   ![](assets/s_ncs_user_report_wizard_06.png)

1. 生成分析报告后，您可以根据需要调整显示内容，而无需更改配置。 例如，您可以切换轴：右键单击域名并选择 **[!UICONTROL Turn]** 的双曲余切值。

   ![](assets/s_ncs_user_report_wizard_07.png)

   表格显示如下信息：

   ![](assets/s_ncs_user_report_wizard_07a.png)

## 定量数据分析 {#quantitative-data-analysis}

**Target**:生成关于收件人年龄的定量分析报告

1. 打开描述性分析向导，然后选择 **[!UICONTROL Quantitative distribution]** 从下拉列表中。

   ![](assets/s_ncs_user_report_wizard_011a.png)

   单击 **[!UICONTROL Next]** 按钮以批准此步骤。

1. 选择 **[!UICONTROL Age]** 变量并输入其标签。 指定它是否为整数，然后单击 **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_report_wizard_011.png)

1. 删除 **[!UICONTROL Deciles]**, **[!UICONTROL Distribution]** 和 **[!UICONTROL Sum]** 统计：这里不需要它们。

   ![](assets/s_ncs_user_report_wizard_012.png)

1. 单击 **[!UICONTROL Next]** 以显示报表。

   ![](assets/s_ncs_user_report_wizard_013.png)

## 分析工作流中的过渡目标 {#analyzing-a-transition-target-in-a-workflow}

**Target**:生成有关定位工作流群体的报告

1. 打开所需的定位工作流。
1. 右键单击指向收件人表的过渡。
1. 选择 **[!UICONTROL Analyze target]** 在下拉菜单中，打开描述性分析窗口。

   ![](assets/s_ncs_user_report_wizard_from_transision.png)

1. 此时，您可以选择 **[!UICONTROL Existing analyses and reports]** 选项，并使用之前创建的报表(请参阅 [重新使用现有报告和分析](../../reporting/using/processing-a-report.md#re-using-existing-reports-and-analyses))，或创建新的描述性分析。 为此，请将 **[!UICONTROL New descriptive analysis from a template]** 选项。

   配置的其余部分与所有描述性分析的配置相同。

### Target分析推荐 {#target-analyze-recommendations}

在工作流中分析群体时，需要该群体仍然存在于过渡中。 如果启动工作流，则可能会从过渡中清除与群体有关的结果。 要运行分析，您可以：

* 将过渡从其目标活动中分离出来，然后启动工作流以使其处于活动状态。 过渡开始闪烁后，按常规方式启动向导。

   ![](assets/s_ncs_user_report_wizard_018.png)

* 通过选择 **[!UICONTROL Keep the result of interim populations between two executions]** 选项。 这样，即使工作流已完成，您也可以对所选过渡进行分析。

   ![](assets/s_ncs_user_report_wizard_020.png)

   如果从过渡中清除了群体，则会显示一条错误消息，要求您在启动描述性分析向导之前选择相关选项。

   ![](assets/s_ncs_user_report_wizard_019.png)

>[!CAUTION]
>
>的 **[!UICONTROL Keep the result of interim populations between two executions]** 选项只能在开发阶段使用，但不能用于生产环境。\
>在达到保留期限后，临时群体会自动清除。 工作流属性中指定了此截止日期 **[!UICONTROL Execution]** 选项卡。

## 分析收件人跟踪日志 {#analyzing-recipient-tracking-logs}

描述性分析向导可以生成其他工作表的报告。 这意味着您可以通过创建专用报告来分析投放日志。

在本例中，我们要分析新闻稿收件人的反应率。

要执行此操作，请应用以下步骤：

1. 通过 **[!UICONTROL Tools > Descriptive analysis]** 菜单，然后更改默认工作表。 选择 **[!UICONTROL Recipient tracking log]** 并添加过滤器以排除校样并包含新闻稿。

   ![](assets/reporting_descriptive_sample_tracking_1.png)

   选择表格显示并单击 **[!UICONTROL Next]**.

1. 在下一个窗口中，指定分析与投放相关。

   ![](assets/reporting_descriptive_sample_tracking_2.png)

   在此，投放标签将显示在第一列中。

1. 删除默认计数并创建三个统计信息，以配置要在表中显示的统计信息。

   在此，对于每个新闻稿，表格将显示：打开次数、点击次数、反应性比率（以百分比表示）。

1. 添加统计信息以计数点击次数：在 **[!UICONTROL Filter]** 选项卡。

   ![](assets/reporting_descriptive_sample_tracking_3.png)

1. 然后，单击 **[!UICONTROL General]** 选项卡，以重命名统计标签和别名：

   ![](assets/reporting_descriptive_sample_tracking_4.png)

1. 添加第二个统计信息以计算打开次数：

   ![](assets/reporting_descriptive_sample_tracking_5.png)

1. 然后，单击 **[!UICONTROL General]** 选项卡，以重命名统计标签及其别名：

   ![](assets/reporting_descriptive_sample_tracking_6.png)

1. 添加第三个统计信息并选择 **[!UICONTROL Calculated field]** 运算符来测量反应率。

   ![](assets/reporting_descriptive_sample_tracking_7.png)

   转到 **[!UICONTROL User function]** 字段，然后输入以下公式：

   ```
   @clic / @open * 100
   ```

   调整统计标签，如下所示：

   ![](assets/reporting_descriptive_sample_tracking_8.png)

   最后，指定是否以百分比形式显示值：要执行此操作，请取消选中 **[!UICONTROL Default formatting]** 选项 **[!UICONTROL Advanced]** 选项卡，选择 **[!UICONTROL Percentage]** 没有小数点。

   ![](assets/reporting_descriptive_sample_tracking_10.png)

1. 单击 **[!UICONTROL Next]** 以显示报表。

   ![](assets/reporting_descriptive_sample_tracking_9.png)

## 分析投放排除日志 {#analyzing-delivery-exclusion-logs}

如果分析涉及投放，则可以分析排除的群体。 为此，请选择要分析的投放，然后右键单击以访问 **[!UICONTROL Action > Explore exclusions]** 菜单。

![](assets/reporting_descriptive_exclusion_menu.png)

这会将您转到描述性分析向导，分析将涉及收件人排除日志。

例如，您可以显示所有排除的地址的域，并按排除日期对其进行排序。

![](assets/reporting_descriptive_exclusion_sample.png)

这将生成以下类型的报表：

![](assets/reporting_descriptive_exclusion_result.png)
