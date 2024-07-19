---
product: campaign
title: 创建新报告
description: 了解创建新报告的关键步骤
feature: Reporting, Monitoring
exl-id: 4c2aad47-0e2d-4d0b-8898-b437f4a05e11
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# 创建新报告{#creating-a-new-report}



要创建报告，请应用以下步骤：

1. 打开Adobe Campaign Explorer，然后从&#x200B;**[!UICONTROL Administration > Configuration]**&#x200B;节点中选择&#x200B;**[!UICONTROL Reports]**&#x200B;文件夹。
1. 单击报告列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮。
1. 选择 **[!UICONTROL Create a new report from a template]** 并单击 **[!UICONTROL Next]**。

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. 在下拉列表中选择报表模板。

   * **[!UICONTROL Extended report]**&#x200B;允许您创建使用图表配置的报告。
   * **[!UICONTROL Qualitative distribution]**&#x200B;报表允许您根据所有类型的数据（公司名称、电子邮件域等）创建统计数据。
   * **[!UICONTROL Quantitative distribution]**&#x200B;报表允许您创建可测量或计数的数据（发票金额、收件人年龄等）的统计信息。

   有关这些报告模板的更多信息，请参阅[此章节](../../reporting/using/about-descriptive-analysis.md)。

1. 在相应字段中输入报表名称及其说明。 指定要应用报告的&#x200B;**[!UICONTROL schema]**。

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. 保存此报表。

## 为图表建模 {#modelizing-the-chart}

保存报告后，应会显示该内容。 您现在可以构建报告的图表。

![](assets/s_ncs_user_report_wizard_021.png)

用于构建报表的图表由一系列活动组成。

![](assets/s_ncs_advuser_report_wizard_031.png)

活动使用由箭头表示的过渡进行链接。

![](assets/s_ncs_advuser_report_wizard_032.png)

要根据报告的性质和上下文来构建报告，您需要确定有用的元素并建模其逻辑序列。

1. 使用&#x200B;**[!UICONTROL Start]**&#x200B;活动具体化要执行的第一个生成报告的进程。 每个报表只能使用其中一个活动。

   如果图表包含循环，则此为必填字段。

1. 添加一个或多个&#x200B;**[!UICONTROL Query]**&#x200B;活动以收集对生成报告有用的数据。 可以直接通过数据库架构上的查询来收集数据，也可以通过导入的列表或现有多维数据集来收集数据。

   有关详情，请参阅[收集要分析的数据](../../reporting/using/collecting-data-to-analyze.md)。

   此数据将在报表中显示（或不显示），具体取决于页面配置。

1. 放置一个或多个&#x200B;**[!UICONTROL Page]**&#x200B;活动以定义所收集数据的图形表示。 您可以插入表、图表、输入字段，并设置显示一个或多个页面或页面元素的条件。 显示的内容可进行完全配置。

   有关详细信息，请参阅[静态元素](#static-elements)。

1. 使用&#x200B;**[!UICONTROL Test]**&#x200B;活动定义显示或访问数据的条件。

   有关详情，请参阅[调节页面显示](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display)。

1. 如有必要，请通过&#x200B;**[!UICONTROL Script]**&#x200B;活动添加个性化脚本，例如，计算报表名称，筛选特定上下文中的结果显示等。

   有关详细信息，请参阅[脚本活动](../../reporting/using/advanced-functionalities.md#script-activity)。

1. 最后，为了更便于阅读复杂报表，您可以插入一个或多个&#x200B;**[!UICONTROL Jump]**&#x200B;类型活动。 这样，您就可以从一个活动转到另一个活动，而无需在报表中实体化过渡。 **[!UICONTROL Jump]**&#x200B;活动也可用于显示其他报告。

   有关详细信息，请参阅[跳转活动](../../reporting/using/advanced-functionalities.md#jump-activity)。

不能同时执行多个分支。 这意味着类似这样的报表将无法正常运行：

![](assets/reporting_graph_sample_ko.png)

但是，您可以放置多个分支。 将只执行其中一个：

![](assets/reporting_graph_sample_ok.png)

## 创建页面 {#creating-a-page}

内容可通过置于图表中的活动进行配置。 有关详细信息，请参阅[建模图表](#modelizing-the-chart)。

要配置活动，请双击其图标。

显示的内容在&#x200B;**页面**&#x200B;类型活动中定义。

报表可以包含一个或多个页面。 页面通过专用编辑器创建，该编辑器允许您以树结构插入输入字段、选择字段、静态元素、图表或表。 容器可帮助您定义布局。 有关详细信息，请参阅[元素布局](../../reporting/using/element-layout.md)。

要将组件添加到页面，请使用工具栏左上角部分的图标。

![](assets/reporting_add_component_in_page.png)

您还可以右键单击要添加组件的节点，然后从列表中选择该节点。

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>如果报告预定以Excel格式导出，我们建议不要使用复杂的HTML格式。 有关详细信息，请参阅[导出报告](../../reporting/using/actions-on-reports.md#exporting-a-report)。

**[!UICONTROL Page]**&#x200B;可以包含以下元素：

* 条形图、饼图、曲线类型&#x200B;**[!UICONTROL charts]**&#x200B;等。
* 透视；具有组或划分&#x200B;**[!UICONTROL tables]**&#x200B;的列表。
* 文本或数字类型&#x200B;**[!UICONTROL Input controls]**。
* 下拉列表、复选框、单选按钮、多项选择、日期或矩阵类型&#x200B;**[!UICONTROL Selection controls]**。
* 链接编辑器、常量、文件夹选择类型&#x200B;**[!UICONTROL Advanced controls]**。
* 值、链接、HTML、图像等。**[!UICONTROL Static elements]**。
* 允许您控制组件布局的&#x200B;**[!UICONTROL Containers]**。

[此部分](../../web/using/about-web-forms.md)详细介绍了页面及其组件的配置模式。

利用工具栏，您可以添加或删除控件，并组织它们在报表页面中的顺序。

![](assets/s_ncs_advuser_report_wizard_08.png)

### 静态元素 {#static-elements}

您可以使用静态元素在报表中显示用户不会与之交互的信息，如图形元素或脚本。 有关详细信息，请参阅[此部分](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

![](assets/s_advuser_report_page_activity_03.png)

### 过滤报表中的信息 {#filtering-information-in-a-report}

使用输入和选择控件，可以筛选报表中显示的信息。 有关实现此类筛选的详细信息，请参阅查询中的[筛选选项](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries)。

要了解有关创建和配置输入字段和选择字段的更多信息，请参阅[此章节](../../web/using/about-web-forms.md)。

您可以将一个或多个输入控件集成到报表中。 通过此类控件，可根据输入的值筛选显示的信息。

![](assets/reporting_control_text.png)

您还可以将一个或多个选择控件集成到报表中。 通过此类控件，可根据选定的值筛选报表中包含的信息，例如：

* 通过单选按钮或复选框：

  ![](assets/reporting_radio_buttons.png)

* 通过下拉列表：

  ![](assets/reporting_control_list.png)

* 通过日历：

  ![](assets/reporting_control_date.png)

最后，您可以将一个或多个高级控件集成到报表中。 通过这种类型的控件，可以插入链接、常量或选择文件夹。

在此处，您可以筛选报告中的数据，以仅显示树中某个文件夹包含的信息：

![](assets/reporting_control_folder.png)
