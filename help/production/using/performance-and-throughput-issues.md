---
solution: Campaign Classic
product: campaign
title: 性能和吞吐量问题
description: 性能和吞吐量问题
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: d1b38acc5209a5c96ab7a35fe9640159141b110f
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 2%

---


# 性能和吞吐量问题{#performance-and-throughput-issues}

首先，您应检查是否已安装最新版本。 这可确保您具备最新功能和错误修复。

有关每个发行版内容的详细信息，请参阅[发行说明](../../rn/using/latest-release.md)。

## 硬件和基础架构{#hardware-and-infrastructure}

本[页](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html)中详细介绍了内部部署Campaign Classic的硬件要求的一般准则。

咨询团队可以为托管客户提供一个工具，它允许您轻松视图数据库中各种类型的表使用了多少空间以及SFTP站点上使用的空间。 此外，它还提供允许您清理不必要数据的工具。 如果您需要实施此工具，请联系[Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 以下是使用此工具时要检查的一些重要事项：

* 如果索引大小大于表大小，则需要真空。
* 检查具有最大膨胀的表。 如果这些表格经常使用，则需要抽空。
* 阻止数据库可能导致电子邮件停止发送。

Adobe Campaign还提供了一个[工具](../../production/using/monitoring-processes.md#manual-monitoring)以检查CPU和RAM使用情况。 使用此工具并查看特定指标，如：**内存**、**交换内存**、**磁盘**、**活动进程**。 如果值过高，您可以尝试在不同时间减少工作流或计划工作流到开始的数量。

## 数据库检查{#database-performances}

大多数时候，性能问题都与数据库维护相关。 以下是要检查的主要项目：

* 配置：我们建议检查初始Adobe Campaign平台配置并运行完整的硬件检查。
* 安装和配置Adobe Campaign平台：检查网络配置和平台可交付性选项。
* 数据库维护：确保数据库清理任务可以运行，并确保正确计划和执行数据库维护。 检查工作表的数量和大小。
* 实时诊断：检查进程和平台日志文件，然后在重新创建问题时监视数据库活动。

>[!NOTE]
>
>有关详细信息，请参阅此部分：[数据库性能](../../production/using/database-performances.md)。

## 应用程序配置{#application-configuration}

以下是与应用程序配置最佳实践相关的文章列表:

* MTA和MTAChild进程和内存：**mta**&#x200B;模块向其&#x200B;**mtachild**&#x200B;子模块分发消息。 每个&#x200B;**mtachild**&#x200B;在从统计服务器请求授权并发送消息之前准备消息。 有关详细信息，请参阅此[页](../../installation/using/email-deliverability.md)。
* TLS配置：不建议全局启用TLS，因为它可以降低吞吐量。 相反，应根据需要调整由可交付性团队管理的每域TLS设置。 有关详细信息，请参阅此[页](../../installation/using/email-deliverability.md#mx-configuration)。
* DKIM:为确保DKIM的安全级别，建议使用1024b作为最佳实践。 大多数访问提供者将不认为低DKIM密钥有效。 请参见[此页面](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

## 可交付性问题{#deliverability-issues}

以下是与可交付性相关的最佳实践和文章的列表:

* IP信誉：如果IP信誉不够好，将对性能产生影响。 **可交付性监控**&#x200B;模块优惠各种工具来跟踪平台的可交付性性能。 请参阅此[页](../../delivery/using/monitoring-deliverability.md)。
* IP预热：IP预热由可交付性团队执行。 这包括在几周内通过新IP逐渐增加电子邮件数量。
* IP关联设置：不正确的IP关联设置可以完全停止电子邮件(配置中的运算符/关联名称不正确)或降低吞吐量(关联中的IP数量较少)。 请参阅此[页](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)。
* 电子邮件大小：电子邮件大小在吞吐量中起着重要作用。 建议的最大电子邮件大小为60 KB。 请参阅此[页](https://helpx.adobe.com/legal/product-descriptions/campaign.html)。 在[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)报告中，检查按小时传输的字节数。
* 大量无效收件人:当存在大量无效收件人时，会影响吞吐量。 MTA会继续重试向无效收件人发送电子邮件。 请确保您的数据库已妥善维护。
* 个性化数量：如果投放仍在“进行个性化”中，请检查个性化块中使用的JavaScript。

>[!NOTE]
>
>另请参阅[Deliverability](../../delivery/using/about-deliverability.md)部分。 有关可交付性的更深入了解，请参阅[《Adobe可交付性最佳实践指南》](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)。
