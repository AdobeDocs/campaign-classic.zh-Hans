---
title: 使用描述性分析向导
seo-title: 使用描述性分析向导
description: 使用描述性分析向导
seo-description: null
page-status-flag: never-activated
uuid: 30554909-4b91-46ff-bd8d-fa57ab6304f9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 18ba04d9-7bab-4eea-8dbb-6c2c138c5293
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 使用描述性分析向导{#using-the-descriptive-analysis-wizard}

要创建描述性分析报告，请使用专用向导。 配置取决于要分析的数据以及所需的渲染。

## 分析数据库中的数据 {#analyzing-data-in-the-database}

描述性分析向导可以通过菜单启 **[!UICONTROL Tools > Descriptive analysis]** 动：在这种情况下，分析会默认涉及收件人(**nms:recipient**)。 它适用于Adobe Campaign数据库中的所有数据。

![](assets/reporting_descriptive_wz_launch.png)

要分析标准收件人之外的表(**nms:recipient**)，请单击向导最后一步中的链接，然后选择与设置匹配的表，在本例中， **[!UICONTROL Advanced settings...]** cus:individual ****:

![](assets/reporting_descriptive_other_schema.png)

如果要对部分数据生成统计信息，可以定义过滤器：要执行此操作，请单击链 **[!UICONTROL Advanced settings...]** 接并定义要应用的过滤器，如下所示：

![](assets/reporting_descriptive_wz_filter.png)

这项分析只涉及16岁及以上、住在伦敦的数据库接收人。

## 分析一组数据 {#analyzing-a-set-of-data}

您可以通过其他上下文使用描述性分析向导：列表、工作流转换、一个或多个提交、所选收件人等。

它可通过指向收件人表的Adobe Campaign树的多个节点访问。

通过选择项目并右键单击打开描述性分析向导。 将仅分析选定的数据。

![](assets/reporting_descriptive_from_recipients.png)

* 对于一组收件 **人**，选择要分析的收件人，然后右键单击并选择 **[!UICONTROL Actions > Explore...]**，如上所示。 如果将过滤器应用于收件人列表，则只会分析其内容。

   要选择文件夹或当前筛选器中的所有收件人，请使用CTRL+A快捷键。 这意味着即使未显示的收件人也会被选中。

   有关收件人的描述性分析的示例，请参阅：定 [性数据分析](../../reporting/using/use-cases.md#qualitative-data-analysis)。

* 在工作流的上 **下文中**，将光标放在指向收件人表的过渡上，右键单击并选择 **[!UICONTROL Analyze target]**。 有关详细信息，请参阅分析工作流中 [的过渡目标中的示例](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow)。
* 对于 **列表**，请选择一个或多个列表，并应用与收件人相同的流程。
* 在分发的上下 **文中**，选择要分析其目标的分发，右键单击并选择 **[!UICONTROL Actions > Explore the target]**，如下所示：

   ![](assets/reporting_descriptive_from_deliveries.png)

   以下是提交的描述性分析示例：分 [析人口](../../reporting/using/use-cases.md#analyzing-a-population) ，并在此处：分析 [收件人跟踪日志](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs)。

## 配置定性分发模板 {#configuring-the-qualitative-distribution-template}

通过 **[!UICONTROL Qualitative distribution]** 该模板，您可以创建有关所有类型数据（例如公司名称、电子邮件域）的统计信息。

通过模板创建的报表的可用配置选 **[!UICONTROL Qualitative distribution]** 项在表格的显示 [数据中有详细说明](#displaying-data-in-the-table)。 分析人群中详细介绍 [了完整示例](../../reporting/using/use-cases.md#analyzing-a-population)。

当您使用描述性分析向导分析数据时，可用的选项取决于所选的设置。 下文详述。

### 数据绑定 {#data-binning}

选择要显示的变量时，可以定义数据绑定，即为所选数据配置分组条件。

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>当使用聚合计算所涉及的场时，检查以改 **[!UICONTROL The data is already aggregated]** 进性能。

这些选项会因字段内容而异：

* **[!UICONTROL None]** :此选项允许您显示变量的所有可用值，而无需绑定。

   >[!CAUTION]
   >
   >应谨慎使用此选项：它会对报告和机器性能产生重大影响。

* **[!UICONTROL Auto]** :此选项允许您显示n个最频繁表示的值。 它们会自动计算，每个变量表示与素材箱数相比的变量百分比。 对于数值，Adobe Campaign会自动生成n个类，将数据分类到中。
* **[!UICONTROL Manual]** :此选项的操作方式与 **[!UICONTROL Auto]** 选项类似，只是您可以手动设置这些值。 为此，请单 **[!UICONTROL Add]** 击值表右侧的按钮。

   在个性化之前，Adobe Campaign可以自动初始化这些值：为此，请输入要生成的素材箱数并单击链 **[!UICONTROL Initialize with]** 接，如下所示：

   ![](assets/reporting_descriptive_initialize.png)

   然后调整内容以满足您的需求：

   ![](assets/reporting_descriptive_initialize_perso.png)

   根据所需的精度级别，包含日期的字段可以按时间、日、月、年等进行分组。

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** :允许您创建数值组。 例如，值为10的模允许您创建一个值间隔，该间隔以十为单位更改。

   ![](assets/reporting_descriptive_initialize_modulo.png)

   通过此示例，您可以按年龄组查看收件人的细目。

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### 在表中显示数据 {#displaying-data-in-the-table}

使用工具栏可个性化显示表中的变量：删除列、以行而非列显示数据、将列向左或向右移动、查看或更改值计算。

![](assets/s_ncs_user_report_wizard_toolbar.png)

在窗口的上半部分，您可以选择显示设置。

您可以显示或隐藏统计信息的名称和子合计，并选择统计信息的方向。 有关详细信息，请参阅 [Analysis报告显示设置](../../reporting/using/processing-a-report.md#analysis-report-display-settings)。

### 在图表中显示数据 {#displaying-data-in-the-chart}

在描述性分析向导的第一步中，您可以选择仅以图表形式显示数据，而不显示表。 在这种情况下，配置图形时必须完成变量选择。 必须首先选择要显示的变量数，然后从相关数据库中选择字段。

![](assets/s_ncs_user_report_wizard_023.png)

然后，选择所需的图表类型。

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>可以同时在图表和表中显示变量。 为此，请在窗口中输入变 **[!UICONTROL Table configuration]** 量。 在图 **[!UICONTROL Next]** 表配置窗口中单击并选择图表类型。 如果子维在表中定义，则不会在图表中显示。

单击该 **[!UICONTROL Variants]** 链接可修改图表属性。

![](assets/reporting_descriptive_graphe_options.png)

提供的选项取决于所选的图表类型。 For more information, refer to [this page](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

### 统计计算 {#statistics-calculation}

通过描述性分析向导，您可以计算有关数据的几种类型的统计信息。 默认情况下，只配置一个简单计数。

单击 **[!UICONTROL Add]** 可创建新统计信息。

![](assets/reporting_descriptive_create_stat.png)

可以执行以下操作：

* **[!UICONTROL Count]** 计算要聚集的字段的所有非空值，包括（聚集字段的）重复值，
* **[!UICONTROL Average]** 计算数值场中的平均值，
* **[!UICONTROL Minimum]** 计算数值场中的最小值，
* **[!UICONTROL Maximum]** 计算数值场中的最大值，
* **[!UICONTROL Sum]** 计算数值场中值的和，
* **[!UICONTROL Standard deviation]** 计算返回值在平均值周围的分布情况，
* **[!UICONTROL Row percentage distribution]** 要计算列中的值与行中的值的比值（仅适用于表）,
* **[!UICONTROL Column percentage distribution]** 要计算行中的值与列中值的比值（仅适用于表）,
* **[!UICONTROL Total percentage distribution]** 计算值所涉及的接收者的分布，

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** 创建个性化的操作员（仅适用于表）。 在字 **[!UICONTROL User function]** 段中，您可以输入要应用于数据的计算。

   示例：根据国家／地区和来源计算每位客户的平均购买额

   ![](assets/report_compute_data_sample1.png)

   要在表中显示上述信息，您需要创建一个计算字段以存储每位客户的平均购买额。

   操作步骤：

   1. 计算购买总数。

      ![](assets/report_compute_data_sample2.png)

   1. 此统计信息不会显示在表中。 您需要取消选 **[!UICONTROL Display in the table]** 中选项卡的选 **[!UICONTROL Advanced]** 项。

      ![](assets/report_compute_data_sample3.png)

   1. 创建新类 **[!UICONTROL Calculated field]** 型统计，并在字段中输入以下公 **[!UICONTROL User function]** 式： **@purchases/@count**。

      ![](assets/report_compute_data_sample4.png)

### 显示报告 {#displaying-the-report}

在向导的最后一步中，您可以显示报表，即已配置的表或图表。

当报表包含表时，计算结果单元格将着色。 结果越高，颜色越浓。

![](assets/report_compute_data_sample1.png)

可以更改结果的布局。 为此，右键单击相关变量，并从快捷菜单中选择输入。

![](assets/s_ncs_user_report_wizard_029.png)

当报表包含图表时，图例的标签允许您过滤显示的信息：单击标签以启用／禁用图表中的显示。

![](assets/report_display_data_in_graph.png)

## 配置定量分发模板 {#configuring-the-quantitative-distribution-template}

要自行生成描述性分析，请从模板 **中选择“新建描述性分析”(New descriptive analysis** from a template)选项（如果未在默认情况下设置）。

用 **[!UICONTROL Quantitative distribution]** 于生成可测量或计数的数据的统计信息的模板（例如发票额、收件人的年龄）。

通过模板创建的分析报告的配置模式在 **[!UICONTROL Quantitative distribution]** 实施示例定量数据分 [析中详细描述](../../reporting/using/use-cases.md#quantitative-data-analysis)。

使用描述性分析向导创建定量报告时可用的选项在下面进行了详细介绍。

首先选择计算所关注的变量：

![](assets/s_ncs_user_report_wizard_017.png)

默认情况下，Adobe Campaign提供一系列统计信息，以便为选定数据计算。 您可以根据需要更改此列表、添加到该列表或删除统计信息。

可以执行以下操作：

* **[!UICONTROL Count]** 计算要聚集的字段的所有非空值，包括（聚集字段的）重复值，
* **[!UICONTROL Average]** 计算数值场中的平均值，
* **[!UICONTROL Minimum]** 计算数值场中的最小值，
* **[!UICONTROL Maximum]** 以计算数值字段中值的最大值。
* **[!UICONTROL Sum]** 计算数值场中值的和，
* **[!UICONTROL Standard deviation]** 以计算返回的值在平均值周围的分布情况。
* **[!UICONTROL Number of missing values]** 以计算未定义值的数字字段数。
* **[!UICONTROL Decile distribution]** 分配返回的值，使每个值代表数字字段中值的1/10。
* **[!UICONTROL Custom distribution]** 根据用户定义的阈值分发返回的值。

   通过 **[!UICONTROL Detail...]** 该按钮可编辑统计信息，并根据需要个性化其计算或显示：

   ![](assets/s_ncs_user_report_wizard_030.png)

   向导的最后一步显示定量分析报告。

   ![](assets/reporting_descriptive_view_report.png)

   要更改报表，请参阅处 [理报表](../../reporting/using/processing-a-report.md)。

