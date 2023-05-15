---
product: campaign
title: 工作流执行
description: 工作流执行
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---

# 工作流执行{#workflow-execution}



以下部分介绍与工作流执行相关的常见问题以及如何对其进行故障诊断的信息。

有关工作流的更多信息，请参阅以下章节：

* [关于工作流](../../workflow/using/about-workflows.md)
* [启动工作流](../../workflow/using/starting-a-workflow.md)
* [工作流生命周期](../../workflow/using/workflow-life-cycle.md)
* [使用工作流时的最佳实践](../../workflow/using/workflow-best-practices.md)

## 在营销活动中尽快开始 {#start-as-soon-as-possible-in-campaigns}

在某些情况下，从营销活动执行的工作流在单击 **[!UICONTROL Start]** 按钮。 它不会开始，而是会进入“尽快开始”状态。

此问题的原因可能有多种，请按照以下步骤进行解决：

1. 检查 [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) 技术工作流状态。 此工作流管理营销活动内的作业或工作流。 如果失败，则会导致工作流不启动/停止。 重新启动它以继续运行营销活动工作流。

   有关技术工作流监控的更多信息，请参阅 [本页](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >重新启动工作流后，请确保执行挂起的任务(右键单击 **[!UICONTROL Scheduler]** 活动/ **[!UICONTROL Execute pending task(s) now]**)，以检查它在任何活动上是否再次失败。

   如果工作流仍然失败，请检查审核日志中是否存在特定错误，并进行相应的故障诊断，然后再次重新启动工作流。

1. 检查 **[!UICONTROL wfserver]** 模块状态(在 **[!UICONTROL Monitoring]** 选项卡，可从Campaign Classic主页访问(请参阅 [监控流程](../../production/using/monitoring-processes.md))。 此过程负责运行所有工作流。

   管理员用户还可以检查 **wfserver@`<instance>`** 在主应用程序服务器上使用以下命令启动模块。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   如果模块未运行，请联系Adobe客户关怀团队。 如果您已安装内部部署，则管理员用户必须使用以下命令重新启动该服务。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >替换 **`<instancename>`** ，其名称为实例（生产、开发等）。 实例名称通过配置文件进行标识：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有关如何重新启动模块的更多信息，请参阅 [此部分](../../production/using/usual-commands.md#module-launch-commands).

1. 检查 **运行的营销活动进程数** 实例上的值大于阈值。 存在由 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 选项，可同时在实例上运行多少个营销活动进程。 达到此限制后，只要运行的工作流数量超过限制，工作流就会保持“尽快启动”状态。

   要解决此问题，请停止不需要的工作流并删除失败的投放。 如果达到阈值，则允许运行新进程。

   要检查您的实例运行的工作流数量，我们建议使用预定义视图，该视图默认可在 **[!UICONTROL Administration]** / **[!UICONTROL Audit]** 文件夹。 有关详细信息，请参见[此页面](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)。

   >[!IMPORTANT]
   >
   >将 **[!UICONTROL NmsOperation_LimitConcurrency]** 选项阈值可能会导致实例出现性能问题。 无论如何，请勿自行执行此操作，并联系您的Adobe Campaign联系人。

有关如何监控工作流的更多信息，请参阅 [此部分](../../workflow/using/monitoring-workflow-execution.md).

## 开始进行 {#start-in-progress}

如果工作流未执行且其状态为 **开始进行**，这可能意味着未启动工作流模块。

要选中此复选框并在必要时启动模块，请应用以下步骤：

1. 检查 **[!UICONTROL wfserver]** 模块状态(在 **[!UICONTROL Monitoring]** 选项卡，可从Campaign Classic主页访问(请参阅 [监控流程](../../production/using/monitoring-processes.md))。

   管理员用户还可以检查 **wfserver@`<instance>`** 在主应用程序服务器上使用以下命令启动模块。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   有关如何监视模块的详细信息，请参阅 [此部分](../../production/using/usual-commands.md#monitoring-commands-).

1. 如果模块未运行，请联系Adobe客户关怀团队。 如果您已安装内部部署，则管理员必须使用以下命令重新启动该安装。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >替换 **`<instancename>`** ，其名称为实例（生产、开发等）。 实例名称通过配置文件进行标识：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有关如何重新启动模块的更多信息，请参阅 [此部分](../../production/using/usual-commands.md#module-launch-commands).

## 失败的工作流 {#failed-workflow}

如果工作流失败，请执行以下步骤：

1. 检查工作流日记帐。 有关更多信息，请参阅 [监控工作流执行](../../workflow/using/monitoring-workflow-execution.md) 和 [显示日志](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 中。
1. 监测技术工作流. 有关更多信息，请参阅 [此部分](../../workflow/using/monitoring-technical-workflows.md).
1. 查找单个工作流活动的失败。
