---
solution: Campaign Classic
product: campaign
title: 工作流执行
description: 工作流执行
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---


# 工作流执行{#workflow-execution}

以下部分介绍与工作流执行相关的常见问题以及如何解决这些问题。

有关工作流的详细信息，请参阅以下部分：

* [关于工作流](../../workflow/using/about-workflows.md)
* [启动工作流](../../workflow/using/starting-a-workflow.md)
* [工作流生命周期](../../workflow/using/workflow-life-cycle.md)
* [使用工作流时的最佳实践](../../workflow/using/workflow-best-practices.md)

## 开始尽快在活动{#start-as-soon-as-possible-in-campaigns}中

在某些情况下，当单击&#x200B;**[!UICONTROL Start]**&#x200B;按钮时，从活动执行的工作流不会开始。 它不是开始，而是进入“尽快开始”状态。

此问题有多种原因，请按照以下步骤解决：

1. 检查[**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md)技术工作流状态。 此工作流管理活动内的作业或工作流。 如果失败，将导致工作流不开始/停止。 重新启动它以恢复活动工作流的运行。

   有关技术工作流监视的详细信息，请参阅[此页](../../workflow/using/monitoring-technical-workflows.md)。

   >[!NOTE]
   >
   >重新启动工作流后，请确保执行挂起的任务(右键单击&#x200B;**[!UICONTROL Scheduler]**&#x200B;活动/ **[!UICONTROL Execute pending task(s) now]**)，以便检查它是否在任何活动上再次失败。

   如果工作流仍然失败，请检查审计日志中是否有特定错误，进行相应的疑难解答，然后重新启动该工作流。

1. 检查&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡中的&#x200B;**[!UICONTROL wfserver]**&#x200B;模块状态，可从Campaign Classic主页访问该选项卡（请参阅[监控进程](../../production/using/monitoring-processes.md)）。 此过程负责运行所有工作流。

   管理员用户还可以使用以下命令检查是否已在主应用程序服务器上启动&#x200B;**wfserver@`<instance>`**&#x200B;模块。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   如果模块未运行，请与Adobe客户服务部门联系。 如果您有内部部署安装，则管理员用户必须使用以下命令重新启动该服务。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >将&#x200B;**`<instancename>`**替换为实例的名称（生产、开发等）。 实例名称通过配置文件进行标识：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有关如何重新启动模块的详细信息，请参阅[本节](../../production/using/usual-commands.md#module-launch-commands)。

1. 检查实例上运行&#x200B;**的**&#x200B;活动进程数是否大于阈值。 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management)选项对实例上可并行运行的活动进程数量有限。 当达到此限制时，只要运行的开始数超过该限制，工作流就会保持“尽快”状态。

   要解决此问题，请停止不需要的工作流并删除失败的投放。 如果达到阈值，则允许运行新进程。

   要检查实例运行的工作流数，我们建议使用预定义视图，默认情况下可在&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Audit]**&#x200B;文件夹中访问预定义的。 有关详细信息，请参见[此页面](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)。

   >[!IMPORTANT]
   >
   >增加&#x200B;**[!UICONTROL NmsOperation_LimitConcurrency]**&#x200B;选项阈值可能会导致实例出现性能问题。 无论如何，请勿自行执行此操作并联系您的Adobe Campaign联系人。

有关如何监视工作流的详细信息，请参阅[本节](../../workflow/using/monitoring-workflow-execution.md)。

## 开始正在{#start-in-progress}

如果工作流未执行，且其状态为&#x200B;**正在开始**，则这可能意味着工作流模块未启动。

要选中此项并在必要时开始模块，请应用以下步骤：

1. 检查&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡中的&#x200B;**[!UICONTROL wfserver]**&#x200B;模块状态，可从Campaign Classic主页访问该选项卡（请参阅[监控进程](../../production/using/monitoring-processes.md)）。

   管理员用户还可以使用以下命令检查是否已在主应用程序服务器上启动&#x200B;**wfserver@`<instance>`**&#x200B;模块。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   有关如何监视模块的详细信息，请参阅[本节](../../production/using/usual-commands.md#monitoring-commands-)。

1. 如果模块未运行，请与Adobe客户服务部门联系。 如果您有内部部署安装，管理员必须使用以下命令重新启动该安装。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >将&#x200B;**`<instancename>`**替换为实例的名称（生产、开发等）。 实例名称通过配置文件进行标识：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有关如何重新启动模块的详细信息，请参阅[本节](../../production/using/usual-commands.md#module-launch-commands)。

## 工作流{#failed-workflow}失败

如果工作流失败，请执行以下步骤：

1. 检查工作流日志。 有关详细信息，请参阅[监视工作流执行](../../workflow/using/monitoring-workflow-execution.md)和[显示日志](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)部分。
1. 监控技术工作流。 有关详细信息，请参阅[此部分](../../workflow/using/monitoring-technical-workflows.md)。
1. 查找各个工作流活动的失败。
