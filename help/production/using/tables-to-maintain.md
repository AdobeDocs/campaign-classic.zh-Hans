---
solution: Campaign Classic
product: campaign
title: 要维护的表
description: 要维护的表
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---


# 要维护的表{#tables-to-maintain}

要维护的表的列表取决于Adobe Campaign的版本、使用方式和数据模型配置。

以下列表只包含最易碎的表。 影响如下：

* 磁盘空间过度消耗，从而影响数据库访问，
* 未定期更新的索引，这会降低查询性能。

## Adobe Campaign表 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表名称 </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>主要活动类型</strong><br /> </th> 
   <th> <strong>注释</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> 小<br /> </td> 
   <td> Updates<br /> </td> 
   <td> 每个投放操作有一条记录。 单个记录可以多次更新以反映投放进度，因此此表上的索引往往会快速分段。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 在准备投放时插入记录的工作表。 然后在投放期间更新它们，最后在投放完成后删除它们。<br /> 尽管平均大小相当有限，但此表往往会迅速碎裂。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 此表包含生成个性化镜像页面所需的信息。 它包含一个备忘录(CLOB)字段，因此它将非常大。 音量与保存的镜像页面历史直接成比例。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表包含有关投放进程的统计信息。 其记录会定期更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> 中<br /> </td> 
   <td> 更新、插入<br /> </td> 
   <td> 此表包含有关电子邮件地址的信息。 它经常作为隔离过程的一部分进行更新(记录是在第一个投放错误时创建的，在计数器发生更改时进行更新并在投放成功后删除)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 小<br /> </td> 
   <td> Updates<br /> </td> 
   <td> 每个工作流实例有一条记录，因此记录很少。 但是，会定期更新表，以反映状态和进展。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 工作流活动的每次执行都会导致在此表中创建记录。 清除机制会在它们过期后将其删除。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 在工作流中的任务之间激活的每个过渡都会导致在此表中创建记录。 清除机制会在它们过期后将其删除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 非常小 <br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表特定于工作流引擎。 它允许向工作流(例如开始、停止、暂停)发送命令。 尽管它很小，但在清除链接到工作流的事务表时，会考虑此表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 这是系统中最大的表。 每条消息发送一条记录，这些记录将被插入、更新以跟踪投放状态，并在清除历史记录时被删除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 跟踪日志在清除历史记录时被插入和删除，但不会更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> 小<br /> </td> 
   <td> Updates<br /> </td> 
   <td> 此表包含用于确认SMTP错误的信息。 它相当小，但会进行大量更新，因此此表上的索引往往会迅速分解。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表包含按域排序的SMTP错误聚合。 它最初包含详细信息，一旦过时，清理任务会汇总这些详细信息。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid(在中间源实例上)<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 仅当5.10（或更高版本）实例用作中间源实例时。 这是数据库中最大的表之一。 每条消息发送一条记录，这些记录将被插入、更新以跟踪投放状态，并在清除历史记录时被删除。 使用中间源时，建议限制历史记录（通常不到两个月），因此此表在大小（6000万行中小于30 Go，数据+索引）方面保持合理，但是不时重新构建它很重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp（当使用NmsRecipient表时） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 这是系统中最大的表。 每条消息发送一条记录，这些记录将被插入、更新以跟踪投放状态，并在清除历史记录时被删除。 请注意，在5.10中，此表比4.05(NmsBroadLog)中的等效表小，因为SMTP消息文本在5.10版本的NmsBroadLogMsg表中被分解。 但是，仍然必须定期（每隔一周）重新编制此表的索引，以便与之开始，并不时（每月一次，或当性能受到影响时）完全重建它。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx(当使用外部收件人表时)<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与NmsBroadLogRcp相同，但带有外部收件人表。 请将Yyy和Xxx与投放映射中的值进行调整。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp（当使用NmsRecipient表时） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 跟踪日志在清除历史记录时被插入和删除，但不会更新。 卷取决于数据保留的长度。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx(当使用外部收件人表时)<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 与NmsTrackingLogRcp相同，但带有外部收件人表。 请使用投放映射中使用的值调整Yyy和Xxx。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent(消息中心执行实例)<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与其他广播表相似，但与NmsRtEvent（而非NmsRecipient）一起使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent(消息中心执行实例)<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 与其他trackingLog表相似，但与NmsRtEvent表相似，而不是与NmsRecipient相同。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent(消息中心执行实例)<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 包含消息中心事件序列的表。 这些事件的状态由消息中心在处理时更新。 清除期间执行删除操作。 我们建议您定期重新创建此表的索引并重新构建它。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto(消息中心控制实例)<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与NmsRtEvent相似。 此表存档所有事件的每个执行实例。 它不由实时进程使用，只由报告使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> 非常小<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 包含移动应用程序及其配置的表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新<br /> </td> 
   <td> 包含用于发送通知的移动设备（地址）标识符的表(与收件人表类似)。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与其他广播表类似，但使用NmsappSubscriptionRcp而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 与其他trackingLog表相似，但使用NmsappSubscriptionRcp表而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 包含用户会话的表。 插入和删除的数量非常重要。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 客户表 {#customer-tables}

除了上述列表之外，在平台设置期间由客户创建(Adobe Campaign数据模型中不存在)的表也可能会碎片化，尤其是在数据加载或同步过程中频繁更新时。 这些表可以是默认Adobe Campaign数据模型(例如 **NmsRecipient**)的一部分。 在这种情况下，Adobe Campaign平台的管理员应对其特定数据库模型进行审核以找到这些自定义表。 这些表不一定在我们的维护过程中被明确提及。
