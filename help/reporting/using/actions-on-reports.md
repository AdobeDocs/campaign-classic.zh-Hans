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

您可以配置报表，以将其以PDF、Excel或OpenOffice格式导出。 打开Adobe Campaign资源管理器并选择相关的报表。

可通过报表&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡的&#x200B;**[!UICONTROL Page]**&#x200B;活动访问导出选项。

根据需要更改&#x200B;**[!UICONTROL Paper]**&#x200B;和&#x200B;**[!UICONTROL Margins]**&#x200B;的设置。 您还可以仅授权导出PDF格式的页面。 要执行此操作，请取消选中&#x200B;**[!UICONTROL Activate OpenOffice/Microsoft Excel export]**&#x200B;选项。

![](assets/s_ncs_advuser_report_wizard_021.png)

### 导出到Microsoft Excel {#exporting-into-microsoft-excel}

对于&#x200B;**[!UICONTROL List with group]**&#x200B;类型要导出到Excel的报表，将应用以下建议和限制：

* 这些报表不得包含任何空行。

   ![](assets/export_limitations_remove_empty_line.png)

* 列表的图例必须隐藏。

   ![](assets/export_limitations_hide_label.png)

* 报表不必使用在单元格级别定义的特定格式。 最好使用&#x200B;**[!UICONTROL Form rendering]**&#x200B;定义表中单元格的格式。 可通过&#x200B;**[!UICONTROL Administration > Configuration > Form rendering]**&#x200B;访问&#x200B;**[!UICONTROL Form rendering]**。
* 我们不建议插入HTML内容。
* 如果报表包含多个表、图表等 类型元素，它们将导出一个，而另一个将导出。
* 可以在单元格中强制返回回车符：此配置将保留在Excel中。 有关更多信息，请参阅此[定义单元格格式](../../reporting/using/creating-a-table.md#defining-cell-format)。

### 推迟出口 {#postpone-the-export}

例如，您可以推迟导出报表，以等待异步调用。 要实现此目的，请在页面的初始化脚本中输入以下参数：

```
document.nl_waitBeforeRender = true;
```

要激活导出并开始转换为PDF，请使用&#x200B;**document.nl_renderToPdf()**&#x200B;函数，而不使用任何参数。

### 内存分配 {#memory-allocation}

在导出某些大型报告时，可能会出现内存分配错误。

在某些情况下，在&#x200B;**serverConf.xml**&#x200B;配置文件中指示的JavaScript的默认值&#x200B;**maxMB**（托管实例的&#x200B;**SKMS**）设置为64 MB。 如果在导出报告时遇到内存不足的错误，建议将此数字增加到512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

要应用对配置所做的更改，需要重新启动&#x200B;**nlserver**&#x200B;服务。

要详细了解&#x200B;**serverConf.xml**&#x200B;文件，请参阅[此部分](../../production/using/configuration-principle.md)。

要详细了解&#x200B;**nlserver**&#x200B;服务，请参阅[此部分](../../production/using/administration.md)。

## 打印报表 {#printing-a-report}

您可以打印报表：要执行此操作，请单击打印机图标：这将打开对话框。

为了获得更好的结果，请编辑Internet Explorer打印选项，然后选择&#x200B;**[!UICONTROL Print background colors and images]**。

![](assets/s_ncs_advuser_report_print_options.png)

## 创建报告存档 {#creating-report-archives}

通过存档报表，您可以创建报表在不同时段的视图，例如显示给定时间段的统计信息。

要创建存档，请打开相关报表并单击相应的图标。

![](assets/s_ncs_advuser_report_wizard_07.png)

要显示或隐藏现有存档，请单击显示/隐藏图标。

![](assets/s_ncs_advuser_report_history_06.png)

存档日期显示在显示/隐藏图标下。 单击存档以查看。

![](assets/s_ncs_advuser_report_history_04.png)

可以删除报表存档。 为此，请转到存储报表的Adobe Campaign节点。 单击&#x200B;**[!UICONTROL Archives]**&#x200B;选项卡，选择要删除的选项卡，然后单击&#x200B;**[!UICONTROL Delete]**。

![](assets/s_ncs_advuser_report_history_01.png)
