---
title: 工作流执行
seo-title: 工作流执行
description: 工作流执行
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5a4ee9b14d4c77f74ff73209d4323bf4f1347155
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 3%

---


# 工作流执行{#workflow-execution}

以下部分介绍与工作流执行相关的常见问题以及如何解决这些问题。

有关工作流的详细信息，请参阅以下部分：

* [关于工作流](../../workflow/using/about-workflows.md)
* [启动工作流](../../workflow/using/starting-a-workflow.md)
* [工作流生命周期](../../workflow/using/workflow-life-cycle.md)
* [使用工作流时的最佳实践](../../workflow/using/workflow-best-practices.md)

## 开始在活动 {#start-as-soon-as-possible-in-campaigns}

在某些情况下，从活动执行的工作流在单击按钮时不会开始 **[!UICONTROL Start]** 。 它不是开始，而是进入“尽快开始”状态。

此问题有多种原因，请按照以下步骤解决：

1. 检查技术 [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) 工作流状态。 此工作流管理活动内的作业或工作流。 如果失败，将导致工作流不开始/停止。 重新启动它以恢复活动工作流的运行。

   有关技术工作流监视的详细信息，请 [参阅此页](../../workflow/using/monitoring-technical-workflows.md)。

   >[!NOTE]
   >
   >重新启动工作流后，请确保您执行待处理任务(右 **[!UICONTROL Scheduler]** 键单击活动 **[!UICONTROL Execute pending task(s) now]**/)，以检查它是否在任何活动上再次失败。

   如果工作流仍然失败，请检查审核日志中是否有特定错误，并进行相应的疑难解答，然后重新启动该工作流。

1. 检查选 **[!UICONTROL wfserver]** 项卡中的模 **[!UICONTROL Monitoring]** 块状态，可从Campaign Classic主页访问(请参 [阅监视进程](../../production/using/monitoring-processes.md))。 此过程负责运行所有工作流。

   管理员用户还可以使用以下 **命令检查`<instance>`** wfserver@module是否已在主应用程序服务器上启动。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   如果模块未运行，请与Adobe客户服务部门联系。 如果您有内部部署安装，管理员用户必须使用以下命令重新启动服务。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >替换 **`<instancename>`** 为实例的名称（生产、开发等）。 实例名称通过配置文件进行标识：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有关如何重新启动模块的详细信息，请参 [阅本节](../../production/using/usual-commands.md#module-launch-commands)。

1. 检查实 **例上运行的活动进** 程数是否大于阈值。 该选项对实例上可 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 以并行运行的活动进程数量定义了限制。 达到此限制后，只要运行的开始数超过该限制，工作流就会保持“尽快”状态。

   要解决此问题，请停止不需要的工作流并删除失败的投放。 如果达到阈值，则允许运行新进程。

   要检查实例运行的工作流数，我们建议使用预定义视图，默认情况下可在／文件夹中 **[!UICONTROL Administration]** 访 **[!UICONTROL Audit]** 问它。 有关详细信息，请参见[此页面](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)。

   >[!CAUTION]
   >
   >增加选 **[!UICONTROL NmsOperation_LimitConcurrency]** 项阈值可能会导致实例的性能问题。 无论如何，请勿自行执行此操作，并联系Adobe Campaign联系人。

有关如何监控工作流的详细信息，请参 [阅本节](../../workflow/using/monitoring-workflow-execution.md)。

## 开始进行中 {#start-in-progress}

如果工作流未执行且其状态 **正在开始**，这可能意味着工作流模块未启动。

要检查此项并在必要时开始模块，请应用以下步骤：

1. 检查选 **[!UICONTROL wfserver]** 项卡中的模 **[!UICONTROL Monitoring]** 块状态，可从Campaign Classic主页访问(请参 [阅监视进程](../../production/using/monitoring-processes.md))。

   管理员用户还可以使用以下 **命令检查`<instance>`** wfserver@module是否已在主应用程序服务器上启动。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   有关如何监视模块的详细信息，请参 [阅本节](../../production/using/usual-commands.md#monitoring-commands-)。

1. 如果模块未运行，请与Adobe客户服务部门联系。 如果您有内部部署安装，管理员必须使用以下命令重新启动该安装。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >替换 **`<instancename>`** 为实例的名称（生产、开发等）。 实例名称通过配置文件进行标识：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有关如何重新启动模块的详细信息，请参 [阅本节](../../production/using/usual-commands.md#module-launch-commands)。

## 失败的工作流 {#failed-workflow}

如果工作流失败，请执行以下步骤：

1. 检查工作流日志。 有关详细信息，请参阅“监视工 [作流执行](../../workflow/using/monitoring-workflow-execution.md) ”和“ [显示日志](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) ”部分。
1. 监控技术工作流。 For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. 查找单个工作流活动的失败。
