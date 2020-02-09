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
source-git-commit: 69b562979f3b32a4d30dfed0695cf3cf6c0fd26a

---


# 工作流执行{#workflow-execution}

以下部分介绍与工作流执行相关的常见问题以及如何解决这些问题。

有关工作流的详细信息，请参阅以下各节：

* [关于工作流](../../workflow/using/about-workflows.md)
* [执行工作流](../../workflow/using/executing-a-workflow.md)
* [使用工作流时的最佳实践](../../workflow/using/workflow-best-practices.md)

## 在营销活动中尽快开始 {#start-as-soon-as-possible-in-campaigns}

在某些情况下，从营销活动执行的工作流在单击按钮时不会启 **[!UICONTROL Start]** 动。 它不是开始，而是进入“尽快开始”状态。

此问题有多种原因，请按照以下步骤解决：

1. 检查技术 [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) 工作流状态。 此工作流管理营销活动内的作业或工作流。 如果失败，这将导致工作流不启动／停止。 重新启动它以恢复营销活动工作流的运行。

   有关技术工作流监控的详细信息，请参 [阅本页](../../workflow/using/monitoring-technical-workflows.md)。

   >[注意]
   >
   >重新启动工作流后，请确保执行待处理任务(右键单击活动 **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**)，以便检查其是否再次在任何活动上失败。

   如果工作流仍然失败，请检查审核日志中是否有特定错误，并相应地进行疑难解答，然后再次重新启动该工作流。

1. 检查选 **[!UICONTROL wfserver]** 项卡中的模块状态， **[!UICONTROL Monitoring]** 可从“营销活动经典”主页访问该选项卡(请参阅 [监视流程](../../production/using/monitoring-processes.md))。 此过程负责运行所有工作流。

   管理员用户还可以使用以下 **命令检查是否在主应用程序服务器上启动了wfserver@`<instance>`**module。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   如果模块未运行，请与Adobe客户关怀联系。 如果您有内部部署安装，管理员用户必须使用以下命令重新启动服务。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >用 **`<instancename>`** 实例的名称（生产、开发等）替换。 通过配置文件标识实例名称：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有关如何重新启动模块的详细信息，请参 [阅此部分](../../production/using/usual-commands.md#module-launch-commands)。

1. 检查实例 **上运行的系列活动进程** ，数量是否大于阈值。 该选项对实例上可以并行运 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 行的营销活动进程数量定义了一个限制。 当达到此限制时，只要运行的工作流数超过该限制，该工作流就会保持“尽快启动”状态。

   要解决此问题，请停止不需要的工作流并删除失败的提交。 如果达到阈值，则允许运行新进程。

   要检查实例运行的工作流数，我们建议使用预定义的视图，默认情况下可在 **[!UICONTROL Administration]** /文件夹 **[!UICONTROL Audit]** 中访问。 For more information, refer to [this page](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[警告]
   >
   >增加选 **[!UICONTROL NmsOperation_LimitConcurrency]** 项阈值可能导致实例的性能问题。 无论如何，请勿自行执行此操作，并联系您的Adobe Campaign联系人。

有关如何监视工作流的详细信息，请参阅 [此部分](../../workflow/using/monitoring-workflow-execution.md)。

## 开始进行 {#start-in-progress}

如果工作流未执行，且其状态为“ **开始”**，这可能意味着工作流模块未启动。

要选中此项并根据需要启动模块，请应用以下步骤：

1. 检查选 **[!UICONTROL wfserver]** 项卡中的模块状态， **[!UICONTROL Monitoring]** 可从“营销活动经典”主页访问该选项卡(请参阅 [监视流程](../../production/using/monitoring-processes.md))。

   管理员用户还可以使用以下 **命令检查是否在主应用程序服务器上启动了wfserver@`<instance>`**module。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   有关如何监视模块的详细信息，请参阅 [本节](../../production/using/usual-commands.md#monitoring-commands-)。

1. 如果模块未运行，请与Adobe客户关怀联系。 如果您有内部部署安装，则管理员必须使用以下命令重新启动它。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >用 **`<instancename>`** 实例的名称（生产、开发等）替换。 通过配置文件标识实例名称：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有关如何重新启动模块的详细信息，请参 [阅此部分](../../production/using/usual-commands.md#module-launch-commands)。

## 失败的工作流 {#failed-workflow}

如果工作流失败，请执行以下步骤：

1. 选中工作流日记帐。 有关详细信息，请参阅监视工 [作流执行](../../workflow/using/monitoring-workflow-execution.md)[和显示日志部分](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 。
1. 监控技术工作流程。 For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. 查找单个工作流活动的失败情况。
