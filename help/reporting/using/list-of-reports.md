---
product: campaign
title: 报告列表
description: 报告列表
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 报告列表{#list-of-reports}

![](../../assets/common.svg)

## 投放报告 {#reports-on-deliveries}

Adobe Campaign提供的内置报告可在下表中找到。

有关这些报表内容的更多信息，请参阅 [此部分](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(recipientActivity)<br /> </td> 
   <td> 按时间段划分打开数、点击数和交易记录。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放吞吐量（吞吐量）<br /> </td> 
   <td> 投放吞吐量图表，以消息/小时和Mbit/s为单位。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 失败和退回（错误）<br /> </td> 
   <td> 退回和无法交付项（按原因和域）。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指标(deliveryFeedback)<br /> </td> 
   <td> 用于跟踪收件人行为的关键指标摘要。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指示器(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 向移动应用程序投放的跟踪指示器。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览器(browserStatistics)<br /> </td> 
   <td> 点击消息的收件人使用的浏览器的统计资料。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(deliveryForward)<br /> </td> 
   <td> 共享活动和邮件打开统计信息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 热点点击（旋转）<br /> </td> 
   <td> 显示消息和叠加的点击率。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设验证报告(deliveryHexishopion)<br /> </td> 
   <td> 显示有关投放假设的测量摘要。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 传递统计信息(statisticsPerDelivery)<br /> </td> 
   <td> 每个电子邮件域的统计信息（已处理的消息、已投放的消息、硬退回、软退回、点击、退订）。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivities)<br /> </td> 
   <td> 每个时段共享活动、打开数和订阅数的分析。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪统计信息(trackingStatistics)<br /> </td> 
   <td> 打开、单击和交易费率报表。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(deliverySending)<br /> </td> 
   <td> 交付指标摘要：目标、排除和发送的消息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(deliveryStatistics)<br /> </td> 
   <td> 选定投放的摘要表：目标、排除项和已发送的消息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作系统(osStatistics)<br /> </td> 
   <td> 单击消息的收件人使用的操作系统的统计信息。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应率(deliveryFeedbackSocial)<br /> </td> 
   <td> 投放反应性率和反应破裂。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和点击吞吐量(topUrlDelivery)<br /> </td> 
   <td> 最反应的URL和关联的点击流。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 营销活动报告 {#reports-on-campaigns}

营销活动报表涉及 **nms：操作** 表。

Adobe Campaign提供的内置报告可在下表中找到。

有关这些报表内容的更多信息，请参阅 [此部分](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用户活动(operationRecipientActivity)<br /> </td> 
   <td> 按时间段划分的打开数、点击数和交易记录，取决于促销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放吞吐量(operationThroughput)<br /> </td> 
   <td> 投放吞吐量图表（以邮件/小时和Mbit/s为单位）取决于促销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 促销活动费用(budgetOperationExpenses)<br /> </td> 
   <td> 根据营销活动，显示营销活动行项目的详细信息。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失败和退回(operationErrors)<br /> </td> 
   <td> 退回和无法交付项（按原因和域）取决于Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的描述性分析取决于MRM。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪指标(operationFeedback)<br /> </td> 
   <td> 关键跟踪指标概述：打开数、点击数和交易数取决于促销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享到社交网络(operationForward)<br /> </td> 
   <td> 共享活动和邮件打开统计信息取决于Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 假设验证报告（操作假设）<br /> </td> 
   <td> 显示营销活动投放假设测量的摘要，具体取决于营销活动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享活动统计信息(forwardActivityOpt)<br /> </td> 
   <td> 分享活动、每个时间段的打开数和订阅数的分析取决于Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放摘要(operationStatistics)<br /> </td> 
   <td> 营销活动投放的摘要图表：目标、排除项和已发送的消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和点击吞吐量(operationTopUrlDelivery)<br /> </td> 
   <td> 大多数反应式URL和关联的点击流取决于促销活动。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服务报告 {#reports-on-services}

有关服务的报告涉及 **nms:service** 表。

Adobe Campaign提供的内置报告可在下表中找到。

有关这些报表内容的更多信息，请参阅相关指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 粉丝获取(socialAcquisitionsByWebapp)<br /> </td> 
   <td> 哪些Web应用程序支持潜在客户获取？ 取决于社交营销加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅细分(mobileAppDistribution)<br /> </td> 
   <td> 每个移动设备应用程序的活动订阅的划分取决于移动设备应用程序渠道加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅跟踪(subscriptionsProgress)<br /> </td> 
   <td> 信息服务订阅的演变<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性比率(socialReactionRate)<br /> </td> 
   <td> 最新投放的反应率是多少？ 取决于社交营销加载项。<br /> </td> 
  </tr> 
  <tr> 
   <td> 反应性比率(mobileAppRictiveRate)<br /> </td> 
   <td> 最新投放的反应率取决于移动设备应用程序渠道加载项。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 预算报表 {#budget-reports}

Adobe Campaign提供的内置报告可在下表中找到。

有关这些报表内容的更多信息，请参阅 [此部分](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 与方案有关的费用(budgetProgramCost)<br /> </td> 
   <td> 方案费用细目。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算演变(budgetEvolution)<br /> </td> 
   <td> 按承诺水平开列的预算费用演变。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算的累积演变(budgetCumulativeEvolution)<br /> </td> 
   <td> 按预算分摊的累计预算费用的演变<br /> 部门级别。 </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerBudget)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorer)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerPlan)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 浏览成本行(budgetExplorerProgram)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 预算（预算）汇总表<br /> </td> 
   <td> 主要成本、费用类别和预算的快照。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模拟报告 {#reports-on-simulations}

模拟报表涉及 **nms：模拟** 表。

Adobe Campaign提供的内置报告可在下表中找到。

有关这些报表内容的更多信息，请参阅相关指南。

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
   <td> 按排名划分选件(offerSimulationRanking)<br /> </td> 
   <td> 模拟中按排名划分选件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 模拟摘要(dlvSimuLossSummary)<br /> </td> 
   <td> 模拟卷和排除项的摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 重叠统计(dlvSimuOverlapping)<br /> </td> 
   <td> 交付目标卷重叠。<br /> </td> 
  </tr> 
  <tr> 
   <td> 因模拟(dlvSimuLossSimu)导致的排除概要<br /> </td> 
   <td> 模拟导致的排除项表。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web应用程序报告 {#reports-on-web-applications}

Web应用程序报表涉及 **nms:WebApp** 表。

Adobe Campaign提供的内置报告可在下表中找到。

有关这些报表内容的更多信息，请参阅 [此部分](../../web/using/about-web-applications.md).

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
   <td> 主要(surveyProperties)<br /> </td> 
   <td> 调查属性<br /> </td> 
  </tr> 
  <tr> 
   <td> 响应的划分(surveyDistribution)<br /> </td> 
   <td> 对问题的回答的划分。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他ootb报告 {#other-ootb-reports}

还提供了以下内置报告。 有关更多信息，请参阅相关功能文档。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签和内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
   <td> <strong>架构</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 选件分析(offerAnalysis)<br /> </td> 
   <td> 按日期和渠道进行选件分析，具体取决于交互加载项。<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> 再营销效率（再营销效果）<br /> </td> 
   <td> 再营销效率的衡量<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 社交潜在客户获取历史记录(socialVisitorStatistics)<br /> </td> 
   <td> twitter和Facebook潜在客户获取的历史取决于社交营销附加组件。<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近的建议跟踪(recentPropositions)<br /> </td> 
   <td> 实时建议跟踪<br /> </td> 
   <td> nms:campationRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
