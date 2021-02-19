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

下表提供了由Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅[本节](../../reporting/using/delivery-reports.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>模式</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动符(recipientActivity)<br /> </td> 
   <td> 按时间段划分打开、单击和事务。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放吞吐量（吞吐量）<br /> </td> 
   <td> 投放吞吐量图表，以消息/小时和Mbits/s为单位。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 故障和弹回（错误）<br /> </td> 
   <td> 按原因和域跳出和非交付项。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(deliveryFeedback)<br /> </td> 
   <td> 跟踪收件人行为的关键指标摘要。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 移动投放的跟踪指示器。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览器(browserStatistics)<br /> </td> 
   <td> 单击消息的收件人使用的浏览器统计信息。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(deliveryForward)<br /> </td> 
   <td> 共享活动和邮件打开统计信息。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 热点单击（霍特尔）<br /> </td> 
   <td> 显示消息和叠加的点击率。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设验证报告(deliveryHexposition)<br /> </td> 
   <td> 显示有关投放假设验证的度量汇总。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放统计(statisticsPerDelivery)<br /> </td> 
   <td> 每个电子邮件域的统计信息(已处理的邮件、已传递的邮件、硬弹回、软弹回、点击、退订)。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivities)<br /> </td> 
   <td> 分析每个时段共享活动、打开和订阅。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪统计信息(trackingStatistics)<br /> </td> 
   <td> 打开、单击和事务处理率报表。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(deliverySending)<br /> </td> 
   <td> 投放指标摘要：目标、排除和消息已发送。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(deliveryStatistics)<br /> </td> 
   <td> 选定投放的摘要表：目标、排除和消息已发送。<br /> </td> 
   <td> nms:投放<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作系统(osStatistics)<br /> </td> 
   <td> 关于单击消息的收件人使用的操作系统的统计信息。<br /> </td> 
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

## 关于活动{#reports-on-campaigns}的报告

有关活动的报告涉及&#x200B;**nms:operation**&#x200B;表中的数据。

下表提供了由Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅[本节](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(operationRecipientActivity)<br /> </td> 
   <td> 按时间段划分的打开、点击和事务取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放吞吐量(operationThroughput)<br /> </td> 
   <td> 投放吞吐量图表（以邮件/小时和Mbit/s为单位）取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 活动费用(budgetOperationExpenses)<br /> </td> 
   <td> 详细显示活动行项目，具体取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 故障和弹回(operationErrors)<br /> </td> 
   <td> 按原因和域划分的弹回和非交付项取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的描述性分析，取决于MRM<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(operationFeedback)<br /> </td> 
   <td> 主要跟踪指标概述：“打开”、“单击”和“事务”取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(operationForward)<br /> </td> 
   <td> 共享活动和邮件打开统计信息取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设验证报告(operationHexposition)<br /> </td> 
   <td> 显示活动投放的假设验证度量汇总，具体取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivityOpt)<br /> </td> 
   <td> 每个时段共享活动、打开和订阅的分析取决于活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(operationStatistics)<br /> </td> 
   <td> 活动投放的摘要图表：目标、排除和消息已发送。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL并单击吞吐量(operationTopUrlDelivery)<br /> </td> 
   <td> 多数反应性URL和关联的点击流取决于活动。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 关于服务{#reports-on-services}的报告

有关服务的报告与&#x200B;**nms:service**&#x200B;表中的数据有关。

下表提供了由Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅相关指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 风扇购买(socialAccubrationsByWebapp)<br /> </td> 
   <td> 哪些Web应用程序支持潜在客户获取？ 取决于社交营销加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅划分(mobileAppDistribution)<br /> </td> 
   <td> 按移动应用程序划分活动订阅，具体取决于移动应用程序渠道加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅跟踪(subscriptionsProgress)<br /> </td> 
   <td> 订阅到信息服务的演化<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性率(socialReactionRate)<br /> </td> 
   <td> 最新投放的反应率是多少？ 取决于社交营销加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性率(mobileAppRyctibleRate)<br /> </td> 
   <td> 最新投放的反应性率取决于移动应用程序渠道加载项。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 预算报告{#budget-reports}

下表提供了由Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅[本节](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>模式</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 与项目(budgetProgramCost)关联的成本<br /> </td> 
   <td> 项目费用细目。<br /> </td> 
   <td> nms:项目<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算演变(budgetEvolution)<br /> </td> 
   <td> 按承付程度开列的预算费用演变。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算的累积演变(budgetCumulativeEvolution)<br /> </td> 
   <td> 按委员会<br />职等划分的累积预算费用的演变。 </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerBudget)<br /> </td> 
   <td> 成本行的描述分析。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorer)<br /> </td> 
   <td> 成本行的描述分析。<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerPlan)<br /> </td> 
   <td> 成本行的描述分析。<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerProgram)<br /> </td> 
   <td> 成本行的描述分析。<br /> </td> 
   <td> nms:项目<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算（预算）汇总表<br /> </td> 
   <td> 主要成本、费用类别和预算的快照。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 关于模拟{#reports-on-simulations}的报告

有关模拟的报告涉及&#x200B;**nms:模拟**&#x200B;表中的数据。

下表提供了由Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅相关指南。

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
   <td> 按级别划分优惠(offerSimulationRanking)<br /> </td> 
   <td> 模拟中优惠按级别划分。<br /> </td> 
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
   <td> 因模拟(dlvSimuLossSimu)<br />导致的排除概要 </td> 
   <td> 由于模拟导致的排除表。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 关于Web 应用程序{#reports-on-web-applications}的报告

有关Web 应用程序的报告与&#x200B;**nms:WebApp**&#x200B;表中的数据有关。

下表提供了由Adobe Campaign提供的内置报告。

有关这些报告内容的详细信息，请参阅[本节](../../web/using/about-web-applications.md)。

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
   <td> 主(surveyProperties)<br /> </td> 
   <td> 调查属性<br /> </td> 
  </tr> 
  <tr> 
   <td> 对响应的划分(surveyDistribution)<br /> </td> 
   <td> 对问题的答复的细目。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他ootb报告{#other-ootb-reports}

还内置了以下报告。 有关此问题的详细信息，请参阅他们所关心的功能文档。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>模式</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 优惠分析(offerAnalysis)<br /> </td> 
   <td> 优惠分析/日期和渠道，取决于Interaction加载项。<br /> </td> 
   <td> nms:优惠<br /> </td> 
  </tr> 
  <tr> 
   <td> 再营销效率（再营销效果）<br /> </td> 
   <td> 再营销效率的衡量<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 社交潜在客户获取的历史记录(socialVisitorStatistics)<br /> </td> 
   <td> Twitter和Facebook潜在客户获取的历史记录取决于Social marketing加载项。<br /> </td> 
   <td> nms:访客<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近提案跟踪(recentPropositions)<br /> </td> 
   <td> 实时命题跟踪<br /> </td> 
   <td> nms:compationRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

