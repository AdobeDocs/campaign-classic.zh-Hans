---
product: campaign
title: 报告列表
description: 报告列表
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 2%

---

# 报告列表{#list-of-reports}



## 投放报告 {#reports-on-deliveries}

下表显示了Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅[此部分](../../reporting/using/delivery-reports.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(recipientActivity)<br /> </td> 
   <td> 按时间段划分打开、点击和交易。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放吞吐量（吞吐量）<br /> </td> 
   <td> 传递吞吐量图表，以消息/小时和Mbits/s为单位。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 失败和退回（错误）<br /> </td> 
   <td> 退回和无法按原因和域分类。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指标(deliveryFeedback)<br /> </td> 
   <td> 用于跟踪收件人行为的关键指标摘要。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 跟踪传递到移动应用程序的投放指示器。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览器(browserStatistics)<br /> </td> 
   <td> 点击邮件的收件人使用的浏览器统计信息。<br /> </td> 
   <td> xtk：none<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(deliveryForward)<br /> </td> 
   <td> 共享活动和邮件打开统计信息。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 热门点击(hoturls)<br /> </td> 
   <td> 显示消息和叠加的点击率。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设验证报告(deliveryHypothesis)<br /> </td> 
   <td> 显示有关投放假设的度量摘要。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放统计信息(statisticsPerDelivery)<br /> </td> 
   <td> 每个电子邮件域的统计信息（已处理邮件、已送达邮件、硬退回、软退回、点击次数、取消订阅）。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivities)<br /> </td> 
   <td> 分析每个时间段的共享活动、打开次数和订阅。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪统计信息(trackingStatistics)<br /> </td> 
   <td> 打开、单击和交易费率报表。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(deliverySending)<br /> </td> 
   <td> 传递指示器的摘要：目标、排除项和已发送的消息。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(deliveryStatistics)<br /> </td> 
   <td> 所选投放的摘要表：“目标”、“排除项”和“发送的消息”。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作系统(osStatistics)<br /> </td> 
   <td> 点击邮件的收件人使用的操作系统的统计信息。<br /> </td> 
   <td> xtk：none<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应率(deliveryFeedbackSocial)<br /> </td> 
   <td> 投放反应率和反应细分。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和点击吞吐量(topUrlDelivery)<br /> </td> 
   <td> 大多数反应URL和相关联的点击流。<br /> </td> 
   <td> nms：delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 营销活动报表 {#reports-on-campaigns}

营销活动报表涉及&#x200B;**nms：operation**&#x200B;表中的数据。

下表显示了Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅[此部分](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(operationRecipientActivity)<br /> </td> 
   <td> 按时段划分的打开、点击和交易，取决于促销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 传递吞吐量(operationThroughput)<br /> </td> 
   <td> 以邮件/小时和Mbits/s表示的投放吞吐量图表取决于Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 营销活动费用(budgetOperationExpenses)<br /> </td> 
   <td> 显示详细的促销活动行项目，具体取决于促销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失败和退回(operationErrors)<br /> </td> 
   <td> 退回和无法按原因和域交付，具体取决于Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的描述性分析，取决于MRM。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(operationFeedback)<br /> </td> 
   <td> 关键跟踪指标的概述：打开数、点击数和交易数，取决于促销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(operationForward)<br /> </td> 
   <td> 共享活动和邮件打开统计信息，取决于营销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设验证报告(operationHypothesis)<br /> </td> 
   <td> 显示Campaign投放的假设验证测量摘要，具体取决于Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivityOpt)<br /> </td> 
   <td> 对共享活动、打开次数和每个时间段的订阅的分析取决于Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(operationStatistics)<br /> </td> 
   <td> 活动投放的摘要图表：目标、排除项和发送的消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和点击吞吐量(operationTopUrlDelivery)<br /> </td> 
   <td> 大多数被反应的URL和相关联的点击流，都取决于Campaign。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服务报表 {#reports-on-services}

服务报表涉及&#x200B;**nms：service**&#x200B;表中的数据。

下表显示了Adobe Campaign提供的内置报告。

有关这些报告内容的更多信息，请参阅相关指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 粉丝赢取(socialAcquisitionsByWebapp)<br /> </td> 
   <td> 哪些Web应用程序支持了潜在客户收购？ 依赖社交营销加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅(mobileAppDistribution)<br />的细分 </td> 
   <td> 每个移动应用程序的活动订阅细分，取决于移动应用程序渠道加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅跟踪(subscriptionsProgress)<br /> </td> 
   <td> 信息服务订阅的演变<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应率(socialReactionRate)<br /> </td> 
   <td> 最新投放的反应率是多少？ 依赖社交营销加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应率(mobileAppReactivityRate)<br /> </td> 
   <td> 最新投放的反应率，取决于移动设备应用程序渠道加载项。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 预算报表 {#budget-reports}

下表显示了Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅[此部分](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 链接到方案的成本(budgetProgramCost)<br /> </td> 
   <td> 方案成本细目。<br /> </td> 
   <td> nms：program<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算演变(budgetEvolution)<br /> </td> 
   <td> 按承诺级别列出的预算成本的演变。<br /> </td> 
   <td> nms：budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算的累积演变(budgetCumulativeEvolution)<br /> </td> 
   <td> 按承诺<br />分段级别细分的累计预算成本的演变。 </td> 
   <td> nms：budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerBudget)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms：budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorer)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms：costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerPlan)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms：plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerProgram)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms：program<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算（预算）摘要<br /> </td> 
   <td> 主要成本、费用类别和预算的快照。<br /> </td> 
   <td> nms：budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模拟报表 {#reports-on-simulations}

模拟报告涉及&#x200B;**nms：simulation**&#x200B;表中的数据。

下表显示了Adobe Campaign提供的内置报告。

有关这些报告内容的更多信息，请参阅相关指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 模拟排除的详细信息(dlvSimuLossDetail)<br /> </td> 
   <td> 排除所有原因的详细表。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按等级(offerSimulationRanking)<br />划分优惠 </td> 
   <td> 模拟中的优惠细分，按等级<br /> </td> 
  </tr> 
  <tr> 
   <td> 模拟摘要(dlvSimuLossSummary)<br /> </td> 
   <td> 模拟卷和排除项摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 重叠统计信息(dlvSimuOverlaying)<br /> </td> 
   <td> 传递目标重叠卷。<br /> </td> 
  </tr> 
  <tr> 
   <td> 模拟排除的摘要(dlvSimuLossSimu)<br /> </td> 
   <td> 模拟导致的排除项表。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web应用程序报表 {#reports-on-web-applications}

有关Web应用程序的报表涉及&#x200B;**nms：WebApp**&#x200B;表中的数据。

下表显示了Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅[此部分](../../web/using/about-web-applications.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 文档（调查词典）<br /> </td> 
   <td> 调查结构的描述，取决于调查管理器加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 主要(surveyProperties)<br /> </td> 
   <td> 调查属性<br /> </td> 
  </tr> 
  <tr> 
   <td> 响应的细目(surveyDistribution)<br /> </td> 
   <td> 对问题的答复的细目。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他ootb报告 {#other-ootb-reports}

内置提供了以下报告。 有关更多信息，请参阅有关其相关功能的文档。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠分析(offerAnalysis)<br /> </td> 
   <td> 每个日期和渠道的优惠分析，取决于交互加载项。<br /> </td> 
   <td> nms：offer<br /> </td> 
  </tr> 
  <tr> 
   <td> 再营销效率(remarketingEffect)<br /> </td> 
   <td> 衡量再营销效率<br /> </td> 
   <td> nms：webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 社交潜在客户获取的历史(socialVisitorStatistics)<br /> </td> 
   <td> X(以前称为Twitter)和Facebook潜在客户收购的历史记录取决于Social营销附加产品。<br /> </td> 
   <td> nms：visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近建议跟踪(recentPropositions)<br /> </td> 
   <td> 实时建议跟踪<br /> </td> 
   <td> nms：propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
