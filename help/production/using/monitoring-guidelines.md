---
product: campaign
title: 监测准则
description: 了解监控 Campaign 实例和流程的准则和最佳实践。
audience: production
content-type: reference
topic-tags: introduction
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 20%

---

# 监测准则 {#monitoring-guidelines}

## 实例监控仪表板{#instance-monitoring-dashboard}

**[!UICONTROL Monitoring]**&#x200B;选项卡可从Campaign Classic主页访问，它是帮助您监视实例的主要入口点。

它提供了实例中发生情况的功能板：其状态（生成版本、已安装的包等）、系统指示器、日志、当前正在运行的工作流、上次发送投放的状态等。

详情请见[此处](../../production/using/monitoring-processes.md)。

![](assets/monitoring_tab.png)

## 监控Campaign Classic进程{#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">监控实例</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">监测工作流</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">监测投放</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">监视数据库</a></p></td></tr>
</table>

还提供了其他监控不同营销活动流程的方法。 它们提供了多种监视实例的方法，以确保您的系统运行正常，并最终解决在设置工作流、发送投放等操作时可能出现的问题。

### 监控实例{#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**自动监控工具**

提供了多种自动方法。 来帮助您监控实例。 例如，您可以设置包含检测到的异常的电子邮件报表，以XML格式检索指标列表等。 [单击此处](../../production/using/monitoring-processes.md#automatic-monitoring)以了解更多信息。

**审核跟踪**

审核跟踪允许您查看与实例中的选项、工作流和架构相关的更改的完整历史记录。 [单击此处](../../production/using/audit-trail.md)以了解更多信息。

**控制面板**

利用控制面板，可管理实例的多个设置：管理URL权限，检查实例详细信息，如服务器的内部版本等。 它还允许您监视连接到实例的SFTP服务器上的可用空间。 [单击此处](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)以了解更多信息。

>[!NOTE]
>
>所有管理员用户都可访问控制面板。[此页面](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans#discover-control-panel)详细介绍了授予用户管理员访问权限的步骤。
>
>请注意，您的实例必须托管在AWS上，并升级为最新的[Gold Standard](../../rn/using/gs-overview.md)内部版本或[最新的GA内部版本(21.1)](../../rn/using/latest-release.md)。 在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何确认您的版本。要检查您的实例是否托管在 AWS 上，请按照[此页面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详述的步骤操作。

### 监控工作流 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流热图**

工作流热图直观地显示了在您的实例上运行的所有工作流。 它使您能够轻松监控实例上的负载并相应地规划工作流。 [单击此处](../../workflow/using/heatmap.md)以了解更多信息。

**审核跟踪**

审核跟踪允许您可视化工作流中所做的所有修改及其当前状态。 [单击此处](../../production/using/audit-trail.md).

**工作流疑难解答**

当遇到工作流执行问题时，可以执行特定操作。 [单击此](../../production/using/workflow-execution.md) 处以了解更多信息

**工作流状态监控**

除了热图之外，您还可以创建一个工作流，用于监视一组工作流的状态并向主管发送定期消息。 [单击此处](../../workflow/using/supervising-workflows.md)以了解更多信息。

**一般准则**

使用工作流时，请遵循以下准则和最佳实践，这有助于提高性能。 有关更多信息，请参阅以下章节：
* [使用工作流时的最佳实践](../../workflow/using/workflow-best-practices.md)
* [监控工作流执行](../../workflow/using/monitoring-workflow-execution.md)

### 监控投放 {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP报表**

SMTP报表按域显示投放统计信息和SMTP错误。 [了解详情](../../production/using/monitoring-processes.md)

**最佳做法**

[投放发送和设计的最](../../delivery/using/delivery-best-practices.md) 佳实践可以帮助您提高性能。

**投放疑**
难解答在遇到投放问题时，可以执行特定操作：
* [投放能力问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [图像显示问题](../../production/using/image-display-issues.md)
* [交付性能问题](../../delivery/using/delivery-performances.md)
* [临时文件问题](../../production/using/temporary-files.md)  — 仅限 *内部部署托管模型*

### 监视数据库{#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**数据库清理工作流**

利用数据库清理工作流，可从数据库中删除过时的数据。 建议避免数据库呈指数级增长。 [单击此处](../../production/using/database-cleanup-workflow.md)以了解更多信息。

**数据库性能疑难解答**

在遇到数据库性能问题时，可以执行特定操作。 [单击此处](../../production/using/database-performances.md)以了解更多信息。

**数据库维护**

*仅限内部部署和混合托管模型*

我们建议您定期执行数据库维护，以避免磁盘空间过度消耗，从而影响数据库访问。 [单击此处](../../production/using/recommendations.md)以了解更多信息。

**备份和恢复**

*仅限内部部署和混合托管模型*

备份对于避免在计算机上出现问题（无论是物理问题还是系统问题）时丢失数据至关重要。 [单击此处](../../production/using/backup.md)以了解更多信息。[此部分](../../production/using/restoration.md)中介绍了恢复过程。

## Campaign Classic技术原则{#campaign-classic-technical-principles}

技术资源可在Campaign Classic文档中找到。 我们建议您在对实例执行任何技术操作之前先熟悉这些主题。

**托管模型和功能**

* [Campaign Classic托管模型](../../installation/using/hosting-models.md)
* [托管模型功能](../../installation/using/capability-matrix.md)

**服务器配置**

*仅限内部部署和混合托管模型*

* [服务器配置](../../installation/using/configuring-campaign-server.md)
* [Serverconf.xml文件配置](../../installation/using/the-server-configuration-file.md)
* [用于可投放性的服务器配置](../../installation/using/email-deliverability.md)
* [用于创建实例并声明数据库的命令行](../../installation/using/command-lines.md)

**一般原则**

* [Campaign Classic架构](../../production/using/general-architecture.md)
* [Campaign Classic模块](../../production/using/operating-principle.md)
* [Campaign Classic选项](../../installation/using/configuring-campaign-options.md)
* [如何设置模块自动启动](../../production/using/administration.md)
* [营销活动配置原则](../../production/using/configuration-principle.md)
* [故障排除过程](../../production/using/performance-and-throughput-issues.md)
