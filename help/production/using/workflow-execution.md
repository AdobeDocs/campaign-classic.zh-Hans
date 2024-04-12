---
product: campaign
title: 工作流执行
description: 工作流执行
feature: Monitoring, Workflows
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# 工作流执行{#workflow-execution}



以下部分介绍了与工作流执行相关的常见问题以及如何对其进行疑难解答。

有关工作流的详细信息，请参阅以下章节：

* [关于工作流](../../workflow/using/about-workflows.md)
* [启动工作流](../../workflow/using/starting-a-workflow.md)
* [工作流生命周期](../../workflow/using/workflow-life-cycle.md)
* [使用工作流时的最佳实践](../../workflow/using/workflow-best-practices.md)

## 在活动中尽快开始 {#start-as-soon-as-possible-in-campaigns}

在某些情况下，从营销策划执行的工作流不会在单击 **[!UICONTROL Start]** 按钮。 它不会启动，而是进入“尽快启动”状态。

此问题可能由多种原因引起，请按照以下步骤解决该问题：

1. 查看 [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) 技术工作流状态。 此工作流用于管理营销活动中的作业或工作流。 如果失败，这将导致工作流无法启动/停止。 重新启动工作流可继续运行活动工作流。

   有关技术工作流监控的更多信息，请参阅 [此页面](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >重新启动工作流后，确保执行挂起的任务(右键单击 **[!UICONTROL Scheduler]** 活动/ **[!UICONTROL Execute pending task(s) now]**)，以检查它是否在任何活动中再次失败。

   如果工作流仍然失败，请检查审核日志中的特定错误，进行相应的故障诊断，然后再次重新启动工作流。

1. 查看 **[!UICONTROL wfserver]** 中的模块状态 **[!UICONTROL Monitoring]** 选项卡，可从Campaign Classic主页访问(请参阅 [监控流程](../../production/using/monitoring-processes.md))。 此进程负责运行所有工作流。

   管理员用户还可以检查 **wfserver@`<instance>`** 使用下面的命令在主应用程序服务器上启动模块。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   如果模块未运行，请联系Adobe客户关怀团队。 如果您的是内部部署安装，管理员用户必须使用以下命令重新启动服务。

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >替换 **`<instance-name>`** 使用实例的名称（生产、开发等）。 实例名称通过配置文件进行标识：
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   有关如何重新启动模块的更多信息，请参阅 [本节](../../production/using/usual-commands.md#module-launch-commands).

1. 检查 **运行的营销活动进程数** 实例上的大于阈值。 有一个由定义的限制 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 选项可以在该实例上并行运行多少个Campaign进程。 达到此限制后，只要正在运行的工作流数量超过限制，工作流就会一直处于“尽快启动”状态。

   要解决此问题，请停止不需要的工作流并删除失败的投放。 如果达到此阈值，则将允许运行新进程。

   要检查实例正在运行的工作流数量，我们建议使用预定义视图，默认情况下可在中访问这些视图。 **[!UICONTROL Administration]** / **[!UICONTROL Audit]** 文件夹。 有关详细信息，请参见[此页面](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)。

   >[!IMPORTANT]
   >
   >增加 **[!UICONTROL NmsOperation_LimitConcurrency]** 选项阈值可能会导致实例出现性能问题。 无论如何，请不要自行执行此操作，并联系您的Adobe Campaign联系人。

有关如何监控工作流的详细信息，请参阅 [本节](../../workflow/using/monitoring-workflow-execution.md).

## 开始进行中 {#start-in-progress}

如果工作流未执行，且其状态为 **开始进行中**，这可能意味着未启动工作流模块。

要选中此复选框，并在必要时启动模块，请应用以下步骤：

1. 查看 **[!UICONTROL wfserver]** 中的模块状态 **[!UICONTROL Monitoring]** 选项卡，可从Campaign Classic主页访问(请参阅 [监控流程](../../production/using/monitoring-processes.md))。

   管理员用户还可以检查 **wfserver@`<instance>`** 使用下面的命令在主应用程序服务器上启动模块。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   有关如何监视模块的详细信息，请参阅 [本节](../../production/using/usual-commands.md#monitoring-commands-).

1. 如果模块未运行，请联系Adobe客户关怀团队。 如果您的是内部部署安装，管理员必须使用以下命令将其重新启动。

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >替换 **`<instance-name>`** 使用实例的名称（生产、开发等）。 实例名称通过配置文件进行标识：
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   有关如何重新启动模块的更多信息，请参阅 [本节](../../production/using/usual-commands.md#module-launch-commands).

## 失败的工作流 {#failed-workflow}

如果工作流失败，请执行以下步骤：

1. 检查工作流日志。 有关详细信息，请参见 [监控工作流执行](../../workflow/using/monitoring-workflow-execution.md) 和 [显示日志](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 部分。
1. 监控技术工作流。 欲知详情，请参阅 [本节](../../workflow/using/monitoring-technical-workflows.md).
1. 查找单个工作流活动上的失败。
