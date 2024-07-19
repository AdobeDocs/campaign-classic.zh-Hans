---
product: campaign
title: 应用程序对象
description: 应用程序对象
feature: Monitoring
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 4%

---

# 应用程序对象{#application-objects}



应该对内置对象进行监控，防止它们过度增长很重要。

## ID序列 {#sequence-of-ids}

Adobe Campaign使用的ID序列必须相应地使用： **xtkNewId**。 如果序列使用非常快（即每天超过100,000个），则必须验证序列是否符合您的业务要求，例如每天发送数百万封电子邮件。 可以为特定表定义专用序列。 您可以设置工作流来监控ID使用情况。

当序列达到20亿以上（2,147,483,648是确切数字）时，它会返回零。 这种情况必须避免，并造成问题，因此必须监测这一进程。

要防止大型表出现这种情况，请考虑使用特定顺序。 可以使用架构中的&#x200B;**pkSequence**&#x200B;属性完成此操作。

创建大量日志的高频工作流将占用大量ID。 因此，强烈建议避免在工作流中记录过多且频率较高。

如果序列已经循环，最好的解决方案是切换到负ID，从 — 2,147,483,648开始。

## 文件夹 {#folders}

任何实例上的文件夹都应少于1000个。 文件夹数量超过此数量可能会导致Campaign客户端出现性能问题。 您可以设置监视作业以计算文件夹数、工作流数等，并定期报告。

此方法还会突出显示创建过多对象的用户。

## 投放 {#deliveries}

实例上的投放随时应少于1000个。 大量投放会占用数据库空间并产生问题。 每天创建10个以上投放的实例必须根据业务需求进行检查。 考虑使用连续投放来减少投放。 如需详细信息，请参阅[此小节](../../workflow/using/continuous-delivery.md)。

应从实例中清除超过两年的投放。

## 文件 {#files}

应用程序服务器磁盘上的文件数不应无限增加。

导入工作流会创建文件，因此会导致磁盘扩展。 使用标准[文件收集器](../../workflow/using/file-collector.md)活动可防止出现这种情况。 文件收集器将文件移动到临时文件夹并自动将其清除。

如果工作流导入了文件但未使用标准功能，则需要清除工作流以最大限度地减少磁盘空间。

## 事务性数据和日志 {#transactional-data-and-logs}

将数据导入Adobe Campaign的每个[工作流](../../workflow/using/data-life-cycle.md#work-table)都会导致数据库大小增大。

检查清理或清除工作流是否正在运行，并是否有效地清除记录。 必须清除所有事务性数据和日志。 清理任务仅清除标准表：跟踪和广泛日志。 特定表必须由特定工作流清除。 请参阅[此小节](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)。

通过检查记录的最早创建日期，观察事务型数据的老化情况。
