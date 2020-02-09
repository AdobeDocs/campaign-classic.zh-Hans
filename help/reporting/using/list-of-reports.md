---
title: 报告列表
seo-title: 报告列表
description: 报告列表
seo-description: null
page-status-flag: never-activated
uuid: 79a914d0-7828-4fe1-b1b7-b055d4bf1f82
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: 3e593527-5580-44ea-93dc-9084d862537e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7655cd93a7dc8ecd35cd379da350ad279cae725

---


# 报告列表{#list-of-reports}

## 有关交付的报告 {#reports-on-deliveries}

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参 [阅此部分](../../reporting/using/delivery-reports.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(recipientActivity)<br /> </td> 
   <td> 按时间段划分打开、单击和事务。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付吞吐量（吞吐量）<br /> </td> 
   <td> 传送吞吐量图表，以消息／小时和Mbit/s为单位。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 故障和弹回（错误）<br /> </td> 
   <td> 按原因和域列出的退回和非交付内容。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(deliveryFeedback)<br /> </td> 
   <td> 用于跟踪收件人行为的关键指标摘要。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 向移动应用程序传送的跟踪指示器。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览器(browserStatistics)<br /> </td> 
   <td> 单击消息的收件人使用的浏览器统计信息。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(deliveryForward)<br /> </td> 
   <td> 共享活动和邮件打开的统计信息。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 热点单击（滚动）<br /> </td> 
   <td> 显示消息和叠加的点击率。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设报告(deliveryHextions)<br /> </td> 
   <td> 显示有关交付假设的度量摘要。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付统计信息(statisticsPerDelivery)<br /> </td> 
   <td> 每个电子邮件域的统计信息（已处理的消息、已传送的消息、硬弹回、软弹回、点击、取消订阅）。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivities)<br /> </td> 
   <td> 分析每个时段的共享活动、打开次数和订阅。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪统计信息(trackingStatistics)<br /> </td> 
   <td> 打开、单击和事务处理率报告。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付摘要（delivery发送）<br /> </td> 
   <td> 交付指标摘要：目标、排除和发送的消息。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付摘要(deliveryStatistics)<br /> </td> 
   <td> 选定提交的汇总表：目标、排除和消息已发送。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作系统(osStatistics)<br /> </td> 
   <td> 关于单击消息的收件人使用的操作系统的统计信息。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性率(deliveryFeedbackSocial)<br /> </td> 
   <td> 投递反应性率和反应击穿。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> URL并单击吞吐量(topUrlDelivery)<br /> </td> 
   <td> 最活跃的URL和关联的点击流。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 营销活动报告 {#reports-on-campaigns}

有关营销活动的报告涉及 **nms:operation表中的数据** 。

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参 [阅此部分](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(operationRecipientActivity)<br /> </td> 
   <td> 按时间段划分的打开次数、点击次数和事务处理数取决于营销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付吞吐量(operationThroughput)<br /> </td> 
   <td> 投递吞吐量图表（以邮件／小时为单位）取决于营销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 营销活动费用(budgetOperationExpenses)<br /> </td> 
   <td> 根据营销活动详细显示营销活动行项目。<br /> </td> 
  </tr> 
  <tr> 
   <td> 故障和弹回(operationErrors)<br /> </td> 
   <td> 按原因和域划分的退回和非交付项取决于营销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的描述性分析取决于MRM。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(operationFeedback)<br /> </td> 
   <td> 关键跟踪指标概述：打开次数、点击次数和事务处理次数取决于营销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(operationForward)<br /> </td> 
   <td> 共享活动和邮件打开统计信息取决于营销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设报告（操作假设）<br /> </td> 
   <td> 根据营销活动显示营销活动提交的假设测量汇总。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivityOpt)<br /> </td> 
   <td> 分析每个时段的共享活动、打开次数和订阅次数取决于营销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付摘要(operationStatistics)<br /> </td> 
   <td> 营销活动提交的摘要图表：目标、排除和消息已发送。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL并单击吞吐量(operationTopUrlDelivery)<br /> </td> 
   <td> 大多数反应式URL和关联的点击流取决于营销活动。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服务报告 {#reports-on-services}

有关服务的报告涉及 **nms:service表中的数据** 。

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参阅相关指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 粉丝赢取(socialAccubriesByWebapp)<br /> </td> 
   <td> 哪些Web应用程序支持潜在客户获取？ 取决于社交营销附加组件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅细分(mobileAppDistribution)<br /> </td> 
   <td> 每个移动应用程序的活动订阅的细分取决于移动应用程序渠道加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅跟踪（订阅进度）<br /> </td> 
   <td> 信息服务订阅的演变<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性率(socialReactionRate)<br /> </td> 
   <td> 最近交货的反应率是多少？ 取决于社交营销附加组件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性率(mobileAppRactibilityRate)<br /> </td> 
   <td> 最新交付的反应性率取决于移动应用程序渠道加载项。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 预算报告 {#budget-reports}

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参 [阅此部分](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 与方案有关的费用（预算方案费用）<br /> </td> 
   <td> 计划费用细目。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算演变（预算演变）<br /> </td> 
   <td> 预算成本按承诺级别的变化。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算的累积演化(budgetCumulativeEvolution)<br /> </td> 
   <td> 按预算级别划分的累积预算成本的演变<br /> 。 </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerBudget)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行（预算浏览器）<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerPlan)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerProgram)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算（预算）摘要<br /> </td> 
   <td> 主要成本、费用类别和预算的快照。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 关于模拟的报告 {#reports-on-simulations}

有关仿真的报告涉及 **nms:simulation表中的数据** 。

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参阅相关指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 模拟排除的详细信息(dlvSimuLossDetail)<br /> </td> 
   <td> 排除原因的详细表。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按级别划分选件(offerSimulationRanking)<br /> </td> 
   <td> 按级别划分模拟中的选件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 模拟摘要(dlvSimuLossSummary)<br /> </td> 
   <td> 模拟卷和排除的摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 重叠统计信息(dlvSimuOverlapping)<br /> </td> 
   <td> 交付目标重叠卷。<br /> </td> 
  </tr> 
  <tr> 
   <td> 因模拟导致的排除概要(dlvSimuLossSimu)<br /> </td> 
   <td> 由模拟引起的排除表。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web应用程序报告 {#reports-on-web-applications}

有关Web应用程序的报告涉及 **nms:WebApp表中的数据** 。

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参 [阅此部分](../../web/using/about-web-applications.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 文档(surveyDictionary)<br /> </td> 
   <td> 调查结构的说明取决于调查管理器加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 主要（survey属性）<br /> </td> 
   <td> 调查属性<br /> </td> 
  </tr> 
  <tr> 
   <td> 答复细分(surveyDistribution)<br /> </td> 
   <td> 对问题的答复的细分。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他ootb报告 {#other-ootb-reports}

还提供了以下内置报告。 有关详细信息，请参阅他们所关注的功能文档。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠分析（优惠分析）<br /> </td> 
   <td> 根据日期和渠道分析优惠信息，具体取决于Interaction Add-on。<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> 再营销效率（再营销效果）<br /> </td> 
   <td> 再营销效率的衡量<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 社交潜在客户获取历史记录(socialVisitorStatistics)<br /> </td> 
   <td> Twitter和Facebook潜在客户收购的历史取决于社交营销加载项。<br /> </td> 
   <td> nms：访客<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近提议跟踪（最近提议）<br /> </td> 
   <td> 实时定位跟踪<br /> </td> 
   <td> nms：命题Rcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

