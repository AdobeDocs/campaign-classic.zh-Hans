---
solution: Campaign Classic
product: campaign
title: 报告列表
description: 报告列表
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 1%

---


# 报告列表{#list-of-reports}

## 投放报告 {#reports-on-deliveries}

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参 [阅本节](../../reporting/using/delivery-reports.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>模式</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(recipientActivity)<br /> </td> 
   <td> 按时间段划分打开、点击和事务。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放吞吐量（吞吐量）<br /> </td> 
   <td> 投放吞吐量图表，以消息／小时和Mbit/s为单位。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 失败和弹回（错误）<br /> </td> 
   <td> 按原因和域列出的退回和非交付项。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(deliveryFeedback)<br /> </td> 
   <td> 跟踪收件人行为的关键指标摘要。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 跟踪移动应用程序投放的指示器。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览器（浏览器统计）<br /> </td> 
   <td> 单击消息的收件人使用的浏览器统计信息。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(deliveryForward)<br /> </td> 
   <td> 共享活动和邮寄打开的统计信息。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 热点击（滚动）<br /> </td> 
   <td> 显示消息和叠加的点击率。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设验证报告(deliveryHextions)<br /> </td> 
   <td> 显示有关投放假设验证的度量摘要。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放统计(statisticsPerDelivery)<br /> </td> 
   <td> 每个电子邮件域的统计信息(已处理的邮件、已传送的邮件、硬弹回、软弹回、点击、退订)。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计(forwardActivities)<br /> </td> 
   <td> 分析每个时段共享活动、打开次数和订阅。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪统计信息(trackingStatistics)<br /> </td> 
   <td> 打开、单击和事务处理费率报表。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(deliverySending)<br /> </td> 
   <td> 投放指标摘要：目标、排除和消息发送。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(deliveryStatistics)<br /> </td> 
   <td> 所选投放的摘要表：目标、排除和消息发送。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作系统(osStatistics)<br /> </td> 
   <td> 关于单击消息的收件人所使用的操作系统的统计信息。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性率(deliveryFeedbackSocial)<br /> </td> 
   <td> 投放反应性率和反应击穿。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> URL并单击吞吐量(topUrlDelivery)<br /> </td> 
   <td> 最反应的URL和关联的点击流。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 活动报告 {#reports-on-campaigns}

有关活动的报告与nms:operation表 **中的数据** 有关。

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参 [阅本节](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(operationRecipientActivity)<br /> </td> 
   <td> 按时段划分的打开次数、点击次数和事务处理数取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放吞吐量(operationThroughput)<br /> </td> 
   <td> 投放吞吐量图表（以邮件／小时和Mbit/s为单位）取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 活动费用(budgetOperationExpenses)<br /> </td> 
   <td> 根据活动显示详细的活动行项目。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失败和弹回(operationErrors)<br /> </td> 
   <td> 按原因和域划分的弹回和非交付项取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的描述性分析取决于MRM。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(operationFeedback)<br /> </td> 
   <td> 主要跟踪指标概述：打开、单击和事务，取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(operationForward)<br /> </td> 
   <td> 共享活动和邮寄打开的统计信息取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设验证报告(operationHexposition)<br /> </td> 
   <td> 根据假设验证显示活动投放的活动度量摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivityOpt)<br /> </td> 
   <td> 每个时段共享活动、打开次数和订阅的分析取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(operationStatistics)<br /> </td> 
   <td> 活动投放的摘要图表：目标、排除和消息发送。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL并单击吞吐量(operationTopUrlDelivery)<br /> </td> 
   <td> 大多数反应式URL和关联的点击流取决于活动。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服务报告 {#reports-on-services}

有关服务的报告与nms:service表 **中的数据** 有关。

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参阅相关指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 粉丝赢取(socialAccubrationsByWebapp)<br /> </td> 
   <td> 哪些Web应用程序支持潜在客户获取？ 取决于社交营销附加项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅细分(mobileAppDistribution)<br /> </td> 
   <td> 每个移动应用程序的活动订阅的细分取决于移动应用程序渠道加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅跟踪（订阅进度）<br /> </td> 
   <td> 订阅向信息服务的演变<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性率(socialReactionRate)<br /> </td> 
   <td> 最新投放的反应率是多少？ 取决于社交营销附加项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性率(mobileAppRycmityRate)<br /> </td> 
   <td> 最新投放的反应性率取决于移动应用程序渠道加载项。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 预算报告 {#budget-reports}

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参 [阅本节](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>模式</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 与项目相关的成本（预算方案成本）<br /> </td> 
   <td> 项目成本细目。<br /> </td> 
   <td> nms:项目<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算演变(budgetEvolution)<br /> </td> 
   <td> 预算成本按承诺水平的演变。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算的累积演化(budgetCumulativeEvolution)<br /> </td> 
   <td> 按预算级别划分的累积预算成本的演变<br /> 。 </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerBudget)<br /> </td> 
   <td> 成本行的说明性分析。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行（预算浏览器）<br /> </td> 
   <td> 成本行的说明性分析。<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerPlan)<br /> </td> 
   <td> 成本行的说明性分析。<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerProgram)<br /> </td> 
   <td> 成本行的说明性分析。<br /> </td> 
   <td> nms:项目<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算（预算）汇总<br /> </td> 
   <td> 主要成本、费用类别和预算的快照。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模拟报告 {#reports-on-simulations}

有关模拟的报告与nms:模拟表 **中的数据** 有关。

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
   <td> 按级别划分优惠(offerSimulationRanking)<br /> </td> 
   <td> 模拟中优惠的细分（按级别）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 模拟摘要(dlvSimuLossSummary)<br /> </td> 
   <td> 模拟卷和排除的摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 重叠统计信息(dlvSimuOverlapping)<br /> </td> 
   <td> 投放目标重叠卷。<br /> </td> 
  </tr> 
  <tr> 
   <td> 因模拟引起的排除概要(dlvSimuLossSimu)<br /> </td> 
   <td> 由模拟引起的排除表。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web 应用程序报告 {#reports-on-web-applications}

有关Web 应用程序的报告与nms:WebApp表 **中的数据有关** 。

Adobe Campaign提供的内置报告位于下表中。

有关这些报告内容的详细信息，请参 [阅本节](../../web/using/about-web-applications.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 文档(surveyDictionary)<br /> </td> 
   <td> 调查结构的描述取决于调查管理器加载项。<br /> </td> 
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

还内置了以下报告。 有关此内容的详细信息，请参阅他们所关注的功能文档。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>模式</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠分析(offerAnalysis)<br /> </td> 
   <td> 优惠分析/日期和渠道取决于“交互”加载项。<br /> </td> 
   <td> nms:优惠<br /> </td> 
  </tr> 
  <tr> 
   <td> 再营销效率（再营销效果）<br /> </td> 
   <td> 再营销效率的衡量<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 社交潜在客户获取历史(socialVisitorStatistics)<br /> </td> 
   <td> Twitter和Facebook潜在客户获取的历史取决于社交营销加载项。<br /> </td> 
   <td> nms:访客<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近提案跟踪（最近提案）<br /> </td> 
   <td> 实时命题跟踪<br /> </td> 
   <td> nms：命题Rcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

