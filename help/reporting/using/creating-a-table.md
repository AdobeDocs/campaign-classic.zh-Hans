---
product: campaign
title: 创建表
description: 创建表
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 05f76bdf-6dcd-4360-9e72-0ba6a4dd0d5e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2495'
ht-degree: 1%

---

# 创建表{#creating-a-table}

![](../../assets/common.svg)

您可以向报表中添加表格以显示数据。 这可以是基于多维数据集测量创建的数据透视表、具有组的列表或包含值划分的表。

![](assets/s_advuser_report_page_activity_05.png)

## 创建组列表 {#creating-a-list-with-group}

**[!UICONTROL List with group]**&#x200B;类型表允许您对表中的数据进行分组，并生成有关该表的统计信息。 例如，您可以创建数据的总计和子总计。 每个组都有其自己的页眉、详细信息和页脚行。

>[!CAUTION]
>
>包含表的&#x200B;**[!UICONTROL Page]**&#x200B;活动前必须有&#x200B;**[!UICONTROL Query]**&#x200B;或&#x200B;**[!UICONTROL Script]**&#x200B;活动，以收集要在报表中分析的数据。 有关这些活动的更多信息，请参阅[收集数据以分析](../../reporting/using/collecting-data-to-analyze.md)和[脚本活动](../../reporting/using/advanced-functionalities.md#script-activity)。

### 操作原则 {#operating-principle}

您可能需要同时分析多个数据类别。 通过具有组的列表，您可以合并数据并在同一表中创建关于不同数据组的统计信息。 要实现此目的，您可以在表中创建组。

在以下示例中，群组显示数据库中的所有营销活动、投放，以及每个投放和每个营销活动发送的消息数。

它允许您列出与营销活动链接的营销活动(**[!UICONTROL Label (Campaign)]**，投放列表(**[!UICONTROL Label]**)，并允许您在为每个营销活动(**[!UICONTROL Sum(@processed)]**)添加邮件之前，计算每个投放发送的消息数(**[!UICONTROL Processed)]**)。

![](assets/s_advuser_ergo_listgroup_005.png)

### 实施步骤 {#implementation-steps}

