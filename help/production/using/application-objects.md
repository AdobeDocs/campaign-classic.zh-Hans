---
title: 应用程序对象
seo-title: 应用程序对象
description: 应用程序对象
seo-description: null
page-status-flag: never-activated
uuid: 84fbad0f-872d-4aca-8ea9-007577be076d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 24d4875b-81fa-4bf3-8cf0-e6998bec4949
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 1%

---


# 应用程序对象{#application-objects}

内置对象应受到监控，防止其增长过多非常重要。

## ID序列 {#sequence-of-ids}

Adobe Campaign使用必须相应使用的ID序列： **xtkNewId**。 如果该序列消耗得非常快（即从每天100,000个开始），您必须验证它是否符合您的业务要求，如每天发送数百万封电子邮件。 可以为特定表定义专用序列。 您可以设置一个工作流来监视ID使用情况。

当序列达到20亿多（确切数字为2147483648）时，它会回到零。 必须避免并引起问题，这就是必须监视此序列的原因。

要防止在大表中出现这种情况，请考虑使用特定序列。 这可以使用模式 **中的** pkSequence属性完成。

创建大量日志的高频工作流将占用大量ID。 因此，强烈建议避免工作流中日志过多和频率过高。

如果序列已经循环，则最好的解决方案是切换到负ID，从-2,147,483,648开始。

## 文件夹 {#folders}

任何实例上应少于1000个文件夹。 文件夹数超过此值会导致活动客户端出现性能问题。 您可以设置监视作业以计算文件夹、工作流等的数量，并定期报告。

此方法还突出显示创建过多对象的用户。

## 投放 {#deliveries}

该实例在任何时间应少于1000个投放。 拥有大量投放会占用数据库空间并产生问题。 每天创建10个以上投放的实例必须根据业务要求进行检查。 考虑使用连续投放创建更少投放。 如需详细信息，请参阅[此部分](../../workflow/using/continuous-delivery.md)。

应从实例中清除两年以上的投放。

## 文件 {#files}

应用程序服务器磁盘上的文件数不应无限增加。

导入工作流创建文件，因此导致磁盘扩展。 使用标准文件收集器活动可以防 [止](../../workflow/using/file-collector.md) 。 文件收集器将文件移动到临时文件夹并自动清除它们。

如果工作流导入文件但未使用标准功能，则需要清除该工作流才能将磁盘空间保持在最小。

## 交易数据和日志 {#transactional-data-and-logs}

将数 [据导入](../../workflow/using/data-life-cycle.md#work-table) 到Adobe Campaign的每个工作流程都会导致数据库的大小增大。

检查清除或清除工作流是否正在运行并有效清除记录。 必须清除所有事务数据和日志。 清理任务仅清除标准表： 跟踪和广泛的日志。 特定表必须由特定工作流清除。 Refer to [this section](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

通过检查记录的最旧创建日期来观察事务数据的老化。
