---
product: campaign
title: 消息中心（执行）
description: 消息中心（执行）
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 5%

---


# 消息中心（执行）{#message-center-execution}



下面详细介绍的工作流将随 **消息中心 — 执行** 默认情况下为加载项。

有关更多信息，根据您的Campaign版本，请参阅以下章节：

![](assets/do-not-localize/v7.jpeg)[Campaign v7文档](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)

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
   <td> 利用此工作流，可为事件分配状态。 事件状态如下：<br /> 
    <ul> 
     <li> <p><strong>待处理</strong>：事件处于队列中。 尚未为其关联任何消息模板。</p> </li> 
     <li> <p><strong>待处理投放</strong>：事件处于队列中，已关联消息模板且投放当前正在处理该模板。</p> </li> 
     <li> <p><strong>已发送</strong>：此状态复制于投放日志。 这意味着投放已发送。</p> </li> 
     <li> <p><strong>已被投放忽略</strong>：此状态复制于投放日志。 这意味着该投放已被忽略。</p> </li> 
     <li> <p><strong>投放错误</strong>：此状态复制于投放日志。 这意味着投放已失败。</p> </li> 
     <li> <p><strong>未涵盖的事件</strong>：该事件未能与消息模板关联。 将不会重新处理该事件。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">处理批处理事件</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> 利用此工作流，可在将批量事件与消息模板关联之前将其放入队列中。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">处理实时事件</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> 通过此工作流，在将实时事件与消息模板关联之前，您可以先将它们放入队列中。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

