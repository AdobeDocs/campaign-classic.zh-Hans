---
title: 投放
description: 进一步了解默认投放工作流
page-status-flag: never-activated
uuid: d323eb4d-937b-4b37-8400-942336f0a1b4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 37612f62-68c0-4f73-a9a1-6d017aab862f
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 15%

---


# 投放{#deliveries}

默认情况下，会安装下面详述的工作流。

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
   <td> 此工作流通过电子邮件将系统活动报告发送给“付费”操作员。 默认情况下每月25号触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">有效开单用户档案数</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>此工作流计算活动用户档案的数量。 默认情况下，每天晚上1点触发。</p> <p>“<strong>用户档案</strong>”是指代表最终客户或潜在客户的信息记录（例如 nmsRecipient 表或外部表中的记录，包含 cookie ID、客户 ID、移动标识符或与特定渠道相关的其他信息）。计费只涉及“活动”的用户档案。 如果用户档案在过去12个月内通过任何渠道被定向或传达，则用户档案被视为“活动”。</p> <p>Facebook 和 Twitter 渠道不包含在內。</p> <p>You can have an overview of the <span class="uicontrol">Number of active profiles</span> from the <span class="uicontrol">Administration</span> &gt; <span class="uicontrol">Campaign Management</span> &gt; <span class="uicontrol">Customer metrics</span> menu.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">别名清理</span> <br /> </td> 
   <td> <span class="uicontrol">aliasClecining</span> <br /> </td> 
   <td> 此工作流程实现了明细列表价值的标准化。 默认情况下，每天凌晨3点触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">可投放性更新</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> 通过此工作流，您可以创建弹回邮件资格规则的列表，以及平台中域和MX的列表。 仅当HTTPS端口打开时，此工作流才有效。 除非安装了可交付性模块，否则不更新这些列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">数据库清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>此工作流是数据库维护工作流：它根据部署助手中定义的配置从数据库中删除过时的数据，从而与统计和进程进行不同的计算。 默认情况下，每天凌晨4点触发。</p> <p>For more information, refer to this <a href="../../production/using/database-cleanup-workflow.md">page</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">暂停的工作流清除</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>此工作流会分析严重性设置为正常的已暂停工作流，并在暂停过长时触发警告和通知。 一个月后，暂停的技术工作流将被无条件停止。 默认情况下，每周一早上5点触发。</p> <p>有关详细信息，请参 <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">阅处理暂停的工作流</a>。</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">优惠通知</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> 此工作流将经过批准的优惠部署到在线环境以及优惠目录中包含的每个类别。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">预览</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> 此工作流会分析保存在临时日历中的投放（创建临时日志）。 默认情况下，每天凌晨1点触发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">跟踪</span> <br /> </td> 
   <td> <span class="uicontrol">跟踪</span> <br /> </td> 
   <td> 此工作流执行跟踪信息的恢复和合并。 它还确保重新计算跟踪和投放统计，特别是消息中心归档工作流使用的统计。 默认情况下，每小时触发一次。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

