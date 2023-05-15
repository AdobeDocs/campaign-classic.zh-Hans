---
product: campaign
title: 创建新报告
description: 了解创建新报告的关键步骤
feature: Reporting
exl-id: 4c2aad47-0e2d-4d0b-8898-b437f4a05e11
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# 创建新报告{#creating-a-new-report}



要创建报表，请应用以下步骤：

1. 打开Adobe Campaign Explorer，然后从 **[!UICONTROL Administration > Configuration]** 节点，然后选择 **[!UICONTROL Reports]** 文件夹。
1. 单击 **[!UICONTROL New]** 按钮。
1. 选择 **[!UICONTROL Create a new report from a template]** 并单击 **[!UICONTROL Next]**。

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. 在下拉列表中选择报表模板。

   * 的 **[!UICONTROL Extended report]** 允许您创建使用图表配置的报表。
   * 的 **[!UICONTROL Qualitative distribution]** 报表允许您根据所有类型的数据（公司名称、电子邮件域等）创建统计信息。
   * 的 **[!UICONTROL Quantitative distribution]** 利用报表，可创建可测量或计数的数据（发票金额、收件人年龄等）的统计资料。

   有关这些报表模板的更多信息，请参阅 [此部分](../../reporting/using/about-descriptive-analysis.md).

1. 在相应的字段中输入报表名称及其说明。 指定 **[!UICONTROL schema]** 将在其上应用报表。

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. 保存此报表。

## 为图表建模 {#modelizing-the-chart}

保存报表后，应显示此内容。 您现在可以构建报表图表。

![](assets/s_ncs_user_report_wizard_021.png)

报告的构建图由一系列活动组成。

![](assets/s_ncs_advuser_report_wizard_031.png)

活动使用过渡向上链接，由箭头表示。

![](assets/s_ncs_advuser_report_wizard_032.png)

要构建报表，请根据报表的性质和上下文，确定有用元素并对其逻辑顺序进行建模。

1. 使用 **[!UICONTROL Start]** 活动，以实现构建报表所要执行的第一个流程。 每个报表只能使用其中一个活动。

   如果图表包含循环，则它是必选项。

1. 添加一个或多个 **[!UICONTROL Query]** 活动来收集对构建报表有用的数据。 可以通过数据库模式上的查询直接收集数据，也可以通过导入的列表或现有多维数据集进行收集。

   有关更多信息，请参阅 [收集数据进行分析](../../reporting/using/collecting-data-to-analyze.md).

   此数据将根据页面配置显示在报表中（或不显示）。

1. 放置一个或多个 **[!UICONTROL Page]** 活动，以定义所收集数据的图形表示形式。 您可以插入表格、图表、输入字段和条件，以显示一个或多个页面或页面元素。 显示的内容可完全配置。

   有关更多信息，请参阅 [静态元素](#static-elements).

1. 使用 **[!UICONTROL Test]** 活动，以定义显示或访问数据的条件。

   有关更多信息，请参阅 [调整页面显示](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display).

1. 如有必要，请通过 **[!UICONTROL Script]** 活动，例如计算报表名称、过滤特定上下文中结果的显示等。

   有关更多信息，请参阅 [脚本活动](../../reporting/using/advanced-functionalities.md#script-activity).

1. 最后，为了更便于阅读复杂报表，您可以插入一个或多个 **[!UICONTROL Jump]** 键入活动。 这样，您就可以从一个活动转到另一个活动，而无需在报表中实现过渡。 的 **[!UICONTROL Jump]** 活动还可用于显示其他报表。

   有关更多信息，请参阅 [跳转活动](../../reporting/using/advanced-functionalities.md#jump-activity).

不能同时执行多个分支。 这表示以下方式构建的报表将不起作用：

![](assets/reporting_graph_sample_ko.png)

但是，您可以放置多个分支。 将只执行其中一个：

![](assets/reporting_graph_sample_ok.png)

## 创建页面 {#creating-a-page}

内容通过置于图表中的活动进行配置。 有关更多信息，请参阅 [模型化图表](#modelizing-the-chart).

要配置活动，请双击其图标。

显示的内容在 **页面** 键入活动。

报表可以包含一个或多个页面。 页面是通过专用编辑器创建的，该编辑器允许您在树结构中插入输入字段、选择字段、静态元素、图表或表。 容器可帮助您定义布局。 有关更多信息，请参阅 [元素布局](../../reporting/using/element-layout.md).

要向页面添加组件，请使用工具栏左上角的图标。

![](assets/reporting_add_component_in_page.png)

您还可以右键单击要添加组件的节点，然后从列表中选择该组件。

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>如果报表准备以Excel格式导出，我们建议不要使用复杂的HTML格式。 有关更多信息，请参阅 [导出报表](../../reporting/using/actions-on-reports.md#exporting-a-report).

A **[!UICONTROL Page]** 可以包含以下元素：

* 条形图、饼图、曲线类型 **[!UICONTROL charts]**&#x200B;等。
* 引导；包含组或划分的列表 **[!UICONTROL tables]**.
* 文本或数字类型 **[!UICONTROL Input controls]**.
* 下拉列表、复选框、单选按钮、多选项、日期或矩阵类型 **[!UICONTROL Selection controls]**.
* 链接编辑器、常量、文件夹选择类型 **[!UICONTROL Advanced controls]**.
* 值、链接、HTML、图像等 **[!UICONTROL Static elements]**.
* **[!UICONTROL Containers]** 可让您控制组件布局。

有关页面及其组件的配置模式的详情，请参阅 [此部分](../../web/using/about-web-forms.md).

利用工具栏，可添加或删除控件，并在报表页面中组织其顺序。

![](assets/s_ncs_advuser_report_wizard_08.png)

### 静态元素 {#static-elements}

静态元素允许您在报表中显示用户不会与之交互的信息，如图形元素或脚本。 请参阅 [此部分](../../web/using/static-elements-in-a-web-form.md#inserting-html-content) 以了解更多信息。

![](assets/s_advuser_report_page_activity_03.png)

### 过滤报表中的信息 {#filtering-information-in-a-report}

通过输入和选择控件，您可以过滤报表中显示的信息。 有关实施此类筛选的更多信息，请参阅 [查询中的筛选选项](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries).

要了解有关创建和配置输入字段和选择字段的更多信息，请参阅 [此部分](../../web/using/about-web-forms.md).

您可以将一个或多个输入控件集成到报表中。 此类型的控件允许您根据输入的值筛选显示的信息。

![](assets/reporting_control_text.png)

您还可以将一个或多个选择控件集成到报表中。 此类型的控件允许您根据选定的值过滤报表中包含的信息，例如：

* 通过单选按钮或复选框：

   ![](assets/reporting_radio_buttons.png)

* 通过下拉列表：

   ![](assets/reporting_control_list.png)

* 通过日历：

   ![](assets/reporting_control_date.png)

最后，您可以将一个或多个高级控件集成到报表中。 此类控件允许您插入链接、常量或选择文件夹。

在此，您可以过滤报表中的数据，以仅显示树的其中一个文件夹中包含的信息：

![](assets/reporting_control_folder.png)
