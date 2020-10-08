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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 7%

---


# 消息中心（执行）{#message-center-execution}

下面详细介绍的工作流默认 **情况下随消息中心** -执行模块安装。 For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

要详细了解如何配置与消息中心模块相关的技术工作流，请参 [阅本页](../../message-center/using/technical-workflows.md)。

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
     <li> <p><strong>待定</strong>:事件在排队。 尚未与消息模板关联。</p> </li> 
     <li> <p><strong>待处理投放</strong>:事件在队列中，消息模板已与其关联，当前正由投放处理。</p> </li> 
     <li> <p><strong>发送</strong>:此状态从投放日志复制。 这意味着投放已被发送。</p> </li> 
     <li> <p><strong>投放忽略</strong>:此状态从投放日志复制。 这意味着投放被忽略了。</p> </li> 
     <li> <p><strong>投放错误</strong>:此状态从投放日志复制。 这意味着投放失败了。</p> </li> 
     <li> <p><strong>事件未涵盖</strong>:事件无法与消息模板关联。 不会重新处理事件。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">处理批次事件</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> 通过此工作流，您可以先将批次事件放入队列，然后再将其与消息模板关联。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">处理实时事件</span> <br /> </td> 
   <td> <span class="uicontrol">rtEvents处理</span> <br /> </td> 
   <td> 通过此工作流，您可以在将实时事件与消息模板关联之前，将它们放入队列中。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

