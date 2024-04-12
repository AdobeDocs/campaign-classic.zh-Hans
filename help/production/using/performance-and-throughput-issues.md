---
product: campaign
title: 性能和吞吐量问题
description: 性能和吞吐量问题
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 2%

---

# 性能和吞吐量问题{#performance-and-throughput-issues}



首先，您应该检查是否已安装最新版本。 这可确保您拥有最新的功能和错误修复。

请参阅 [发行说明](../../rn/using/latest-release.md) 以了解有关每个版本内容的更多信息。

## 硬件和基础架构 {#hardware-and-infrastructure}

关于本地Campaign Classic的硬件要求的一般准则详述于此 [页面](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html).

咨询团队可以为托管客户提供一个工具，让您轻松查看数据库中各种类型的表使用的空间量以及SFTP站点上使用的空间。 此外，它还提供了一些工具，允许您清除不必要的数据。 联系人 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 如果您需要实施此工具。 以下是使用此工具需要检查的一些重要事项：

* 如果索引大小大于表大小，则需要使用真空。
* 检查具有最大膨胀量的表。 如果这些表经常使用，则需要对其进行吸尘。
* 数据库阻止可能会导致电子邮件停止发送。

Adobe Campaign还提供 [工具](../../production/using/monitoring-processes.md#manual-monitoring) 检查CPU和RAM使用情况。 使用此工具并查看特定指标，例如： **内存**， **交换内存**， **磁盘**， **活动进程**. 如果值过高，您可以尝试减少工作流的数量，或安排工作流在不同时间启动。

## 数据库检查 {#database-performances}

大多数情况下，性能问题与数据库维护有关。 以下是需要检查的主要项目：

* 配置：我们建议检查初始Adobe Campaign平台配置并运行完整的硬件检查。
* Adobe Campaign平台的安装和配置：检查网络配置和平台可投放性选项。
* 数据库维护：确保数据库清理任务可操作，并且正确地计划和执行数据库维护。 检查工作表的数量和大小。
* 实时诊断：检查流程和平台日志文件，然后在重新创建问题的同时监控数据库活动。

>[!NOTE]
>
>有关更多信息，请参阅此章节： [数据库性能](../../production/using/database-performances.md).

## 应用程序配置 {#application-configuration}

以下是有关应用程序配置最佳实践的文章列表：

* MTA和MTAChild进程和内存： **mta** 模块将消息分发到其 **matachild** 子模块。 每个 **matachild** 在请求统计服务器的授权并发送之前准备消息。 请参阅此 [页面](../../installation/using/email-deliverability.md) 以了解更多信息。
* TLS配置：不建议全局启用TLS，因为它可能会降低吞吐量。 相反，由可投放性团队管理的每个域的TLS设置应根据需要进行调整。 请参阅此 [页面](../../installation/using/email-deliverability.md#mx-configuration) 以了解更多信息。
* DKIM：为确保DKIM的安全级别，1024b是推荐的最佳实践加密大小。 大多数访问提供商不会将较低的DKIM密钥视为有效。 请参见[此页面](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

## 可投放性问题 {#deliverability-issues}

以下是与可投放性相关的最佳实践和文章列表：

* IP信誉：如果IP信誉不够好，将会影响性能。 此 **投放能力监控** 模块提供了多种工具来跟踪平台的可交付性性能。 请参阅此 [页面](../../delivery/using/monitoring-deliverability.md).
* IP预热： IP预热由可投放性团队执行。 这包括在几周内通过新IP逐渐增加电子邮件数量。
* IP关联设置：错误的IP关联设置可能会完全停止电子邮件（配置中的运算符/关联名称不正确）或降低吞吐量（关联中的IP数量较少）。 请参阅此 [页面](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* 电子邮件大小：电子邮件大小在吞吐量中起着重要作用。 建议的最大电子邮件大小为60 KB。 请参阅此 [页面](https://helpx.adobe.com/legal/product-descriptions/campaign.html). 在 [投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput) 报告，检查按小时传输的字节数。
* 大量无效收件人：当存在大量无效收件人时，可能会影响吞吐量。 MTA不断重试向无效收件人发送电子邮件。 请确保您的数据库得到了妥善维护。
* 个性化程度：如果投放持续处于“正在进行个性化”状态，请检查个性化块中使用的JavaScript。

>[!NOTE]
>
>另请参阅 [可投放性](../../delivery/using/about-deliverability.md) 部分。 要更深入地了解可投放性，请参阅 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans).
