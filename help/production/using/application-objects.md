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
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# 应用程序对象{#application-objects}

应该监控内置对象，防止它们过度增长非常重要。

## ID序列 {#sequence-of-ids}

Adobe Campaign使用的ID序列必须相应地使用： **xtkNewId**。 如果该序列消耗得非常快（即从每天100,000个开始），则必须验证其是否符合您的业务要求，如每天发送数百万封电子邮件。 可以为特定表定义专用序列。 您可以设置一个工作流来监视ID使用情况。

当序列达到20亿多个时（确切数字为2147483648），它会恢复为零。 必须避免这种情况并造成问题，这就是必须监测这一顺序的原因。

要防止在大表中出现这种情况，请考虑使用特定序列。 这可以通过架构中 **的pkSequence** 属性来完成。

创建大量日志的高频工作流将占用大量ID。 因此，强烈建议在工作流中避免日志过多和频率过高。

如果序列已循环，最好的解决方法是切换到负ID，从-2,147,483,648开始。

## 文件夹 {#folders}

任何实例上应少于1000个文件夹。 文件夹数大于此值会导致Campaign客户端出现性能问题。 您可以设置监视作业以计算文件夹、工作流等的数量，并定期报告回来。

此方法还突出显示创建过多对象的用户。

## 交付 {#deliveries}

实例随时应少于1000次提交。 大量交付会占用数据库空间并产生问题。 必须根据业务要求检查每天创建10个以上交货的实例。 考虑使用连续提交来创建更少的提交。 如需详细信息，请参阅[此部分](../../workflow/using/continuous-delivery.md)。

应从实例中清除两年以上的交货。

## 文件 {#files}

应用程序服务器磁盘上的文件数不应无限增加。

导入工作流会创建文件，因此会导致磁盘扩展。 使用标准“文件”(File)收集器活动可 [以防止这种情况](../../workflow/using/file-collector.md) 。 文件收集器将文件移到临时文件夹并自动清除它们。

如果工作流导入文件但未使用标准功能，则需要清除它以将磁盘空间保持在最小值。

## 交易数据和日志 {#transactional-data-and-logs}

将数 [据导入](../../workflow/using/executing-a-workflow.md#work-table) Adobe Campaign的每个工作流程都会导致数据库的大小增加。

检查是否正在运行清理或清除工作流并有效清除记录。 必须清除所有事务数据和日志。 清除任务仅清除标准表：跟踪和广泛的日志。 特定表必须由特定工作流清除。 Refer to [this section](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

通过检查记录的最早创建日期来观察交易数据的老化。
