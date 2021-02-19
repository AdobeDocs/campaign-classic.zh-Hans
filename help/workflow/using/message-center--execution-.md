---
solution: Campaign Classic
product: campaign
title: 消息中心（执行）
description: 消息中心（执行）
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# 消息中心（执行）{#message-center-execution}

默认情况下，下面详述的工作流随&#x200B;**消息中心 — 执行**&#x200B;模块一起安装。 有关此模块的详细信息，请参阅此[部分](../../message-center/using/about-transactional-messaging.md)。

要详细了解如何配置与消息中心模块相关的技术工作流，请参阅[此页](../../message-center/using/technical-workflows.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">更新事件状态</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> 通过此工作流，您可以为事件分配状态。 事件状态如下：<br /> 
    <ul> 
     <li> <p><strong>待定</strong>:事件在队列中。尚未与其关联消息模板。</p> </li> 
     <li> <p><strong>待处理投放</strong>:事件在队列中，消息模板已与其关联，当前正由投放处理。</p> </li> 
     <li> <p><strong>已发送</strong>:此状态将从投放日志中复制。这意味着投放已发送。</p> </li> 
     <li> <p><strong>被投放忽略</strong>:此状态将从投放日志中复制。这意味着投放被忽略了。</p> </li> 
     <li> <p><strong>投放错误</strong>:此状态将从投放日志中复制。这意味着投放失败了。</p> </li> 
     <li> <p><strong>事件未涵盖</strong>:事件未能与消息模板关联。不会重新处理事件。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">处理批次事件</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> 通过此工作流，您可以在将批次事件与消息模板关联之前，将其置于队列中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">处理实时事件</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> 通过此工作流，您可以在将实时事件与消息模板关联之前，将它们放入队列中。<br /> </td> 
  </tr> 
 </tbody> 
</table>

