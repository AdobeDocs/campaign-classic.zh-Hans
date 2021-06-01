---
product: campaign
title: 性能和吞吐量问题
description: 性能和吞吐量问题
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 4%

---

# 性能和吞吐量问题{#performance-and-throughput-issues}

首先，您应该检查是否已安装最新内部版本。 这可确保您具有最新功能和错误修复。

有关每个版本内容的更多信息，请参阅[发行说明](../../rn/using/latest-release.md)。

## 硬件和基础架构{#hardware-and-infrastructure}

本[page](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html)中详细描述了内部部署Campaign Classic硬件要求的一般准则。

咨询团队可以为托管客户提供一个工具，让您能够轻松查看数据库中各种类型的表使用了多少空间以及SFTP站点上使用的空间。 此外，它还提供了一些工具，用于清理不必要的数据。 如果您需要实施此工具，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 以下是使用此工具需要检查的一些重要事项：

* 如果索引大小大于表大小，则需要真空。
* 检查最大Bloat的表。 如果这些表格经常使用，则需要清空它们。
* 阻止数据库可能会导致电子邮件停止发送。

Adobe Campaign还提供了[工具](../../production/using/monitoring-processes.md#manual-monitoring)来检查CPU和RAM的使用情况。 使用此工具并查看特定指标，例如：**Memory**、**Swap Memory**、**Disk**、**Active Processes**。 如果值过高，您可以尝试减少工作流的数量或安排工作流在不同时间启动。

## 数据库检查{#database-performances}

大多数时候，性能问题都与数据库维护相关。 以下是要检查的主要项目：

* 配置：我们建议检查初始Adobe Campaign平台配置并运行完整的硬件检查。
* Adobe Campaign平台的安装和配置：检查网络配置和平台可交付性选项。
* 数据库维护：确保数据库清理任务可运行，并且数据库维护已正确计划和执行。 检查工作表的数量和大小。
* 实时诊断：检查进程和平台日志文件，然后在重新创建问题时监视数据库活动。

>[!NOTE]
>
>有关更多信息，请参阅此章节：[数据库性能](../../production/using/database-performances.md)。

## 应用程序配置{#application-configuration}

以下是与应用程序配置最佳实践相关的文章列表：

* MTA和MTAChild进程和内存：**mta**&#x200B;模块将消息分发到其&#x200B;**mtachild**&#x200B;子模块。 每个&#x200B;**mtachild**&#x200B;在从统计服务器请求授权并发送之前准备消息。 有关更多信息，请参阅此[页面](../../installation/using/email-deliverability.md)。
* TLS配置：不建议全局启用TLS，因为它可以减少吞吐量。 相反，应根据需要对由可交付性团队管理的每域TLS设置进行调整。 有关更多信息，请参阅此[页面](../../installation/using/email-deliverability.md#mx-configuration)。
* DKIM:为确保DKIM的安全级别，建议采用1024b加密大小。 大多数访问提供商不会认为DKIM密钥较低有效。 请参见[此页面](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

## 投放能力问题{#deliverability-issues}

以下是与投放能力相关的最佳实践和文章列表：

* IP信誉：如果IP声誉不够好，则会对性能产生影响。 **可投放性监控**&#x200B;模块提供了各种工具来跟踪平台的可投放性能。 请参见此[页面](../../delivery/using/monitoring-deliverability.md)。
* IP预热：IP预热由可投放性团队执行。 这涉及在几周内通过新IP逐步增加电子邮件数量。
* IP亲和度设置：不正确的IP亲和度设置可能会完全停止电子邮件（配置中的运算符/亲和度名称不正确）或降低吞吐量（亲和度中的IP数量较少）。 请参见此[页面](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)。
* 电子邮件大小：电子邮件大小在吞吐量中起着重要作用。 建议的最大电子邮件大小为60 KB。 请参见此[页面](https://helpx.adobe.com/legal/product-descriptions/campaign.html)。 在[投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)报表中，检查按小时传输的字节数。
* 大量无效收件人：当有大量无效收件人时，可能会影响吞吐量。 MTA会持续重试向无效收件人发送电子邮件。 请确保数据库维护良好。
* 个性化金额：如果投放保持“个性化正在进行”，请检查个性化块中使用的JavaScript。

>[!NOTE]
>
>另请参阅[投放能力](../../delivery/using/about-deliverability.md)部分。 有关投放能力的更深入分析，请参阅[Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans)。
