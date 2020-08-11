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
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---


# 性能和吞吐量问题{#performance-and-throughput-issues}

>[!NOTE]
>
>首先，您应检查是否已安装最新版本。 这可确保您拥有最新功能和错误修复。 有关每个版 [本的内容](../../rn/using/latest-release.md) ，请参阅发行说明。

## 硬件和基础架构 {#hardware-and-infrastructure}

本文详细介绍了内部部署Campaign Classic的硬件要求的一般 [准则](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)。

咨询团队可以为托管客户提供一个工具，它允许您轻松视图数据库中各种类型的表使用了多少空间以及SFTP站点上使用的空间。 它还提供允许您清除不必要数据的工具。 如果您需要实施此工具，请与咨询或支持团队联系。 下面是使用此工具检查的一些重要事项：

* 如果索引大小大于表大小，则需要真空。
* 检查具有最大膨胀的表。 如果这些表格经常使用，则需要抽真空。
* 阻止数据库可能导致电子邮件停止发送。

Adobe Campaign还提供 [检查](../../production/using/monitoring-processes.md#manual-monitoring) CPU和RAM使用情况的工具。 使用此工具并查看特定指标，如： **内存**、 **交换内存**、 **磁盘**、活 **动进程**。 如果值过高，您可以尝试在不同时间减少工作流或计划工作流的数量。

## 数据库性能 {#database-performances}

大多数时间、性能问题都与数据库维护相关。 以下是要检查的主要项目：

* 配置：我们建议检查初始Adobe Campaign平台配置并运行完整的硬件检查。
* Adobe Campaign平台的安装和配置：检查网络配置和平台交付性选项。
* 数据库维护：确保数据库清理任务可以运行，并确保正确计划和执行数据库维护。 检查工作表的数量和大小。
* 实时诊断：检查进程和平台日志文件，然后在重新创建问题时监视数据库活动。

>[!NOTE]
>
>For more information, refer to this section: [Database performances](../../production/using/database-performances.md).

## 应用程序配置 {#application-configuration}

以下是与应用程序配置最佳实践相关的一列表文章：

* MTA和MTAChild进程和内存：mta **模块** 将消息分发到 **它的mtachild子模** 块。 每个 **计算** 域在从统计服务器请求授权并发送之前准备消息。 Refer to this [page](../../installation/using/email-deliverability.md) for more information.
* TLS配置：不建议全局启用TLS，因为它可以降低吞吐量。 相反，应根据需要调整由可交付性团队管理的每域TLS设置。 Refer to this [page](../../installation/using/email-deliverability.md#mx-configuration) for more information.
* DKIM:为确保DKIM的安全级别，建议使用最佳实践加密大小。 大多数访问提供者不认为低DKIM密钥有效。 请参阅本 [页](../../delivery/using/technical-recommendations.md#dkim) 和本技 [术说明](https://helpx.adobe.com/cn/campaign/kb/domain-name-delegation.html)。

## 可交付性问题 {#deliverability-issues}

以下是与可交付性相关的最佳实践和文章的列表:

* IP信誉：如果IP信誉不够好，将会影响性能。 可 **交付性监控模块** 优惠各种工具来跟踪平台的可交付性能。 Refer to this [page](../../delivery/using/monitoring-deliverability.md).
* IP预热：IP预热由可交付性团队执行。 这包括在几周内通过新IP逐渐增加电子邮件数量。
* IP关联设置：不正确的IP关联设置可以完全停止电子邮件(配置中的运算符/关联名称不正确)或降低吞吐量(关联中的IP数量较少)。 Refer to this [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* 电子邮件大小：电子邮件大小在吞吐量中起着重要作用。 建议的最大电子邮件大小为60 KB。 Refer to this [page](https://helpx.adobe.com/legal/product-descriptions/campaign.html). 在投放 [吞吐量报](../../reporting/using/global-reports.md#delivery-throughput) 告中，检查按小时传输的字节数。
* 大量无效收件人:当存在大量无效收件人时，会影响吞吐量。 MTA会继续重试向无效收件人发送电子邮件。 请确保数据库得到妥善维护。
* 个性化数量：如果投放保持“个性化正在进行中”，请检查个性化块中使用的JavaScript。

>[!NOTE]
>
>另请参 [阅“可交付性”关键](../../delivery/using/deliverability-key-points.md) 点部分。

