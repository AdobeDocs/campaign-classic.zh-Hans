---
solution: Campaign Classic
product: campaign
title: 创建表
description: 创建表
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2495'
ht-degree: 1%

---


# 创建表{#creating-a-table}

可向报表添加表以显示数据。 这可以是根据多维数据集度量创建的透视表、具有组的列表或包含值细分的表。

![](assets/s_advuser_report_page_activity_05.png)

## 创建组列表 {#creating-a-list-with-group}

通过 **[!UICONTROL List with group]** 类型表，可以对表中的数据进行分组，并生成其统计信息。 例如，您可以创建数据的合计和子合计。 每个组都有其自己的页眉、详细信息和页脚行。

>[!CAUTION]
>
>包 **[!UICONTROL Page]** 含表的活动前面必须有一个或 **[!UICONTROL Query]** 一个 **[!UICONTROL Script]** 活动，以收集要在报告中分析的数据。 有关这些活动的详细信息，请参 [阅收集数据以分析](../../reporting/using/collecting-data-to-analyze.md)[和脚本活动](../../reporting/using/advanced-functionalities.md#script-activity)。

### 工作原理 {#operating-principle}

您可能需要同时分析多个数据类别。 具有组的列表允许您合并数据并在同一表中创建有关不同组数据的统计信息。 为此，可在表中创建组。

在以下示例中，组显示活动库中的所有投放、每个投放和每个活动发送的消息数。

它允许您列表链接到该&#x200B;**[!UICONTROL Label (Campaign)]**&#x200B;活动的投放(活动&#x200B;**[!UICONTROL Label]** 列表)，还允许您计算每个投放发送的消息数(**[!UICONTROL Processed)]**&#x200B;在为每个活动添加消息之前)**[!UICONTROL Sum(@processed)]** 。

![](assets/s_advuser_ergo_listgroup_005.png)

### 实施步骤 {#implementation-steps}

下面提供了完整的实现示例： [用例：创建包含组列表的报表](#use-case--create-a-report-with-a-group-list)。

请注意以下步骤以创建“具有组的列表”类型表：

1. 转到报表图表并放置一个 **[!UICONTROL Query]** 活动。 请参阅 [收集数据以进行分析](../../reporting/using/collecting-data-to-analyze.md)。
1. 填写源表，并选择统计数据将涉及的表字段。
1. 在图 **[!UICONTROL Page]** 表中放置活动。 For more on this, refer to [Static elements](../../reporting/using/creating-a-new-report.md#static-elements).
1. 在页面中 **[!UICONTROL List with group]** 插入一个类型表。
1. 指定查询中作为数据源选择的数据路径或表。

   如果要稍后恢复源表中的字段并将其插入到表的单元格中，则此步骤是必需的。

1. 创建表及其内容。
1. 在选项卡中显示最终 **[!UICONTROL Preview]** 报告。 然后，您可以发布报告并根据需要将其导出为不同格式。 有关此问题的详细信息，请参 [阅导出报告](../../reporting/using/actions-on-reports.md#exporting-a-report)。

### 添加行和列 {#adding-lines-and-columns}

默认情况下， **[!UICONTROL List with group]** 类型表包括页眉、明细行和页脚行。

组本身包括页眉、详细信息和页脚行。

* **标题行**:此行允许您为表的列提供标题。

   ![](assets/s_advuser_ergo_listgroup_003a.png)

* **明细行**:此行包含统计值。

   ![](assets/s_advuser_ergo_listgroup_004.png)

* **页脚行**:此行允许您显示总值。

   ![](assets/s_advuser_ergo_listgroup_003.png)

可以添加行和列以满足您的需求。

该组可放置在表的任何行上，并包含其自己的页眉、详细信息和页脚行。

![](assets/s_advuser_ergo_listgroup_019.png)

**行和列**:要添加或删除行或列，请转到现有行或列，然后使用右键单击菜单。

![](assets/s_advuser_ergo_listgroup_006.png)

您添加的行的性质取决于光标的位置。 例如，要添加标题行，请将光标放在标题上，然后单击 **[!UICONTROL Add > A line above/below]**。

![](assets/s_advuser_ergo_listgroup_006a.png)

可通过项修改列的宽 **[!UICONTROL Column format]** 度。

**组**:要添加组，请转到行并在下拉菜单中选择匹配项。

![](assets/s_advuser_ergo_listgroup_007.png)

### 定义单元格内容 {#defining-cell-content}

要编辑表的单元格并定义其内容和格式，请转到该单元格并使用右键单击菜单。

使用菜 **[!UICONTROL Expression]** 单条目选择要显示的值。

![](assets/s_advuser_ergo_listgroup_010.png)

* 要将要直接分析的值插入表中，请在可用字段中选择它们。

   可用字段的列表与报表构造图表中表前查询的内容一致。

   ![](assets/s_advuser_ergo_listgroup_011.png)

* 输入单元格的标签，例如，标题标签。

   为此，请使用与将字段插入表达式库相同的过程，但不要选择字段。 Enter the label in the **[!UICONTROL Label]** field. 它将按原样显示。

* 计算聚合（平均值、和等） 并在单元格中显示。

   为此，请使用菜 **[!UICONTROL Aggregates]** 单条目并选择所需活动。

   ![](assets/s_advuser_ergo_listgroup_008.png)

### 定义单元格格式 {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

要定义单元格格式，菜单 **[!UICONTROL Cell format...]** 允许您访问选定单元格的所有可用格式选项。

这些选项使您能够个性化报表的最终呈现并更轻松地阅读信息。

将数据 **[!UICONTROL Carriage return]** 导出到Excel时，请使用此字段：选择 **[!UICONTROL Yes]** 值以强制回车。 此值将在导出时保留。 有关此问题的详细信息，请参 [阅导出报告](../../reporting/using/actions-on-reports.md#exporting-a-report)。

在窗 **[!UICONTROL Cell format]** 口中，您可以访问以下选项卡：

* 选项 **[!UICONTROL Value]** 卡
* 选项 **[!UICONTROL Borders]** 卡
* 选项 **[!UICONTROL Click]** 卡
* 选项 **[!UICONTROL Extra]** 卡

通过 **[!UICONTROL Value]** 该选项卡，您可以更改字体和各种值属性，或根据其性质定义格式。

![](assets/s_advuser_ergo_listgroup_009.png)

格式更改了数据显示：例如， **[!UICONTROL Number]**&#x200B;和 **[!UICONTROL Monetary]** 格 **[!UICONTROL Percentage]** 式允许您右对齐数字并显示小数点。

如何配置货币格式的示例：您可以指定值所表示的货币，选择是否分隔千位，以红色显示负值。 货币符号的位置取决于在其用户档案中定义的运算符的语言。

![](assets/s_advuser_ergo_listgroup_012.png)

日期配置示例：您可以选择是否显示时间。

![](assets/s_advuser_ergo_listgroup_013.png)

使用 **边框** 选项卡，可向表中的行和列添加边框。 在将大型报表导出到Excel时，向单元格添加边框可能会导致性能问题。

![](assets/s_advuser_ergo_listgroup_014.png)

如有必要，您可以在表模板()中定义&#x200B;**[!UICONTROL Administration > Configuration > Form rendering]** 边框。

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

通过 **[!UICONTROL Click]** 该选项卡，可在用户单击单元格或表格内容时定义操作。

在以下示例中，单击单元格中的值可显示报表的第二页：它将包含单元格中投放的信息。

![](assets/s_advuser_ergo_listgroup_015.png)

通过 **“额外** ”选项卡，您可以将可视内容链接到数据，如彩色标记或值栏。 当表在图表中显示为图例时，将使用彩色标记。 有关此的详细信息，请参阅实施示例： [第5步——创建第二页](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## 用例：创建包含组列表的报表 {#use-case--create-a-report-with-a-group-list}

在此示例中，我们将创建一个两页报表：第一页将包含列表、每个活动的投放总数以及发送的消息数。 投放名称将是可单击的链接，您可以转到报告的第二页，用表格和图表视图选定投放的每个电子邮件域的投放细分。 在第二页上，表将用作图表的图例。

![](assets/reporting_quick_start_report-final.png)

### 第1步——创建报表 {#step-1---create-a-report}

创建与活动模式相关的新报告 **[!UICONTROL Campaigns (nms)]**。

![](assets/s_advuser_report_listgroup_001.png)

单击 **[!UICONTROL Save]** 以创建报告。

转到图表并添加用于设计报表内容的第一个组件：第一查询和第一页。

![](assets/reporting_quick_start_diagram.png)

### 第2步——创建第一个查询 {#step-2---create-the-first-query}

第一个查询允许您收集链接到每个活动的投放。 目标是显示链接到每个投放的Adobe Campaign库各个活动的报告。

多次-单击第一个查询进行编辑，然后应用以下步骤进行配置：

1. 开始，方法是更改应用查询源的模式:选择 **[!UICONTROL Deliveries (nms)]** 模式
1. 单击链 **[!UICONTROL Edit query]** 接并显示高级字段。

   ![](assets/reporting_quick_start_query-1.png)

1. 选择以下字段：

   * 投放标签，
   * 投放的主键，
   * 活动标签，
   * 已处理投放的指标，
   * 活动链的外键，
   * 错误率指示器。

   ![](assets/s_advuser_report_listgroup_002.png)

   将别名链接到每个字段：建议从将添加到报告第一页的表中选择数据。

   在本例中，我们将使用以下别名：

   * 标签： **@label**
   * 主键： **@deliveryId**
   * 标签(活动): **@label1**
   * 已处理： **@已处理**
   * “活动”（“id”字段）链接的外键： **@operationId**
   * 错误率： **@errorRatio**


1. 单击两 **[!UICONTROL Next]** 次按钮以转到该 **[!UICONTROL Data filtering]** 步骤。

   添加过滤条件以仅收集链接到投放的活动。

   此过滤器的语法如下：“‘活动’的外键大于0”。

   ![](assets/reporting_quick_start_query_filter.png)

1. 单 **[!UICONTROL Finish]** 击以保存这些条件，然 **[!UICONTROL Ok]** 后单击以关闭查询编辑器。

### 第3步：创建第一页 {#step-3--create-the-first-page}

在此步骤中，我们将配置报表的第一页。 要配置它，请应用以下步骤：

1. 打开 **[!UICONTROL Page]** 活动并输入其标题，例如 **投放** 。

   ![](assets/s_advuser_report_listgroup_003.png)

1. 通过工具栏插入具有组的列表并输入其标签，例如：列表每个活动的投放。

   ![](assets/s_advuser_report_listgroup_004.png)

1. 单击链 **[!UICONTROL Table data XPath...]** 接并选择投放链接，即 `[query/delivery]`.

   ![](assets/s_advuser_report_listgroup_005.png)

1. 单击选 **[!UICONTROL Data]** 项卡并更改表的布局：在右侧添加三列。

   ![](assets/s_advuser_report_listgroup_006.png)

1. 添加用户组。

   ![](assets/s_advuser_report_listgroup_008.png)

   通过此组，您可以将活动和链接到这些投放进行分组。

1. 在组窗口中，引用“ **活动”链接的外键** ，并关闭窗口。

   ![](assets/s_advuser_report_listgroup_007.png)

1. 编辑组标题的第一个单元格，并将 **[!UICONTROL Label]** 活动的字段插入为表达式。

   ![](assets/s_advuser_report_listgroup_009.png)

1. 编辑详细信息行的第二个单元格并选择投放 **[!UICONTROL Label]**。

   ![](assets/s_advuser_report_listgroup_011.png)

1. 编辑此单元格的格式并打开选 **[!UICONTROL Click]** 项卡。 配置适当的选项，当用户单击投放名称时，将在同一窗口中打开该选项。

   ![](assets/s_advuser_report_listgroup_0111.png)

   为此，请选择一个 **[!UICONTROL Next page]** 类型操作并选 **[!UICONTROL In the same window]** 择作为打开选项。

   ![](assets/s_advuser_report_listgroup_0112.png)

1. 在窗口的下半部分，单 **[!UICONTROL Add]** 击并指 **`/vars/selectedDelivery`** 定与以 **[!UICONTROL @deliveryId]** 前创建的查询中定义的投放主键的别名相匹配的路径和表达式。 此公式允许您访问所选投放。

   ![](assets/s_advuser_report_listgroup_010.png)

1. 编辑组页脚行的第二个单元格并输 **[!UICONTROL Total per campaign]** 入为标签。

   ![](assets/s_advuser_report_listgroup_012.png)

1. 编辑组标题行的第三个单元格并输 **[!UICONTROL Number of messages sent]** 入为标签。

   ![](assets/s_advuser_report_listgroup_013.png)

   此信息与列标题一致。

1. 编辑详细信息行的第三个单元格，并选择已处理的消息指示符作为表达式。

   ![](assets/s_advuser_report_listgroup_014.png)

1. 编辑组页脚行的第三个单元格，选择已处理的投放指示符并将聚合应 **[!UICONTROL Sum]** 用到它。

   ![](assets/s_advuser_report_listgroup_015.png)

1. 编辑详细信息行的第四个单元格，并选 **择错误投放错误率** 作为表达式。

   ![](assets/s_advuser_report_listgroup_016.png)

1. 选择此单元格可显示表示投放错误率的值栏。

   要执行此操作，请访问单元格格式，然后转到选 **[!UICONTROL More]** 项卡。 在下 **[!UICONTROL Value bar]** 拉列表中选择该条目，然后选择 **[!UICONTROL Hide the cell value]** 选项。

   ![](assets/s_advuser_report_listgroup_023.png)

   您现在可以视图报表的呈现。 单击选 **[!UICONTROL Preview]** 项卡并选择 **[!UICONTROL Global]** 选项：这将显示链接到某个活动的Adobe Campaign库中所有投放的列表。

   ![](assets/s_advuser_report_listgroup_025.png)

   我们建议使用 **[!UICONTROL Preview]** 选项卡来确保正确选择和配置表中的数据。 完成此操作后，您可以继续设置表格格式。

1. 将样 **[!UICONTROL Bold]** 式应用于显示每个活动的总数和所处理邮件总数的单元格。

   ![](assets/s_advuser_report_listgroup_024.png)

1. 单击组标题行(显示活动名称的单元格)的第1个单元格，然后选择 **[!UICONTROL Edit > Merge to right]**。

   ![](assets/s_advuser_report_listgroup_026.png)

   合并组标题行的前两个单元格将重新对齐活动标题和链接到它的投放的列表。

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >我们建议在合并单元格之前等待您的报告构建完成，因为合并是不可逆的。

### 第4步——创建第二个查询 {#step-4---create-the-second-query}

我们要添加第二个查询和第二个页面，以在报表用户单击时显示投放的详细信息。 在添加查询之前，请编辑已创建的页面并启用传出过渡，以将其链接到查询。

1. 在查询后添加新活动 **[!UICONTROL Page]** 并编辑其模式:选择 **[!UICONTROL Recipient delivery logs]** 模式

   ![](assets/reporting_quick_start_query-2.png)

1. 编辑查询并定义输出列。 要显示每个电子邮件域的投放数，您需要：

   * 计算主键的总和以计算投放日志数：

      ![](assets/reporting_quick_start_query-2_count.png)

   * 在此字段中收集收件人电子邮件域和组信息：为此，请在 **[!UICONTROL Group]** 域名列中选择选项。

   ![](assets/reporting_quick_start_query-2_filter.png)

   将以下别名链接到字段：

   * count(primary key): **@count**
   * 电子邮件域(收件人): **@域**

      ![](assets/reporting_quick_start_query-2_alias.png)


1. 单击按 **[!UICONTROL Next]** 钮两次：这会带你走上 **[!UICONTROL Data filtering]** 一步。

   添加过滤条件以仅收集链接到选定投放的信息。

   语法如下：“投放”链接的外键等于设置的值 `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. 关闭查询配置窗口，在第二个查询之后向图表添加一个页面。

### 第5步——创建第二页 {#step-5---create-the-second-page}

1. 编辑页面并输入其标签： **电子邮件域**。
1. 取消选中 **[!UICONTROL Enable output transitions]** 选项：这是报告的最后一页，后面不会有其他活动。

   ![](assets/s_advuser_report_listgroup_028.png)

1. 使用右键菜单为组添加新列表，并将其命名为每个收件人 **的电子邮件域**。
1. 单击该 **[!UICONTROL Table data XPath...]** 链接并选 **[!UICONTROL Recipient delivery logs]** 择链接。

   ![](assets/s_advuser_report_listgroup_029.png)

1. 在选项卡 **[!UICONTROL Data]** 中，按如下方式调整表格：

   * 在右侧添加两列。
   * 在明细行的第一个单元格中，添加 **[!UICONTROL rowNum()-1]** 表达式以计算行数。 然后更改单元格的格式：在选项卡 **[!UICONTROL Extra]** 中，选择 **[!UICONTROL Color tab]** 并单击 **[!UICONTROL Ok]**。

      ![](assets/s_advuser_report_listgroup_018.png)

      此配置将允许您使用表作为图表的题注。

   * 在详细信息行的第二个单元格中，添加 **[!UICONTROL Email domain(Recipient)]** 表达式。
   * 在详细信息行的第三个单元格中，添加 **[!UICONTROL count(primary key)]** 表达式。

   ![](assets/s_advuser_report_listgroup_019.png)

1. 使用右键单击菜单将饼图添加到页面，并为其分 **配“电子邮** 件域”标签。 有关详细信息，请参阅 [图表类型和变体](../../reporting/using/creating-a-chart.md#chart-types-and-variants)。
1. 单击链 **[!UICONTROL Variants]** 接并取消选择 **[!UICONTROL Display label]** 相应的 **[!UICONTROL Display caption]** 选项。
1. 检查是否未配置值排序。 如需详细信息，请参阅[此部分](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report)。

   ![](assets/s_advuser_report_listgroup_0191.png)

1. 在选项卡 **[!UICONTROL Data]** 中，更改数据源：从 **[!UICONTROL Context data]** 下拉列表中选择。

   ![](assets/s_advuser_report_listgroup_020.png)

1. 然后单 **[!UICONTROL Advanced settings]** 击并选择指向收件人投放日志的链接。

   ![](assets/s_advuser_report_listgroup_0201.png)

1. In the **[!UICONTROL Chart type]** section, select the **[!UICONTROL Email domain]** variable.
1. 然后添加要执行的计算：选择sum作为运算符。

   ![](assets/s_advuser_report_listgroup_0202.png)

1. 单击按 **[!UICONTROL Detail]** 钮以选择计数将涉及的字段，然后关闭配置窗口。

   ![](assets/s_advuser_report_listgroup_030.png)

1. 保存报告。

   您的页面现已配置。

### 第6步——查看报表 {#step-6---viewing-the-report}

要视图此配置的结果，请单击选 **[!UICONTROL Preview]** 项卡并选择 **[!UICONTROL Global]** 选项。

报告的第一页详细说明了列表库中包含的所有投放。

![](assets/s_advuser_report_listgroup_021.png)

如果单击其中一个投放的链接，则会显示该投放电子邮件域细分的图表。 您现在位于报表的第二页，可以单击相应按钮返回上一页。

![](assets/s_advuser_report_listgroup_022.png)

## 创建细分表或透视表 {#creating-a-breakdown-or-pivot-table}

此类型的表允许您显示针对数据库中数据计算的统计信息。

这些类型的报表的配置与描述性分析向导所用的配置类似。 有关详细信息，请参见[此页面](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template)。

有关创建透视表的详细信息，请参 [阅本节](../../reporting/using/using-cubes-to-explore-data.md)。
