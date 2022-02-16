---
product: campaign
title: 监控技术工作流
description: 监控技术工作流
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
source-git-commit: 1a4fd75a90667e57149772497a7b1bd14b251db3
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 6%

---

# 监控技术工作流 {#monitoring-technical-workflows}

![](../../assets/common.svg)

需要监控技术工作流，并在其失败时采取相应的操作。

有关监控不同Campaign流程的其他方法，请参见 [本页](../../production/using/monitoring-guidelines.md).

## 实例监控仪表板 {#instance-monitoring-dashboard}

可通过 **[!UICONTROL Monitoring]** 选项卡。

![](assets/monitoring_technical_workflows1.png)

在“System Indicators（系统指示器）”和核心文件下，检查没有指示器以红色突出显示。 如果出现这种情况，但有些情况确实如此，您应该：

* 检查必要的进程是否始终运行，
* 检查所有流程都不太旧，
* 检查不同进程的日志文件中是否不包含警告和重复错误。

## 技术工作流 {#technical-workflows}

技术工作流可从 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

根据技术工作流，请按照下面详述的步骤确保一切正常运行。

要更好地了解每个技术工作流应该执行的操作，请参阅此 [部分](about-technical-workflows.md).

对于 **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. 检查 **[!UICONTROL Database Cleanup]** 工作流每天成功运行并完成。 有关更多信息，请参阅此[页面](../../production/using/database-cleanup-workflow.md)..
1. 查看日志，验证经过的时间是否随时间相对恒定，并且不会干扰其他工作流。

对于 **[!UICONTROL Tracking workflow (‘tracking’)]**:

检查跟踪工作流是否按计划运行（默认为每小时一次），以及日记帐是否不会突出显示重复错误。 有关更多信息，请参阅此](delivery.md)章节[。

对于 **[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. 检查 **[!UICONTROL Deliverability update]** 工作流每天成功运行并完成。
1. 在日志中验证规则是否定期更新。

对于 **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. 查看位于 **[!UICONTROL Campaign process]** 文件夹。 有关详细信息，请参见此 [ 页面](about-technical-workflows.md)。
1. 检查工作流是否按计划运行，以及日记帐是否不会突出显示重复错误。

## 工作流监督 {#workflow-supervision}

的 **[!UICONTROL Workflow supervisors]** 组应包含需要随时了解故障以及哪些人可以及时采取行动的运算符。

![](assets/monitoring_technical_workflows3.png)

出现问题时，应生成警报并将其发送到正确的组。

确保每个操作员都具有有效的电子邮件地址。

为保持平台工作正常而应运行的任何工作流（例如每日数据导入）都应声明为“生产”（复选框），并以粗体显示。

## 工作流维护列表 {#workflow-maintenance-list}

所有自定义技术工作流都应记录在包含以下内容的工作表中：

* 工作流的名称和位置。
* 目的。
* 计划和依赖关系。
* 负责监控的操作员。
* 有关出错时应如何操作的说明。

![](assets/monitoring_technical_workflows4.png)

## 监控的规划和自动化 {#planning-and-automation-of-monitoring}

规划工作流监控可提高其效率。 某些任务需要每天执行，而其他任务则可以每周或每月执行。

在由重复项命名并按执行计划排序的文件夹中设置工作流，可提高监控效率。

自动监控可减少资源开销并确保任务以适当的频率进行计划。

您可以构建监控工作流，以在某些任务失败或关键表过大时发送电子邮件。

您可以创建一个视图，以便监控功能区域或系统范围内的所有工作流。

您还可以使用Adobe Campaign作业或报表功能按需构建文档，该文档始终是最新的。
