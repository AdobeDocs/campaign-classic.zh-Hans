---
product: campaign
title: 投放
description: 了解有关默认投放工作流的更多信息
feature: Workflows
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 4%

---


# 投放{#deliveries}



默认情况下，下面详细介绍的工作流随&#x200B;**投放**&#x200B;模块一起安装。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">报告聚合</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> 此工作流可更新报告中使用的聚合。 默认情况下，此工作流每天凌晨2点触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">付费</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> 此工作流会通过电子邮件将系统活动报告发送给“billing”操作员。 默认情况下，它于每月25日触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">别名清理</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> 此工作流可标准化枚举值。 默认情况下，此工作流每天凌晨3点触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刷新可投放性</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> 利用此工作流，可创建退回邮件鉴别规则的列表，以及平台中域和MX的列表。 此工作流仅在HTTPS端口打开时有效。 除非安装了可投放性模块，否则不会更新这些列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">数据库清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>此工作流是数据库维护工作流：它进行的计算与统计和进程不同，并根据部署向导中定义的配置从数据库中删除过时的数据。 默认情况下，此工作流于每日凌晨4点触发。</p> <p>有关详细信息，请参阅此<a href="../../production/using/database-cleanup-workflow.md">页面</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">暂停的工作流清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>此工作流会分析严重性设置为正常的暂停工作流，并在暂停时间过长时触发警告和通知。 一个月后，暂停的技术工作流将无条件停止。 默认情况下，此工作流于每周一凌晨5点触发。</p> <p>有关详细信息，请参阅<a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">暂停工作流的处理</a>。</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">优惠通知</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> 此工作流将已批准的优惠以及优惠目录中包含的每个类别部署到在线环境中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">预测</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> 此工作流会分析保存在临时日历中的投放（创建临时日志）。 默认情况下，此工作流每天凌晨1点触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">跟踪</span> <br /> </td> 
   <td> <span class="uicontrol">跟踪</span> <br /> </td> 
   <td> 此工作流执行跟踪信息的恢复和整合。 它还确保重新计算跟踪和投放统计数据，特别是消息中心归档工作流使用的统计数据。 默认情况下，每小时触发一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

