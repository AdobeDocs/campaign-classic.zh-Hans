---
product: campaign
title: 对报告执行操作
description: 对报告执行操作
feature: Reporting, Monitoring
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 3%

---

# 对报告执行操作{#actions-on-reports}



在查看报表时，您可以通过工具栏执行特定数量的操作。 下文将详细介绍这些内容。

![](assets/s_ncs_advuser_report_wizard_2.png)

例如，您可以通过工具栏在Web浏览器中导出、打印、存档或显示报表。

![](assets/s_ncs_advuser_report_wizard_04.png)

## 导出报告 {#exporting-a-report}

从下拉列表中选择要将报表导出到的格式。 (.xls、.pdf或.ods)。

![](assets/s_ncs_advuser_report_wizard_06.png)

当报表包含多个页面时，您需要为每个页面重复此操作。

您可以配置报表，以将其导出为PDF、Excel或OpenOffice格式。 打开Adobe Campaign资源管理器并选择相关的报表。

导出选项可通过报告的&#x200B;**[!UICONTROL Page]**&#x200B;活动（在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中）访问。

更改&#x200B;**[!UICONTROL Paper]**&#x200B;和&#x200B;**[!UICONTROL Margins]**&#x200B;的设置以满足您的需要。 您还可以仅授权以PDF格式导出页面。 为此，请取消选中&#x200B;**[!UICONTROL Activate OpenOffice/Microsoft Excel export]**&#x200B;选项。

![](assets/s_ncs_advuser_report_wizard_021.png)

### 导出到Microsoft Excel {#exporting-into-microsoft-excel}

对于要导出到Excel的&#x200B;**[!UICONTROL List with group]**&#x200B;类型报表，适用以下建议和限制：

* 这些报表不得包含任何空行。

  ![](assets/export_limitations_remove_empty_line.png)

* 列表的图例必须隐藏。

  ![](assets/export_limitations_hide_label.png)

* 报表不必使用在单元格级别定义的特定格式。 最好使用&#x200B;**[!UICONTROL Form rendering]**&#x200B;来定义表中单元格的格式。 可以通过&#x200B;**[!UICONTROL Administration > Configuration > Form rendering]**&#x200B;访问&#x200B;**[!UICONTROL Form rendering]**。
* 我们不建议插入HTML内容。
* 如果报告包含多个表格、图表等， 键入元素，它们将被一个导出到另一个下。
* 您可以在单元格中强制回车：此配置将保留在Excel中。 如需详细信息，请参阅[此小节](../../reporting/using/creating-a-table.md#defining-cell-format)。

### 延迟导出 {#postpone-the-export}

例如，您可以推迟导出报表，以等待异步调用。 为此，请在页面的初始化脚本中输入以下参数：

```
document.nl_waitBeforeRender = true;
```

要激活导出并开始转换为PDF，请使用不带任何参数的&#x200B;**document.nl_renderToPdf()**&#x200B;函数。

### 内存分配 {#memory-allocation}

导出某些大型报告时，可能会发生内存分配错误。

在某些实例中，**serverConf.xml**&#x200B;配置文件中指示的JavaScript的默认值&#x200B;**maxMB** （**SKMS**&#x200B;对于托管实例）设置为64 MB。 如果在导出报告时遇到内存不足错误，建议将此数字增加到512 MB：

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

若要应用对配置所做的更改，需要重新启动&#x200B;**nlserver**&#x200B;服务。

要了解有关&#x200B;**serverConf.xml**&#x200B;文件的详细信息，请参阅[此部分](../../production/using/configuration-principle.md)。

要了解有关&#x200B;**nlserver**&#x200B;服务的更多信息，请参阅[此部分](../../production/using/administration.md)。

## 打印报表 {#printing-a-report}

您可以打印报告：要执行此操作，请单击打印机图标：这将打开对话框。

为了获得更好的结果，请编辑Explorer打印选项并选择&#x200B;**[!UICONTROL Print background colors and images]**。

![](assets/s_ncs_advuser_report_print_options.png)

## 创建报告存档 {#creating-report-archives}

通过存档报表，您可以创建各个时段的报表视图，例如，显示给定时段的统计信息。

要创建存档，请打开相关的报告，然后单击相应的图标。

![](assets/s_ncs_advuser_report_wizard_07.png)

要显示或隐藏现有存档，请单击显示/隐藏图标。

![](assets/s_ncs_advuser_report_history_06.png)

存档日期显示在显示/隐藏图标下。 单击归档文件以查看它。

![](assets/s_ncs_advuser_report_history_04.png)

可以删除报告存档。 为此，请转到存储报告的Adobe Campaign节点。 单击&#x200B;**[!UICONTROL Archives]**&#x200B;选项卡，选择要删除的选项卡，然后单击&#x200B;**[!UICONTROL Delete]**。

![](assets/s_ncs_advuser_report_history_01.png)
