---
product: campaign
title: 要维护的表
description: 要维护的表
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 3%

---

# 要维护的表{#tables-to-maintain}



要维护的表列表取决于您的Adobe Campaign版本、使用方式和数据模型配置。

以下列表只包含最容易出现片段的表。 影响如下：

* 磁盘空间过度消耗，从而影响数据库访问，
* 索引没有定期更新，这会降低查询性能。

## Adobe Campaign表 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表名 </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>主要活动类型</strong><br /> </th> 
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
   <td> 在投放准备期间将记录插入到其中的工作表。 它们随后在投放期间更新，并最终在投放完成后删除。<br /> 这张表倾向于快速碎片，尽管它的平均大小相当有限。<br /> </td> 
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
   <td> 更新，插入<br /> </td> 
   <td> 此表包含有关电子邮件地址的信息。 它经常作为隔离过程的一部分进行更新（记录是在第一次投放错误时创建的，当投放成功后计数器更改和删除时更新）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每个工作流实例都有一个记录，因此记录很少。 但表格会定期更新，以反映状态和进度。<br /> </td> 
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
   <td> 在工作流中的任务之间激活的每个过渡都会导致在此表中创建记录。 清除机制会在它们过期后将其删除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 非常小 <br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表特定于工作流引擎。 它允许向工作流发送命令（例如，开始、停止、暂停）。 尽管该表很小，但在清除链接到工作流的事务型表时也会考虑该表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 这是系统中最大的表。 每条发送的消息都有一条记录，这些记录会被插入、更新以跟踪投放状态，并在历史记录被清除时删除。 <br /> </td> 
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
   <td> 此表包含用于确认SMTP错误的信息。 索引相当小，但会被大规模更新，因此此表上的索引倾向于快速分段。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 此表包含按域排序的SMTP错误汇总。 它最初包含详细信息，一旦清除任务过期，便会将其汇总。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid（在中间源实例上）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 仅当5.10（或更高版本）实例用作中间源实例时。 这是数据库中最大的表之一。 每条发送的消息都有一条记录，这些记录会被插入、更新以跟踪投放状态，并在历史记录被清除时删除。 使用中间源时，建议限制历史记录（通常少于两个月），因此此表大小合理（对于6000万行，数据加索引，小于30 Go），但偶尔重建非常重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp（当使用NmsRecipient表时） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 这是系统中最大的表。 每条发送的消息都有一条记录，这些记录会被插入、更新以跟踪投放状态，并在历史记录被清除时删除。 请注意，在5.10中，此表比4.05中的等效表(NmsBroadLog)小，因为5.10版本的NmsBroadLogMsg表中已分解SMTP消息文本。 但是，仍必须定期（开始为每隔一周）重新索引此表，并不时地完全重建它（每月一次，或者当性能受到影响时）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyyBroadLogXxx（使用外部收件人表时）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、删除<br /> </td> 
   <td> 与NmsBroadLogRcp相同，但使用外部收件人表。 请使用投放映射中的值调整Yyyy和Xxx 。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp（当使用NmsRecipient表时） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 清除历史记录时会插入和删除跟踪日志，但不会更新这些日志。 卷取决于数据保留的长度。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyyTrackingLogXxx（当使用外部收件人表时）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、删除<br /> </td> 
   <td> 与NmsTrackingLogRcp相同，但使用外部收件人表。 请使用投放映射中使用的值调整Yyyy和Xxx。 <br /> </td> 
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
   <td> 与其他trackingLog表类似，但使用NmsRtEvent表而不是NmsRecipient。<br /> </td> 
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
   <td> 包含移动设备应用程序及其配置的表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新<br /> </td> 
   <td> 包含用于发送通知的移动设备的标识符（地址）的表（类似于收件人表）。<br /> </td> 
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

除了上述列表之外，包含在平台设置期间由客户创建的表(在Adobe Campaign数据模型中不存在)也可能会出现碎片，尤其是如果这些表在数据加载或同步过程中频繁更新。 这些表可以是默认Adobe Campaign数据模型的一部分(例如， **NmsRecipient**)。 在这种情况下，Adobe Campaign平台管理员需要对其特定数据库模型进行审核，以查找这些自定义表。 在我们的维护过程中不一定明确地提到这些表。
