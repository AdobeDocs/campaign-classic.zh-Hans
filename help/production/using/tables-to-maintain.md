---
product: campaign
title: 要维护的表
description: 要维护的表
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 3%

---

# 要维护的表{#tables-to-maintain}



要维护的表列表取决于您的Adobe Campaign版本、使用方式和数据模型配置。

以下列表仅包含最容易出现片段的表。 影响如下：

* 磁盘空间过度消耗，从而影响数据库访问，
* 尚未定期更新的索引，这会减慢查询性能。

## Adobe Campaign表 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表名 </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>活动的主要类型</strong><br /> </th> 
   <th> <strong>评论</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每个投放操作都有一个记录。 单个记录可以更新多次以反映投放进度，因此此表上的索引往往会快速分段。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 在投放准备期间将记录插入到其中的工作表。 然后，在投放期间更新它们，最后在投放完成后将其删除。<br /> 这张表往往会很快碎裂，尽管它的平均大小相当有限。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 此表包含生成个性化镜像页面所需的信息。 它包含备忘录(CLOB)字段，因此往往非常大。 卷与保留镜像页面的历史记录成正比。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表包含有关投放过程的统计信息。 其记录定期更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> 中<br /> </td> 
   <td> 更新、插入<br /> </td> 
   <td> 此表包含有关电子邮件地址的信息。 在隔离过程中经常会更新该计数器（在第一次投放错误时创建记录，在计数器的更改时更新，并在投放成功后删除）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每个工作流实例都有一个记录，因此记录很少。 但是，该表会定期更新以反映状态和进度。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 每次执行工作流活动都会导致在此表中创建记录。 清除机制会在它们过期后将其删除。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 在工作流中的任务之间激活的每个过渡，都会导致在此表中创建记录。 清除机制会在它们过期后将其删除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 非常小 <br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表特定于工作流引擎。 它允许向工作流发送命令（例如，开始、停止、暂停）。 尽管此表很小，但在清除链接到工作流的事务表时也会考虑它。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 这是系统中最大的表。 每条发送的消息都有一条记录，这些记录会被插入、更新以跟踪投放状态，并在历史记录清除后删除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 清除历史记录时会插入和删除跟踪日志，但不会更新这些日志。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 此表包含用于确认SMTP错误的信息。 它的规模相当小，但会大规模更新，因此此表上的索引往往会快速分段。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表包含按域排序的SMTP错误汇总。 它最初包含详细信息，一旦清除任务过时，便会对其进行汇总。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid（在中间源实例上）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 仅当5.10（或更高版本）实例用作中间源实例时。 这是数据库中最大的表之一。 每条发送的消息都有一条记录，这些记录会被插入、更新以跟踪投放状态，并在历史记录清除后删除。 使用中间源时，建议限制历史记录（通常少于两个月），因此此表在大小上保持合理（对于6000万行，数据加索引，小于30 Go），但偶尔重建它非常重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp（当使用NmsRecipient表时） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 这是系统中最大的表。 每条发送的消息都有一条记录，这些记录会被插入、更新以跟踪投放状态，并在历史记录清除后删除。 请注意，在5.10中，此表比4.05中的相应表(NmsBroadLog)小，因为SMTP消息文本已在5.10版本的NmsBroadLogMsg表中分解。 但是，仍必须定期（从开始到每隔一周）重新索引此表，并不时地完全重建它（每月一次，或者当性能受到影响时）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyybroadLogXxx（使用外部收件人表时）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与NmsBroadLogRcp相同，但使用外部收件人表。 请使用投放映射中的值调整Yyy和Xxx。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp（当使用NmsRecipient表时） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 清除历史记录时会插入和删除跟踪日志，但不会更新这些日志。 卷取决于数据保留的长度。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyytrackingLogXxx（使用外部收件人表时）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 与NmsTrackingLogRcp相同，但使用外部收件人表。 请使用投放映射中使用的值来调整Yyy和Xxx。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent（消息中心执行实例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 类似于其他broadlog表，但使用NmsRtEvent而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent（消息中心执行实例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 类似于其他trackingLog表，但使用NmsRtEvent表而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent（消息中心执行实例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 包含消息中心事件队列的表。 消息中心在处理这些事件时更新其状态。 在清除期间执行删除。 我们建议您定期重新创建此表的索引并重建它。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto（消息中心控制实例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与NmsRtEvent类似。 此表存档所有执行实例中的每个事件。 无实时进程，仅供报告使用。<br /> </td> 
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
   <td> 包含用于发送通知的移动设备（地址）标识符的表（类似于收件人表）。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 类似于其他broadlog表，但使用NmsappSubscriptionRcp而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 类似于其他trackingLog表，但使用NmsappSubscriptionRcp表而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 包含用户会话的表。 插入和删除的次数非常重要。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Customer表 {#customer-tables}

除了上述列表之外，包含客户(在Adobe Campaign数据模型中不存在)在平台设置期间创建的表也可能会出现碎片，尤其是如果这些表在数据加载或同步过程中频繁更新。 这些表可以是默认Adobe Campaign数据模型的一部分(例如， **NmsRecipient**)。 在这种情况下，由Adobe Campaign平台管理员对其特定数据库模型进行审核，以查找这些自定义表。 在我们的维护过程中不一定明确地提到这些表。
