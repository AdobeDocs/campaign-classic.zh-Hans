---
solution: Campaign Classic
product: campaign
title: 消息中心（控制）
description: 消息中心（控制）
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 7%

---


# 消息中心（控制）{#message-center-control}

下面详述的工作流计划每小时运行一次。 默认情况下，它随&#x200B;**消息中心 — Control**&#x200B;模块一起安装。 有关此模块的详细信息，请参阅此[部分](../../message-center/using/about-transactional-messaging.md)。

要详细了解如何配置与消息中心模块相关的技术工作流，请参阅[此页](../../message-center/using/technical-workflows.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 消息中心&lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> 此工作流：<br /> 
    <ul> 
     <li> <p>恢复由操作处理的事件的列表。</p> </li> 
     <li> <p>与NmsBroadLogMsg表同步以恢复投放消息资格。</p> </li> 
     <li> <p>一旦完成与NmsBroadLogMsg表的同步，将恢复事件投放日志。</p> </li> 
     <li> <p>与NmsTrackingUrl表同步，以恢复对投放URL的跟踪。</p> </li> 
     <li> <p>完成与NmsTrackingUrl表的同步后，立即恢复事件跟踪URL。</p> </li> 
     <li> <p>允许您在发送投放后每三小时恢复放入隔离的所有电子邮件地址。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