此处提供了完整的实施示例：[用例：创建具有群组列表](#use-case--create-a-report-with-a-group-list)的报表。

请注意以下步骤以创建“具有组的列表”类型表：

1. 转到报表图表并放置&#x200B;**[!UICONTROL Query]**&#x200B;活动。 请参阅[收集数据以分析](../../reporting/using/collecting-data-to-analyze.md)。
1. 填写源表格，并选择统计数据将涉及的表格字段。
1. 在图表中放置&#x200B;**[!UICONTROL Page]**&#x200B;活动。 有关更多信息，请参阅[静态元素](../../reporting/using/creating-a-new-report.md#static-elements)。
1. 在页面中插入&#x200B;**[!UICONTROL List with group]**&#x200B;类型表。
1. 指定数据路径，或在查询中选择作为数据源的表。

   如果要稍后恢复源表中的字段并将其插入到表的单元格中，则此步骤是必需的。

1. 创建表及其内容。
1. 在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中显示已完成的报告。 然后，您可以发布报表并将其导出为其他格式（如有必要）。 有关更多信息，请参阅[导出报表](../../reporting/using/actions-on-reports.md#exporting-a-report)。

### 添加行和列 {#adding-lines-and-columns}

默认情况下，**[!UICONTROL List with group]**&#x200B;类型表包括页眉、明细行和页脚行。

组本身包括页眉、详细信息和页脚行。

* **标题行**:利用此行，可为表的列指定标题。

   ![](assets/s_advuser_ergo_listgroup_003a.png)

* **明细行**:此行包含统计值。

   ![](assets/s_advuser_ergo_listgroup_004.png)

* **页脚行**:此行可显示总值。

   ![](assets/s_advuser_ergo_listgroup_003.png)

可以根据需要添加行和列。

该组可置于表的任何行上，并包含其自己的页眉、详细信息和页脚行。

![](assets/s_advuser_ergo_listgroup_019.png)

**行和列**:要添加或删除行或列，请转到现有行或列，然后使用右键单击菜单。

![](assets/s_advuser_ergo_listgroup_006.png)

所添加行的性质取决于光标的位置。 例如，要添加标题行，请将游标置于标题上，然后单击&#x200B;**[!UICONTROL Add > A line above/below]**。

![](assets/s_advuser_ergo_listgroup_006a.png)

列的宽度可以通过&#x200B;**[!UICONTROL Column format]**&#x200B;项修改。

**群组**:要添加群组，请转到行并在下拉菜单中选择匹配的项目。

![](assets/s_advuser_ergo_listgroup_007.png)

### 定义单元格内容 {#defining-cell-content}

要编辑表格的单元格并定义其内容和格式，请转到该单元格并使用右键单击菜单。

使用&#x200B;**[!UICONTROL Expression]**&#x200B;菜单条目选择要显示的值。

![](assets/s_advuser_ergo_listgroup_010.png)

* 要将要分析的值直接插入表中，请在可用字段中选择它们。

   可用字段列表与报表构建图表中表之前查询的内容一致。

   ![](assets/s_advuser_ergo_listgroup_011.png)

* 输入单元格的标签，例如标题。

   要实现此目的，请使用与将字段插入数据库相同的过程，但不要选择表达式。 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入标签。 它将按原样显示。

* 计算聚合（平均值、总和等） 并在单元格中显示。

   要实现此目的，请使用&#x200B;**[!UICONTROL Aggregates]**&#x200B;菜单条目并选择所需的营销活动。

   ![](assets/s_advuser_ergo_listgroup_008.png)

### 定义单元格格式 {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

要定义单元格格式，**[!UICONTROL Cell format...]**&#x200B;菜单允许您访问所选单元格可用的所有格式选项。

通过这些选项，您可以个性化报表的最终渲染并更便于阅读信息。

将数据导出到Excel时，请使用&#x200B;**[!UICONTROL Carriage return]**&#x200B;字段：选择&#x200B;**[!UICONTROL Yes]**&#x200B;值以强制回车。 导出时，将保留此值。 有关更多信息，请参阅[导出报表](../../reporting/using/actions-on-reports.md#exporting-a-report)。

**[!UICONTROL Cell format]**&#x200B;窗口允许您访问以下选项卡：

* **[!UICONTROL Value]**&#x200B;选项卡
* **[!UICONTROL Borders]**&#x200B;选项卡
* **[!UICONTROL Click]**&#x200B;选项卡
* **[!UICONTROL Extra]**&#x200B;选项卡

**[!UICONTROL Value]**&#x200B;选项卡允许您更改字体和各种值属性，或根据其性质定义格式。

![](assets/s_advuser_ergo_listgroup_009.png)

格式更改数据显示：例如，**[!UICONTROL Number]**、**[!UICONTROL Monetary]**&#x200B;和&#x200B;**[!UICONTROL Percentage]**&#x200B;格式允许您对齐右侧的数字并显示小数点。

如何配置货币格式的示例：您可以指定值所用的货币，选择是否分隔千位，并以红色显示负值。 货币符号的位置取决于在其配置文件中定义的运算符的语言。

![](assets/s_advuser_ergo_listgroup_012.png)

日期的配置示例：您可以选择是否显示时间。

![](assets/s_advuser_ergo_listgroup_013.png)

使用&#x200B;**Borders**&#x200B;选项卡可向表中的行和列添加边框。 将大型报表导出到Excel时，向单元格添加边框可能会导致性能问题。

![](assets/s_advuser_ergo_listgroup_014.png)

如有必要，您可以在表模板(**[!UICONTROL Administration > Configuration > Form rendering]**)中定义边框。

在这种情况下，您将使用以下语法：

在Web选项卡中：

```
 .tabular td {
 border: solid 1px #000000;
 }
```

在Excel选项卡中：

```
 <style name="odd" fillColor="#fdfdfd">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
 
 <style name="even" fillColor="#f7f8fa">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
```

通过&#x200B;**[!UICONTROL Click]**&#x200B;选项卡，可定义用户单击单元格或表格内容时的操作。

在以下示例中，单击单元格中的值可显示报表的第二页：它将包含有关单元格中投放的信息。

![](assets/s_advuser_ergo_listgroup_015.png)

通过&#x200B;**Extra**&#x200B;选项卡，可将可视化图表链接到数据，如彩色标记或值栏。 当表格在图表中显示为图例时，会使用彩色标记。 有关更多信息，请参阅实施示例：[步骤5 — 创建第二页](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## 用例：创建包含群组列表的报表 {#use-case--create-a-report-with-a-group-list}

在本例中，我们将创建一个两页的报表：第一页将包含列表、每个营销活动的总投放以及已发送的消息数。 投放名称将是可单击的链接，您将转到报告的第二页，以查看包含表格和图表的选定投放的每个电子邮件域的投放细分。 在第二页上，表格将用作图表的图例。

![](assets/reporting_quick_start_report-final.png)

### 第1步 — 创建报表 {#step-1---create-a-report}

创建与促销活动架构相关的新报告&#x200B;**[!UICONTROL Campaigns (nms)]**。

![](assets/s_advuser_report_listgroup_001.png)

单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建报告。

转到图表并添加用于设计报表内容的第一个组件：第一个查询和第一个页面。

![](assets/reporting_quick_start_diagram.png)

### 第2步 — 创建第一个查询 {#step-2---create-the-first-query}

利用第一个查询，可收集链接到每个营销策划的投放。 目标是显示与每个营销活动链接的Adobe Campaign数据库各种投放情况的报告。

双击第一个查询以对其进行编辑，然后应用以下步骤对其进行配置：

1. 首先，更改应用查询源的架构：选择&#x200B;**[!UICONTROL Deliveries (nms)]**&#x200B;架构。
1. 单击&#x200B;**[!UICONTROL Edit query]**&#x200B;链接并显示高级字段。

   ![](assets/reporting_quick_start_query-1.png)

1. 选择以下字段：

   * 投放标签，
   * 投放的主要关键，
   * 营销活动标签，
   * 已处理投放的指标，
   * Campaign链接的外键，
   * 错误率指示器。

   ![](assets/s_advuser_report_listgroup_002.png)

   将别名链接到每个字段：建议从表格中选择要添加到报表第一页的数据。

   在本例中，我们将使用以下别名：

   * 标签：**@label**
   * 主键：**@deliveryId**
   * 标签（营销活动）：**@label1**
   * 已处理：**@processed**
   * “促销活动”（“id”字段）链接的外键：**@operationId**
   * 错误率：**@errorRatio**


1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;按钮两次以进入&#x200B;**[!UICONTROL Data filtering]**&#x200B;步骤。

   添加筛选条件以仅收集链接到营销活动的投放。

   此过滤器的语法如下所示：“促销活动”链接的外键大于0”。

   ![](assets/reporting_quick_start_query_filter.png)

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;保存这些条件，然后单击&#x200B;**[!UICONTROL Ok]**&#x200B;关闭查询编辑器。

### 步骤3:创建第一页 {#step-3--create-the-first-page}

在此步骤中，我们将配置报表的第一页。 要配置它，请应用以下步骤：

1. 打开&#x200B;**[!UICONTROL Page]**&#x200B;活动并输入其标题，例如，在此例中，**投放**。

   ![](assets/s_advuser_report_listgroup_003.png)

1. 通过工具栏插入具有组的列表并输入其标签，例如：每个营销活动的投放列表。

   ![](assets/s_advuser_report_listgroup_004.png)

1. 单击&#x200B;**[!UICONTROL Table data XPath...]**&#x200B;链接并选择投放链接，即`[query/delivery]`。

   ![](assets/s_advuser_report_listgroup_005.png)

1. 单击&#x200B;**[!UICONTROL Data]**&#x200B;选项卡并更改表的布局：在右侧添加三列。

   ![](assets/s_advuser_report_listgroup_006.png)

1. 添加群组。

   ![](assets/s_advuser_report_listgroup_008.png)

   利用此组，可对营销活动及其链接的投放进行分组。

1. 在组窗口中，引用“Campaign”链接&#x200B;**的**&#x200B;外键并关闭窗口。

   ![](assets/s_advuser_report_listgroup_007.png)

1. 编辑组标题的第一个单元格，并将促销活动的&#x200B;**[!UICONTROL Label]**&#x200B;字段作为表达式插入。

   ![](assets/s_advuser_report_listgroup_009.png)

1. 编辑详细信息行的第二个单元格，并选择投放&#x200B;**[!UICONTROL Label]**。

   ![](assets/s_advuser_report_listgroup_011.png)

1. 编辑此单元格的格式并打开&#x200B;**[!UICONTROL Click]**&#x200B;选项卡。 配置适当的选项，以便当用户单击投放的名称时，该投放会在同一窗口中打开。

   ![](assets/s_advuser_report_listgroup_0111.png)

   要执行此操作，请选择&#x200B;**[!UICONTROL Next page]**&#x200B;类型操作，然后选择&#x200B;**[!UICONTROL In the same window]**&#x200B;作为打开选项。

   ![](assets/s_advuser_report_listgroup_0112.png)

1. 在窗口的下部，单击&#x200B;**[!UICONTROL Add]** ，并指定与投放主键别名匹配的&#x200B;**`/vars/selectedDelivery`**&#x200B;路径和&#x200B;**[!UICONTROL @deliveryId]**&#x200B;表达式（在之前创建的查询中定义）。 此公式允许您访问所选投放。

   ![](assets/s_advuser_report_listgroup_010.png)

1. 编辑组页脚行的第二个单元格，并输入&#x200B;**[!UICONTROL Total per campaign]**&#x200B;作为标签。

   ![](assets/s_advuser_report_listgroup_012.png)

1. 编辑组标题行的第三个单元格，并输入&#x200B;**[!UICONTROL Number of messages sent]**&#x200B;作为标签。

   ![](assets/s_advuser_report_listgroup_013.png)

   此信息与列标题一致。

1. 编辑详细信息行的第三个单元格，并选择已处理的消息指示器作为表达式。

   ![](assets/s_advuser_report_listgroup_014.png)

1. 编辑组页脚行的第三个单元格，选择已处理的投放指示器，并将&#x200B;**[!UICONTROL Sum]**&#x200B;聚合应用于该单元格。

   ![](assets/s_advuser_report_listgroup_015.png)

1. 编辑详细信息行的第四个单元格，并选择&#x200B;**错误投放错误率**&#x200B;作为表达式。

   ![](assets/s_advuser_report_listgroup_016.png)

1. 选择此单元格以显示表示投放错误率的值栏。

   要实现此目的，请访问单元格格式，然后转到&#x200B;**[!UICONTROL More]**&#x200B;选项卡。 在下拉列表中选择&#x200B;**[!UICONTROL Value bar]**&#x200B;条目，然后选择&#x200B;**[!UICONTROL Hide the cell value]**&#x200B;选项。

   ![](assets/s_advuser_report_listgroup_023.png)

   您现在可以查看报告的呈现。 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡并选择&#x200B;**[!UICONTROL Global]**&#x200B;选项：这会显示链接到营销活动的Adobe Campaign数据库中所有投放的列表。

   ![](assets/s_advuser_report_listgroup_025.png)

   我们建议使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，以确保正确选择和配置表中的数据。 完成此操作后，您可以继续设置表格格式。

1. 将&#x200B;**[!UICONTROL Bold]**&#x200B;样式应用于显示每个促销活动的总数和处理的消息总数的单元格。

   ![](assets/s_advuser_report_listgroup_024.png)

1. 单击组标题行（显示促销活动名称的单元格）的第1个单元格，然后选择&#x200B;**[!UICONTROL Edit > Merge to right]**。

   ![](assets/s_advuser_report_listgroup_026.png)

   合并组标题行的前两个单元格将重新调整营销活动标题和链接到该标题的投放列表。

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >我们建议在生成报表之前等待合并单元格，因为合并是不可逆的。

### 第4步 — 创建第二个查询 {#step-4---create-the-second-query}

我们希望添加第二个查询和第二个页面，以在报表用户单击某个投放时显示投放的详细信息。 添加查询之前，请编辑您创建的页面并启用传出过渡，以便将其链接到查询。

1. 在&#x200B;**[!UICONTROL Page]**&#x200B;活动之后添加新查询，并编辑其架构：选择&#x200B;**[!UICONTROL Recipient delivery logs]**&#x200B;架构。

   ![](assets/reporting_quick_start_query-2.png)

1. 编辑查询并定义输出列。 要显示每个电子邮件域的投放数，您需要：

   * 计算主键值的总和以计算投放日志的数量：

      ![](assets/reporting_quick_start_query-2_count.png)

   * 收集有关此字段的收件人电子邮件域和组信息：要执行此操作，请在域名列中选择&#x200B;**[!UICONTROL Group]**&#x200B;选项。

   ![](assets/reporting_quick_start_query-2_filter.png)

   将以下别名链接到字段：

   * count(primary key):**@count**
   * 电子邮件域（收件人）：**@domain**

      ![](assets/reporting_quick_start_query-2_alias.png)


1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;按钮两次：这会将您转到&#x200B;**[!UICONTROL Data filtering]**&#x200B;步骤。

   添加筛选条件以仅收集链接到选定投放的信息。

   语法如下所示：“Delivery”链接的外键等于设置`$([vars/selectedDelivery])`的值

   ![](assets/s_advuser_report_listgroup_017.png)

1. 紧跟第二个查询后，关闭查询配置窗口并向图表中添加一个页面。

### 第5步 — 创建第二页 {#step-5---create-the-second-page}

1. 编辑页面并输入其标签：**电子邮件域**。
1. 取消选中&#x200B;**[!UICONTROL Enable output transitions]**&#x200B;选项：这是报表的最后一页，之后不会有其他活动。

   ![](assets/s_advuser_report_listgroup_028.png)

1. 使用右键单击菜单通过组添加新列表，并将其调用为&#x200B;**每个收件人的电子邮件域**。
1. 单击&#x200B;**[!UICONTROL Table data XPath...]**&#x200B;并选择&#x200B;**[!UICONTROL Recipient delivery logs]**&#x200B;链接。

   ![](assets/s_advuser_report_listgroup_029.png)

1. 在&#x200B;**[!UICONTROL Data]**&#x200B;选项卡中，按如下方式调整表：

   * 在右侧添加两列。
   * 在明细行的第一个单元格中，添加&#x200B;**[!UICONTROL rowNum()-1]**&#x200B;表达式以计算行数。 然后，更改单元格的格式：在&#x200B;**[!UICONTROL Extra]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Color tab]**&#x200B;并单击&#x200B;**[!UICONTROL Ok]**。

      ![](assets/s_advuser_report_listgroup_018.png)

      此配置将允许您使用表作为图表的标题。

   * 在详细信息行的第二个单元格中，添加&#x200B;**[!UICONTROL Email domain(Recipient)]**&#x200B;表达式。
   * 在详细信息行的第三个单元格中，添加&#x200B;**[!UICONTROL count(primary key)]**&#x200B;表达式。

   ![](assets/s_advuser_report_listgroup_019.png)

1. 使用右键单击菜单向页面添加饼图，并为其分配&#x200B;**Email domains**&#x200B;标签。 有关更多信息，请参阅[图表类型和变体](../../reporting/using/creating-a-chart.md#chart-types-and-variants)。
1. 单击&#x200B;**[!UICONTROL Variants]**&#x200B;链接并取消选择&#x200B;**[!UICONTROL Display label]**&#x200B;和&#x200B;**[!UICONTROL Display caption]**&#x200B;选项。
1. 检查是否未配置值排序。 如需详细信息，请参阅[此部分](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report)。

   ![](assets/s_advuser_report_listgroup_0191.png)

1. 在&#x200B;**[!UICONTROL Data]**&#x200B;选项卡中，更改数据源：从下拉列表中选择&#x200B;**[!UICONTROL Context data]**。

   ![](assets/s_advuser_report_listgroup_020.png)

1. 然后，单击&#x200B;**[!UICONTROL Advanced settings]**&#x200B;并选择指向收件人投放日志的链接。

   ![](assets/s_advuser_report_listgroup_0201.png)

1. 在&#x200B;**[!UICONTROL Chart type]**&#x200B;部分中，选择&#x200B;**[!UICONTROL Email domain]**&#x200B;变量。
1. 然后，添加要执行的计算：选择总和作为运算符。

   ![](assets/s_advuser_report_listgroup_0202.png)

1. 单击&#x200B;**[!UICONTROL Detail]**&#x200B;按钮以选择计数将涉及的字段，然后关闭配置窗口。

   ![](assets/s_advuser_report_listgroup_030.png)

1. 保存报表。

   您的页面现已配置完成。

### 第6步 — 查看报表 {#step-6---viewing-the-report}

要查看此配置的结果，请单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，然后选择&#x200B;**[!UICONTROL Global]**&#x200B;选项。

报告的第一页详细列出了数据库中包含的所有投放的列表。

![](assets/s_advuser_report_listgroup_021.png)

如果单击其中一个投放的链接，则会显示该投放的电子邮件域细分图表。 您现在位于报表的第二页，可以通过单击相应的按钮返回到上一页。

![](assets/s_advuser_report_listgroup_022.png)

## 创建划分表或数据透视表 {#creating-a-breakdown-or-pivot-table}

利用此类型的表，可显示对数据库中数据计算的统计信息。

这些类型的报表的配置与描述性分析向导所使用的报表类似。 有关详细信息，请参见[此页面](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template)。

有关创建数据透视表的更多信息，请参阅[此部分](../../reporting/using/using-cubes-to-explore-data.md)。
