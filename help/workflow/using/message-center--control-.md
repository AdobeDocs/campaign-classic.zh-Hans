---
product: campaign
title: 消息中心（控制）
description: 消息中心（控制）
feature: Workflows
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 10%

---


# 消息中心（控制）{#message-center-control}

![](../../assets/v7-only.svg)

下面详述的工作流计划每小时运行一次。 它随 **消息中心 — 控制** 模块。


有关更多信息，请根据您的Campaign版本，参阅以下章节：

![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文档](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[  Campaign v8 文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 消息中心 &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> 此工作流：<br /> 
    <ul> 
     <li> <p>取回由操作处理的事件列表。</p> </li> 
     <li> <p>与NmsBroadLogMsg表同步，以恢复投放消息的资格。</p> </li> 
     <li> <p>与NmsBroadLogMsg表同步完成后，立即恢复事件投放日志。</p> </li> 
     <li> <p>与NmsTrackingUrl表同步，以便恢复交付URL的跟踪。</p> </li> 
     <li> <p>完成与NmsTrackingUrl表的同步后，会立即恢复事件跟踪URL。</p> </li> 
     <li> <p>允许您在发送投放后每三小时恢复隔离的所有电子邮件地址。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

