---
solution: Campaign Classic
product: campaign
title: 监控准则
description: 了解监控 Campaign 实例和流程的准则和最佳实践。
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 7%

---


# 监控准则 {#monitoring-guidelines}

## 实例监视仪表板{#instance-monitoring-dashboard}

**[!UICONTROL Monitoring]**&#x200B;选项卡可从Campaign Classic主页访问，它是帮助您监视实例的主要入口点。

它提供了实例中发生情况的仪表板:其状态（构建版本、已安装的包等）、系统指示器、日志、当前正在运行的工作流、上次发送的投放的状态等。

详情请见[此处](../../production/using/monitoring-processes.md)。

![](assets/monitoring_tab.png)

## 监视Campaign Classic进程{#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">监视您的实例</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">监视工作流</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">监视投放</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">监视数据库</a></p></td></tr>
</table>

还提供了其他监视不同活动过程的方法。 它们提供了几种监视实例的方法，以确保您的系统运行正常，并最终解决在设置工作流、发送投放等时可能出现的问题。

### 监视您的实例{#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**自动监控工具**

有几种自动方法可用。 来监控您的实例。 例如，您可以设置检测到异常的电子邮件报告，检索XML格式的列表指示符等。 [请单](../../production/using/monitoring-processes.md#automatic-monitoring) 击此处了解详细信息。

**审核跟踪**

审计跟踪允许您直观地显示与实例中的选项、工作流和模式相关更改的完整历史记录。 [请单](../../production/using/audit-trail.md) 击此处了解详细信息。

**控制面板**

该控制面板允许您管理实例的多个设置：管理URL权限，检查您的实例详细信息，如服务器的构建版本等。 它还允许您监视连接到实例的SFTP服务器上的可用空间。 [请单](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html) 击此处了解详细信息。

>[!NOTE]
>
>控制面板可供所有管理员用户访问。 授予用户管理员访问权限的步骤详见[此页](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)。
>
>请注意，您的实例必须托管在AWS上，并使用最新的[Gold Standard](../../rn/using/gs-overview.md)版本或最新的[ GA版本(21.1)](../../rn/using/latest-release.md)进行升级。 了解如何在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中检查您的版本。 要检查您的实例是否托管在AWS上，请按照[本页](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详细介绍的步骤操作。

### 监控工作流 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流热图**

Workflow HeatMap以可视方式呈现了实例上运行的所有工作流。 它允许您轻松监视实例上的负载并相应地规划工作流。 [请单](../../workflow/using/heatmap.md) 击此处了解详细信息。

**审核跟踪**

“审核”跟踪允许您可视化在工作流中所做的所有修改及其当前状态。 [单击此处](../../production/using/audit-trail.md).

**工作流疑难解答**

在工作流执行遇到问题时，可以执行特定操作。 [单击此](../../production/using/workflow-execution.md) 处以了解更多信息

**工作流状态监视**

除了热图之外，您还可以创建一个工作流，它允许您监视一组工作流的状态并向主管发送循环消息。 [请单](../../workflow/using/supervising-workflows.md) 击此处了解详细信息。

**一般准则**

在使用工作流时遵循准则和最佳实践有助于提高性能。 有关详细信息，请参阅以下部分：
* [使用工作流时的最佳实践](../../workflow/using/workflow-best-practices.md)
* [监控工作流执行](../../workflow/using/monitoring-workflow-execution.md)

### 监控投放 {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP报告**

SMTP报告按域显示投放统计和SMTP错误。 [了解详情](../../production/using/monitoring-processes.md)

**最佳做法**

[投放发送和设计的最](../../delivery/using/delivery-best-practices.md) 佳实践可帮助您改进其性能。

**投放疑**
难排解遇到投放问题时，可以执行特定操作：
* [可交付性问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [图像显示问题](../../production/using/image-display-issues.md)
* [投放性能问题](../../delivery/using/delivery-performances.md)
* [临时文件问题](../../production/using/temporary-files.md)  — 仅 *限内部托管模型*

### 监视数据库{#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**数据库清理工作流**

数据库清理工作流允许您从数据库中删除过时的数据。 建议避免数据库呈指数级增长。 [请单](../../production/using/database-cleanup-workflow.md) 击此处了解详细信息。

**数据库性能疑难解答**

在遇到数据库性能问题时，可以执行特定操作。 [请单](../../production/using/database-performances.md) 击此处了解详细信息。

**数据库维护**

*仅内部部署和混合托管模型*

我们建议您定期执行数据库维护，以避免磁盘空间的过度消耗，从而影响数据库访问。 [请单](../../production/using/recommendations.md) 击此处了解详细信息。

**备份和恢复**

*仅内部部署和混合托管模型*

备份是避免在计算机上出现问题（无论是物理问题还是与系统相关）的事件中丢失数据的关键。 [请单](../../production/using/backup.md) 击此处了解详细信息。在[本节](../../production/using/restoration.md)中介绍了恢复过程。

## Campaign Classic技术原则{#campaign-classic-technical-principles}

技术资源可在Campaign Classic文档中找到。 我们建议您在对实例执行任何技术操作之前先熟悉这些主题。

**托管模型和功能**

* [Campaign Classic托管模型](../../installation/using/hosting-models.md)
* [托管模型功能](../../installation/using/capability-matrix.md)

**服务器配置**

*仅内部部署和混合托管模型*

* [强制性服务器配置](../../installation/using/campaign-server-configuration.md)
* [Serverconf.xml文件配置](../../installation/using/the-server-configuration-file.md)
* [可交付的服务器配置](../../installation/using/email-deliverability.md)
* [用于创建实例并声明数据库的命令行](../../installation/using/command-lines.md)

**一般原则**

* [Campaign Classic架构](../../production/using/general-architecture.md)
* [Campaign Classic模块](../../production/using/operating-principle.md)
* [Campaign Classic选项](../../installation/using/configuring-campaign-options.md)
* [如何设置模块的自动启动](../../production/using/administration.md)
* [活动配置原则](../../production/using/configuration-principle.md)
* [疑难解答过程](../../production/using/performance-and-throughput-issues.md)
