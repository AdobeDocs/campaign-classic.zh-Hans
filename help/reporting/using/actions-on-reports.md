---
product: campaign
title: 对报告执行操作
description: 对报告执行操作
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---

# 对报告执行操作{#actions-on-reports}

![](../../assets/common.svg)

在查看报表时，您可以通过工具栏执行一定数量的操作。 下文详述了这些内容。

![](assets/s_ncs_advuser_report_wizard_2.png)

例如，您可以通过工具栏导出、打印、存档或在Web浏览器中显示报表。

![](assets/s_ncs_advuser_report_wizard_04.png)

## 导出报表 {#exporting-a-report}

从下拉列表中选择要将报表导出到的格式。 (.xls、.pdf或.ods)。

![](assets/s_ncs_advuser_report_wizard_06.png)

当报表包含多个页面时，您需要对每个页面重复该操作。

您可以配置报表，以便以PDF、Excel或OpenOffice格式导出报表。 打开Adobe Campaign资源管理器并选择相关的报表。

可通过 **[!UICONTROL Page]** 报告的活动， **[!UICONTROL Advanced]** 选项卡。

更改 **[!UICONTROL Paper]** 和 **[!UICONTROL Margins]** 来满足你的需要。 您还可以仅授权以PDF格式导出页面。 要执行此操作，请取消选中 **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** 选项。

![](assets/s_ncs_advuser_report_wizard_021.png)

### 导出到Microsoft Excel {#exporting-into-microsoft-excel}

对于 **[!UICONTROL List with group]** 键入要导出到Excel中的报表，则适用以下建议和限制：

* 这些报表不得包含任何空行。

   ![](assets/export_limitations_remove_empty_line.png)

* 列表的图例必须隐藏。

   ![](assets/export_limitations_hide_label.png)

* 报表不必使用在单元格级别定义的特定格式。 最好使用 **[!UICONTROL Form rendering]** 定义表中单元格的格式。 的 **[!UICONTROL Form rendering]** 可以通过 **[!UICONTROL Administration > Configuration > Form rendering]**.
* 我们不建议插入HTML内容。
* 如果报表包含多个表、图表等 类型元素，它们将导出一个，而另一个将导出。
* 可以在单元格中强制返回回车符：此配置将保留在Excel中。 有关更多信息，请参阅此 [定义单元格格式](../../reporting/using/creating-a-table.md#defining-cell-format).

### 推迟出口 {#postpone-the-export}

例如，您可以推迟导出报表，以等待异步调用。 要实现此目的，请在页面的初始化脚本中输入以下参数：

```
document.nl_waitBeforeRender = true;
```

要激活导出并开始转换为PDF，请使用 **document.nl_renderToPdf()** 函数。

### 内存分配 {#memory-allocation}

在导出某些大型报告时，可能会出现内存分配错误。

在某些情况下，默认值 **maxMB** (**SKMS** （对于托管实例） **serverConf.xml** 配置文件设置为64 MB。 如果在导出报告时遇到内存不足的错误，建议将此数字增加到512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

要应用对配置所做的更改，请 **nlserver** 需要重新启动服务。

要详细了解 **serverConf.xml** 文件，请参阅 [此部分](../../production/using/configuration-principle.md).

要详细了解 **nlserver** 服务，请参阅 [此部分](../../production/using/administration.md).

## 打印报表 {#printing-a-report}

您可以打印报表：要执行此操作，请单击打印机图标：这将打开对话框。

为了获得更好的结果，请编辑Internet Explorer打印选项，然后选择 **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## 创建报告存档 {#creating-report-archives}

通过存档报表，您可以创建报表在不同时段的视图，例如显示给定时间段的统计信息。

要创建存档，请打开相关报表并单击相应的图标。

![](assets/s_ncs_advuser_report_wizard_07.png)

要显示或隐藏现有存档，请单击显示/隐藏图标。

![](assets/s_ncs_advuser_report_history_06.png)

存档日期显示在显示/隐藏图标下。 单击存档以查看。

![](assets/s_ncs_advuser_report_history_04.png)

可以删除报表存档。 为此，请转到存储报表的Adobe Campaign节点。 单击 **[!UICONTROL Archives]** ，选择要删除的页面并单击 **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
