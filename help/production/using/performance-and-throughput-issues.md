---
title: 性能和吞吐量问题
seo-title: 性能和吞吐量问题
description: 性能和吞吐量问题
seo-description: null
page-status-flag: never-activated
uuid: 28c35453-9a15-44a3-9961-f4c604c209c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: ec66e3e3-b09a-44a4-914d-e3b38c7643f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# 性能和吞吐量问题{#performance-and-throughput-issues}

>[!NOTE]
>
>首先，您应检查是否已安装最新版本。 这可确保您拥有最新功能和错误修复。 有关每个版 [本内容的详细信息](https://docs.campaign.adobe.com/doc/AC/en/RN.html) ，请参阅发行说明。

## 硬件和基础架构 {#hardware-and-infrastructure}

本文详细介绍了内部部署Campaign Classic的硬件要求的一般指 [南](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)。

咨询团队可以为托管客户提供一个工具，使您能够轻松查看数据库中各种类型的表使用了多少空间以及SFTP站点上使用的空间。 此外，它还提供了一些工具，允许您清理不必要的数据。 如果需要实施此工具，请与咨询或支持团队联系。 以下是使用此工具检查的几个重要事项：

* 如果索引大小大于表大小，则需要真空。
* 检查具有最大膨胀的表。 如果这些表经常使用，则需要抽真空。
* 阻止数据库可能导致电子邮件停止发送。

Adobe Campaign还提供了一 [个检查](../../production/using/monitoring-processes.md#manual-monitoring) CPU和RAM使用情况的工具。 使用此工具并查看特定指标，如：内 **存、交**&#x200B;换内存 **、**&#x200B;磁盘 **、有******&#x200B;效过程 如果值过高，您可以尝试减少工作流的数量或将工作流计划在不同时间启动。

## 数据库性能 {#database-performances}

大多数时候，性能问题都与数据库维护有关。 以下是要检查的主要项目：

* 配置：我们建议检查初始的Adobe Campaign平台配置并运行完整的硬件检查。
* Adobe Campaign平台的安装和配置：检查网络配置和平台交付性选项。
* 数据库维护：确保数据库清除任务可运行，并确保正确计划和执行数据库维护。 检查工作表的数量和大小。
* 实时诊断：检查进程和平台日志文件，然后在重新创建问题时监视数据库活动。

>[!NOTE]
>
>For more information, refer to this section: [Database performances](../../production/using/database-performances.md).

## 应用程序配置 {#application-configuration}

以下是与应用程序配置最佳实践相关的文章列表：

* MTA和MTAChild进程和内存：mta **模块** 向其子模块分 **发消息** 。 每个 **计算机** 在从统计服务器请求授权并发送消息之前准备消息。 Refer to this [page](../../installation/using/email-deliverability.md) for more information.
* TLS配置：不建议全局启用TLS，因为它可以降低吞吐量。 相反，应根据需要调整由可交付性团队管理的每域TLS设置。 Refer to this [page](../../installation/using/email-deliverability.md#mx-configuration) for more information.
* DKIM:为确保DKIM的安全级别，建议采用最佳实践加密大小。 大多数访问提供者不会认为低DKIM密钥有效。 请参阅本 [页](../../delivery/using/technical-recommendations.md#domainkeys-identified-mail--dkim-) 和此技 [术说明](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)。

## 可交付性问题 {#deliverability-issues}

以下是与交付性相关的最佳实践和文章列表：

* IP声誉：如果IP声誉不够好，就会对业绩产生影响。 可交 **付性监视模块** ，提供各种工具来跟踪平台的可交付性能。 Refer to this [page](../../delivery/using/technical-monitoring.md).
* IP预热：ip预热由可交付性团队执行。 这包括在几周内通过新IP逐渐增加电子邮件数量。
* IP亲和力设置：不正确的IP关联设置可以完全停止电子邮件（配置中的运算符／关联名称不正确）或降低吞吐量（关联中的IP数量较少）。 Refer to this [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* 电子邮件大小：电子邮件大小在吞吐量中起着重要作用。 建议的最大电子邮件大小为60 KB。 Refer to this [page](https://helpx.adobe.com/legal/product-descriptions/campaign.html). 在“交 [付吞吐量](../../reporting/using/reports-on-deliveries.md#delivery-throughput) ”报告中，检查按小时传输的字节数。
* 大量无效收件人：当存在大量无效收件人时，它可能会影响吞吐量。 MTA会继续重试向无效收件人发送电子邮件。 请确保数据库得到妥善维护。
* 个性化数量：如果交付仍在“进行个性化”中，请检查个性化基块中使用的JavaScript。

>[!NOTE]
>
>别忘了查阅交付性入 [门指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 。

