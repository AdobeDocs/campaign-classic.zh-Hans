---
product: campaign
title: 要维护的表
description: 要维护的表
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---

# 要维护的表{#tables-to-maintain}

![](../../assets/v7-only.svg)

要维护的表列表取决于您的Adobe Campaign版本、使用方式和数据模型配置。

以下列表仅包含最易碎的表。 影响如下：

* 磁盘空间过度消耗，从而影响数据库访问，
* 未定期更新的索引，这会降低查询性能。

## Adobe Campaign表 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表名称  </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>主要活动类型</strong><br /> </th> 
   <th> <strong>评论</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Small<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每个投放操作有一条记录。 单个记录可多次更新以反映投放进度，因此此表中的索引往往会快速分段。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 在投放准备期间插入记录的工作表。 然后，在投放期间更新这些量度，并在投放完成后最终将其删除。<br /> 虽然此表的平均大小相当有限，但它往往会迅速分解。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，删除<br /> </td> 
   <td> 此表包含生成个性化镜像页面所需的信息。 它包含一个Memo(CLOB)字段，因此它往往非常大。 卷与保留的镜像页面的历史记录成正比。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表包含有关投放过程的统计信息。 其记录会定期更新。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> 中<br /> </td> 
   <td> 更新，插入<br /> </td> 
   <td> 此表包含有关电子邮件地址的信息。 它经常作为隔离过程的一部分进行更新（记录在第一次投放错误时创建，在计数器发生更改时更新，并在投放成功后删除）。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Small<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每个工作流实例有一条记录，因此记录很少。 但是，会定期更新表以反映状态和进度。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Small<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 工作流活动的每次执行都会导致在此表中创建记录。 清除机制会在过期后删除它们。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Small<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 工作流中任务之间激活的每个过渡都会导致在此表中创建记录。 清除机制会在过期后删除它们。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 很小<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表专用于工作流引擎。 它允许向工作流（例如，开始、停止、暂停）发送命令。 尽管它很小，但在清除链接到工作流的事务表时会考虑此表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 这是系统中最大的表。 每个消息都发送一条记录，这些记录会被插入、更新以跟踪投放状态，并在清除历史记录时被删除。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，删除<br /> </td> 
   <td> 在清除历史记录后，将插入和删除跟踪日志，但不会更新它们。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Small<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 此表包含用于确定SMTP错误的信息。 它相当小，但会进行大量更新，因此此表中的索引往往会快速分割。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表包含按域排序的SMTP错误上的聚合。 它最初包含详细信息，在清理任务过期后，该信息会被清理任务聚合。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid（在中间源实例上）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 仅当5.10（或更高版本）实例用作中间源实例时。 这是数据库中最大的表之一。 每个消息都发送一条记录，这些记录会被插入、更新以跟踪投放状态，并在清除历史记录时被删除。 在使用中间源时，建议限制历史记录（通常不到两个月），因此此表在大小上保持合理（6000万行的访问量少于30,000万行，数据+索引），但是必须不时重建它。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp（使用NmsRecipient表时）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 这是系统中最大的表。 每个消息都发送一条记录，这些记录会被插入、更新以跟踪投放状态，并在清除历史记录时被删除。 请注意，在5.10中，此表小于4.05中的等效值(NmsBroadLog)，因为SMTP消息文本在5.10版的NmsBroadLogMsg表中被分解。 但是，必须定期（每隔一周）重新编制此表的索引，并不时（每月一次，或性能受到影响时）完全重建此表。<br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx（使用外部收件人表时）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与NmsBroadLogRcp相同，但与外部收件人表相同。 请将Yyy和Xxx与投放映射中的值进行调整。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp（使用NmsRecipient表时）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，删除<br /> </td> 
   <td> 在清除历史记录后，将插入和删除跟踪日志，但不会更新它们。 卷取决于数据保留的长度。<br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx（使用外部收件人表时）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，删除<br /> </td> 
   <td> 与NmsTrackingLogRcp相同，但与外部收件人表相同。 请调整Yyy和Xxx，并使用投放映射中使用的值。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent（消息中心执行实例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与其他broadlog表类似，但使用NmsRtEvent而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent（消息中心执行实例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，删除<br /> </td> 
   <td> 与其他trackingLog表类似，但使用NmsRtEvent表而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent（消息中心执行实例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 包含消息中心事件队列的表。 消息中心会在处理这些事件时更新这些事件的状态。 清除期间执行删除操作。 我们建议您定期重新创建此表的索引并重新生成此索引。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto（消息中心控制实例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与NmsRtEvent类似。 此表存档所有执行实例中的每个事件。 它仅由报表使用，不由实时进程使用。<br /> </td> 
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
   <td> 插入，更新<br /> </td> 
   <td> 该表包含用于发送通知的移动设备（地址）的标识符（类似于收件人表）。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与其他broadlog表类似，但使用NmsappSubscriptionRcp而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，删除<br /> </td> 
   <td> 与其他trackingLog表类似，但使用NmsappSubscriptionRcp表而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Small<br /> </td> 
   <td> 插入，删除<br /> </td> 
   <td> 包含用户会话的表。 插入和删除的次数非常重要。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 客户表 {#customer-tables}

除上面的列表外，客户在平台设置期间创建的(在Adobe Campaign数据模型中不存在)包含的表也可能会被分割，尤其是当这些表在数据加载或同步过程中经常更新时。 这些表可以是默认Adobe Campaign数据模型的一部分（例如&#x200B;**NmsRecipient**）。 在这种情况下，由Adobe Campaign平台的管理员对其特定数据库模型进行审核，以查找这些自定义表。 这些表不一定在我们的维护过程中明确提及。
