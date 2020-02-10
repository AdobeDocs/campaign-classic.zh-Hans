---
title: 消息中心（执行）
seo-title: 消息中心（执行）
description: 消息中心（执行）
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 消息中心（执行）{#message-center-execution}

默认情况下，下面详细介绍的工作流 **随“消息中心——执行** ”模块一起安装。 For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

要了解有关如何配置与消息中心模块相关的技术工作流程的更多信息，请参 [阅本页](../../message-center/using/technical-workflows.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">更新活动状态</span><br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span><br /> </td> 
   <td> 通过此工作流，您可以为活动分配状态。 活动状态如下：<br /> 
    <ul> 
     <li> <p><strong>待定</strong>:该事件位于队列中。 尚未将消息模板关联到该模板。</p> </li> 
     <li> <p><strong>待交付</strong>:该事件位于队列中，消息模板已关联到该事件，并且当前正由交付处理。</p> </li> 
     <li> <p><strong>发送</strong>:此状态将从交付日志中复制。 这意味着送货已经送出。</p> </li> 
     <li> <p><strong>交付忽略</strong>:此状态将从交付日志中复制。 这意味着传送已被忽略。</p> </li> 
     <li> <p><strong>传送错误</strong>:此状态将从交付日志中复制。 这意味着交付失败了。</p> </li> 
     <li> <p><strong>未涵盖的活动</strong>:活动未能与消息模板关联。 不会重新处理该事件。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">处理批处理事件</span><br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span><br /> </td> 
   <td> 通过此工作流，您可以在将批处理事件与消息模板关联之前将它们放入队列中。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">处理实时事件</span><br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span><br /> </td> 
   <td> 通过此工作流，您可以在将实时事件与消息模板关联之前，将它们放入队列中。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

