---
solution: Campaign Classic
product: campaign
title: 投放
description: 进一步了解默认投放工作流
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 7cd76b5a31ed9fc0e64a650316ea29293c628233
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 15%

---


# 投放{#deliveries}

默认情况下，下面详述的工作流随&#x200B;**投放**&#x200B;模块一起安装。

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
   <td> 此工作流更新报表中使用的聚合。 默认情况下，每天凌晨2点触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">付费</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> 此工作流通过电子邮件将系统活动报告发送给“付费”操作员。 默认情况下，每月25日触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">帐单(有效用户档案)</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>此工作流会计算活动用户档案的数量。 默认情况下，每晚1点触发。</p> <p>“<strong>用户档案</strong>”是指代表最终客户或潜在客户的信息记录（例如 nmsRecipient 表或外部表中的记录，包含 cookie ID、客户 ID、移动标识符或与特定渠道相关的其他信息）。计费仅涉及“活动”的用户档案。 如果用户档案在过去12个月内通过任何渠道成为目标或传达信息，则用户档案被视为“活动”。</p> <p>Facebook 和 Twitter 渠道不包含在內。</p> <p>您可以从<span class="uicontrol">管理</span> &gt; <span class="uicontrol">活动管理</span> &gt; <span class="uicontrol">客户量度</span>菜单查看<span class="uicontrol">活动用户档案数</span>。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">别名清理</span> <br /> </td> 
   <td> <span class="uicontrol">aliasClacining</span> <br /> </td> 
   <td> 此工作流程实现了明细列表价值的标准化。 默认情况下，每天在凌晨3点触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">可投放性更新</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> 通过此工作流，您可以创建跳出邮件资格规则的列表，以及平台中域和MX的列表。 仅当HTTPS端口打开时，此工作流才有效。 除非安装了可交付性模块，否则不会更新这些列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">数据库清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>此工作流是数据库维护工作流：它根据部署助手中定义的配置从数据库中删除过时的数据，从而与统计数据和进程进行不同的计算。 默认情况下，每天凌晨4点触发。</p> <p>有关详细信息，请参阅此<a href="../../production/using/database-cleanup-workflow.md">页面</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">暂停的工作流清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>此工作流会分析严重性设置为正常的已暂停工作流，并在暂停过长时触发警告和通知。 一个月后，暂停的技术工作流将无条件停止。 默认情况下，每周一早上5点触发。</p> <p>有关详细信息，请参阅<a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">处理暂停的工作流</a>。</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">优惠通知</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> 此工作流将批准的优惠部署到联机环境以及优惠目录中包含的每个类别。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">预测</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> 此工作流会分析保存在临时日历中的投放（创建临时日志）。 默认情况下，每天在凌晨1点触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">跟踪</span> <br /> </td> 
   <td> <span class="uicontrol">跟踪</span> <br /> </td> 
   <td> 此工作流执行跟踪信息的恢复和合并。 它还可以确保重新计算跟踪和投放统计，特别是消息中心归档工作流使用的统计。 默认情况下，每小时触发一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

