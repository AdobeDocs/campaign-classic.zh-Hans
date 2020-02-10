---
title: 报告操作
seo-title: 报告操作
description: 报告操作
seo-description: null
page-status-flag: never-activated
uuid: 7f9d99ab-ce19-46dd-bbf0-79de348d38fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 3b9c138e-8f7f-4ee1-9baa-328848d01d3a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# 报告操作{#actions-on-reports}

在查看报表时，工具栏允许您执行若干操作。 下文详述。

![](assets/s_ncs_advuser_report_wizard_2.png)

通过工具栏可以导出、打印、存档或在Web浏览器中显示报表。

![](assets/s_ncs_advuser_report_wizard_04.png)

## 导出报告 {#exporting-a-report}

从下拉列表中选择要将报表导出到的格式。 （.xls、.pdf或。ods）。

![](assets/s_ncs_advuser_report_wizard_06.png)

当报表包含多个页面时，您需要对每个页面重复此操作。

您可以配置报表，以便以PDF、Excel或OpenOffice格式导出。 打开Adobe Campaign浏览器并选择相关报告。

导出选项可通过报 **[!UICONTROL Page]** 告的活动在选项卡中访 **[!UICONTROL Advanced]** 问。

更改和的设 **[!UICONTROL Paper]** 置以 **[!UICONTROL Margins]** 满足您的需求。 您也只能授权导出PDF格式的页面。 要执行此操作，请取消选中 **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** 选项。

![](assets/s_ncs_advuser_report_wizard_021.png)

### 导出到Microsoft Excel {#exporting-into-microsoft-excel}

对于 **[!UICONTROL List with group]** 要导出到Excel的类型报表，有以下建议和限制：

* 这些报告不得包含任何空行。

   ![](assets/export_limitations_remove_empty_line.png)

* 列表的图例必须隐藏。

   ![](assets/export_limitations_hide_label.png)

* 报告不必使用在单元格级别定义的特定格式。 最好使用表 **[!UICONTROL Form rendering]** 中单元格的格式。 可 **[!UICONTROL Form rendering]** 通过访问 **[!UICONTROL Administration > Configuration > Form rendering]**。
* 我们不建议插入HTML内容。
* 如果报表包含多个表、图表等。 类型元素，它们将导出到另一个下方。
* 可以强制单元格中的回车符：此配置将保留在Excel中。 有关详细信息，请参阅此定 [义单元格格式](../../reporting/using/creating-a-table.md#defining-cell-format)。

### 推迟出口 {#postpone-the-export}

您可以推迟导出报告，例如等待异步调用。 为此，请在页面的初始化脚本中输入以下参数：

```
document.nl_waitBeforeRender = true;
```

要激活导出并开始转换为PDF，请使用 **document.nl_renderToPdf()函数（不带任何参数）** 。

### 内存分配 {#memory-allocation}

导出某些大型报告时，可能会发生内存分配错误。

在某些情况下， **serverConf.xml配置文件中指示的JavaScript的默认值** maxMB **(托管实例的SKMS** ) **** 设置为64 MB。 如果在导出报告时遇到内存不足的问题，建议将此数字增加到512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

要应用对配置所做的更改，需 **要重新启动Nlserver** 服务。

要进一步了解 **serverConf.xml文件** ，请参 [阅本节](../../production/using/configuration-principle.md)。

要进一步了解Nlserver服务 **，请参** 阅本节 [](../../production/using/administration.md)。

## 打印报告 {#printing-a-report}

您可以打印报表：要执行此操作，请单击打印机图标：这将打开对话框。

为获得更好的效果，请编辑Internet explorer打印选项并选择 **[!UICONTROL Print background colors and images]**。

![](assets/s_ncs_advuser_report_print_options.png)

## 创建报告存档 {#creating-report-archives}

通过存档报表，您可以创建报表在不同时间段的视图，例如显示给定时间段的统计信息。

要创建存档，请打开相关报告，然后单击相应的图标。

![](assets/s_ncs_advuser_report_wizard_07.png)

要显示或隐藏现有存档，请单击显示／隐藏图标。

![](assets/s_ncs_advuser_report_history_06.png)

存档日期显示在显示／隐藏图标下。 单击存档以查看它。

![](assets/s_ncs_advuser_report_history_04.png)

可以删除报告存档。 为此，请转到存储报告的Adobe Campaign节点。 单击选 **[!UICONTROL Archives]** 项卡，选择要删除的选项卡，然后单击 **[!UICONTROL Delete]**。

![](assets/s_ncs_advuser_report_history_01.png)

