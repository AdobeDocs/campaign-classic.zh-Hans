---
title: 监控指南
description: 了解监控活动实例和流程的准则和最佳实践。
page-status-flag: never-activated
uuid: cf0d782d-47bf-40ae-ab6f-d1d47fa15792
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: 8b33e6af-15c3-4b30-8ad6-d76a1f33be21
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 6%

---


# 监控指南 {#monitoring-guidelines}

## 实例监视仪表板 {#instance-monitoring-dashboard}

Campaign Classic **[!UICONTROL Monitoring]** 主页可访问该选项卡，它是帮助您监视实例的主要入口点。

它提供实例发生情况的仪表板:其状态（内部版本、安装的包等）、系统指示符、日志、当前正在运行的工作流、上次发送投放的状态等。

详情请见[此处](../../production/using/monitoring-processes.md)。

![](assets/monitoring_tab.png)

## Monitoring Campaign Classic processes {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">监视您的实例</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">监视工作流</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">监视投放</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">监视数据库</a></p></td></tr>
</table>

还提供了其他监视不同活动过程的方法。 它们提供多种监视实例的方法，以确保您的系统正常，并最终解决在设置工作流、发送投放等时可能出现的问题。

### 监视实例 {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**自动监控工具**

有几种自动方法可用。 以帮助您监控您的实例。 例如，您可以设置检测到异常的电子邮件报告，检索XML格式的列表指示符，等等。 [单击此处](../../production/using/monitoring-processes.md#automatic-monitoring) ，了解更多信息。

**审核跟踪**

审核跟踪允许您查看与实例中的选项、工作流和模式相关更改的完整历史记录。 [单击此处](../../production/using/audit-trail.md) ，了解更多信息。

**控制面板**

该控制面板允许您管理实例的多个设置：管理URL权限，检查您的实例详细信息，如服务器的构建版本等。 它还允许您监视连接到实例的SFTP服务器上的可用空间。 [单击此处](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html) ，了解更多信息。

>[!NOTE]
>
>请注意，控制面板仅供管理员用户访问，并且适用于所有使用Adobe Managed Services的客户。

### 监控工作流 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流热图**

Workflow HeatMap为实例上运行的所有工作流提供了直观的表示形式。 它允许您轻松监视实例上的负载并相应地规划工作流。 [单击此处](../../workflow/using/heatmap.md) ，了解更多信息。

**审核跟踪**

审核跟踪允许您可视化在工作流中所做的所有修改及其当前状态。 [单击 此处](../../production/using/audit-trail.md).

**工作流疑难解答**

在工作流执行遇到问题时，可以执行特定操作。 [单击此处](../../production/using/workflow-execution.md) ，了解更多信息

**工作流状态监视**

除了热图之外，您还可以创建一个工作流，它允许您监视一组工作流的状态并向主管发送循环消息。 [单击此处](../../workflow/using/supervising-workflows.md) ，了解更多信息。

**一般准则**

在使用工作流时遵循准则和最佳实践有助于提高性能。 有关详细信息，请参阅以下部分：
* [使用工作流时的最佳实践](../../workflow/using/workflow-best-practices.md)
* [监控工作流执行](../../workflow/using/monitoring-workflow-execution.md)

### 监控投放 {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP报告**

SMTP报告按域显示投放统计和SMTP错误。 [了解详情](../../production/using/monitoring-processes.md)

**最佳做法**

[投放发送和设计的最佳实践](../../delivery/using/delivery-best-practices.md) ，可帮助您改进其性能。

**投放疑难**&#x200B;排解遇到投放问题时，可以执行特定操作：
* [可交付性问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [图像显示问题](../../production/using/image-display-issues.md)
* [投放性能问题](../../delivery/using/monitoring-a-delivery.md#performance_issues)
* [临时文件问题](../../production/using/temporary-files.md) -仅 *限预置托管模型*

### 监视数据库 {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**数据库清理工作流**

数据库清理工作流允许您从数据库中删除已废弃的数据。 建议避免数据库呈指数级增长。 [单击此处](../../production/using/database-cleanup-workflow.md) ，了解更多信息。

**数据库性能疑难解答**

在遇到数据库性能问题时，可以执行特定操作。 [单击此处](../../production/using/database-performances.md) ，了解更多信息。

**数据库维护**

*仅限预置和混合托管模型*

我们建议您定期执行数据库维护，以避免磁盘空间的过度消耗，从而影响数据库访问。 [单击此处](../../production/using/recommendations.md) ，了解更多信息。

**备份和恢复**

*仅限预置和混合托管模型*

备份是避免在计算机上出现问题（无论是物理问题还是与系统相关）的事件中丢失数据的关键。 [单击此处](../../production/using/backup.md) ，了解更多信息。 本节介绍了恢 [复过程](../../production/using/restoration.md)。

## Campaign Classic技术原则 {#campaign-classic-technical-principles}

技术资源可在Campaign Classic文档中找到。 我们建议您在对实例执行任何技术操作之前先熟悉这些主题。

**托管模型和功能**

* [Campaign Classic托管模型](../../installation/using/hosting-models.md)
* [托管模型功能](https://helpx.adobe.com/cn/campaign/kb/acc-on-prem-vs-hosted.html)

**服务器配置**

*仅内部部署和混合托管模型*

* [强制的服务器配置](../../installation/using/campaign-server-configuration.md)
* [Serverconf.xml文件配置](../../installation/using/the-server-configuration-file.md)
* [可交付的服务器配置](../../installation/using/email-deliverability.md)
* [用于创建实例并声明数据库的命令行](../../installation/using/command-lines.md)

**一般原则**

* [Campaign Classic架构](../../production/using/general-architecture.md)
* [Campaign Classic模块](../../production/using/operating-principle.md)
* [Campaign Classic选项](../../installation/using/configuring-campaign-options.md)
* [如何设置模块的自动启动](../../production/using/administration.md)
* [活动配置原理](../../production/using/configuration-principle.md)
* [疑难解答过程](../../production/using/performance-and-throughput-issues.md)
