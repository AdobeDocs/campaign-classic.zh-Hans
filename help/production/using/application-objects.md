---
product: campaign
title: 应用程序对象
description: 应用程序对象
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---

# 应用程序对象{#application-objects}



应监控内置对象，并防止其增长过多非常重要。

## ID序列 {#sequence-of-ids}

Adobe Campaign使用的ID序列必须相应地使用： **xtkNewId**. 如果该序列使用非常快（即每天10万封），则必须验证它是否符合您的业务要求，例如每天发送数百万封电子邮件。 可以为特定表定义专用序列。 您可以设置一个工作流来监视ID使用情况。

当序列达到20多亿（确切数字为2,147,483,648）时，它会返回零。 必须避免这种情况，并造成问题，因此必须监控此序列。

要防止出现大表格的情况，请考虑使用特定序列。 这可以通过 **pkSequence** 属性。

创建大量日志的高频工作流将占用大量ID。 因此，强烈建议避免工作流中的日志过多和高频率。

如果序列已经循环，则最佳解决方案是从–2,147,483,648开始切换到负ID。

## 文件夹 {#folders}

任何实例上的文件夹应少于1000个。 文件夹数量超过此数量时，Campaign客户端可能会出现性能问题。 您可以设置一个监控作业来计算文件夹、工作流等的数量，并定期报告。

此方法还会突出显示创建过多对象的用户。

## 投放 {#deliveries}

实例上的投放数应随时少于1000次。 拥有大量投放会占用数据库空间并导致问题。 每天创建10个以上投放的实例必须根据业务需求进行检查。 考虑使用连续投放来创建更少的投放。 如需详细信息，请参阅[此部分](../../workflow/using/continuous-delivery.md)。

应从实例中清除两年以上的投放。

## 文件 {#files}

应用程序服务器磁盘上的文件数不应无限期地增加。

导入工作流会创建文件，从而导致磁盘扩展。 使用标准 [文件收集器](../../workflow/using/file-collector.md) 活动。 文件收集器将文件移动到临时文件夹并自动清除它们。

如果工作流导入文件而未使用标准功能，则需要清除该文件，以将磁盘空间保持在最小。

## 事务型数据和日志 {#transactional-data-and-logs}

每 [工作流](../../workflow/using/data-life-cycle.md#work-table) 将数据导入Adobe Campaign会导致数据库的大小增加。

检查清理或清除工作流是否正在运行并有效清除记录。 必须清除所有事务型数据和日志。 清理任务仅清除标准表：跟踪和广泛的日志。 特定表必须被特定工作流清除。 请参阅[此小节](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)。

通过检查记录的最早创建日期，观察事务型数据的时效性。
