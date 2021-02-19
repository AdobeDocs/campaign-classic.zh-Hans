---
solution: Campaign Classic
product: campaign
title: 应用程序对象
description: 应用程序对象
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---


# 应用程序对象{#application-objects}

应该监控内置物体，防止它们增长过多很重要。

## ID序列{#sequence-of-ids}

Adobe Campaign使用必须相应使用的ID序列：**xtkNewId**。 如果该序列使用非常快（即从每天100,000个），您必须验证它是否符合您的业务要求，例如每天发送数百万封电子邮件。 可以为特定表定义专用序列。 您可以设置一个工作流来监视ID使用情况。

当序列达到20亿多（确切数字为2,147,483,648）时，它会回到零。 必须避免这种情况，并造成问题，因此必须监视这一顺序。

要防止对大表执行此操作，请考虑使用特定序列。 可以使用模式中的&#x200B;**pkSequence**&#x200B;属性执行此操作。

创建大量日志的高频工作流将消耗大量ID。 因此，强烈建议避免工作流中日志过多和频率过高。

如果序列已循环，则最佳解决方案是切换到负ID，从–2,147,483,648开始。

## 文件夹{#folders}

任何实例上应少于1000个文件夹。 拥有比这更多的文件夹可能会导致活动客户端出现性能问题。 您可以设置监视作业以计数文件夹、工作流等，并定期报告。

此方法还会突出显示创建过多对象的用户。

## 投放 {#deliveries}

该实例在任何时候应少于1000个投放。 拥有大量投放会占用数据库空间并产生问题。 每天创建10个以上投放的实例必须根据业务要求进行检查。 考虑使用连续投放来创建更少的投放。 如需详细信息，请参阅[此部分](../../workflow/using/continuous-delivery.md)。

应从实例中清除两年以上的投放。

## 文件{#files}

应用程序服务器磁盘上的文件数不应无限增加。

导入工作流会创建文件，因此会导致磁盘扩展。 使用标准[文件收集器](../../workflow/using/file-collector.md)活动可以防止这种情况。 文件收集器将文件移动到临时文件夹并自动清除它们。

如果工作流导入文件但未使用标准功能，则需要清除它，以将磁盘空间保持在最小。

## 事务数据和日志{#transactional-data-and-logs}

将数据导入Adobe Campaign的每个[工作流](../../workflow/using/data-life-cycle.md#work-table)都会导致数据库大小增大。

检查清除或清除工作流是否正在运行并有效清除记录。 必须清除所有事务数据和日志。 清理任务仅清除标准表：跟踪和广泛的日志。 特定表必须由特定工作流清除。 请参阅[此章节](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs) 。

通过检查记录的最旧创建日期来观察事务数据的老化。
