---
product: campaign
title: 消息中心（控制）
description: 消息中心（控制）
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 7%

---


# 消息中心（控制）{#message-center-control}

下面详述的工作流计划每小时运行一次。 默认情况下，它随&#x200B;**消息中心 — 控制**&#x200B;模块一起安装。 有关此模块的更多信息，请参阅此[部分](../../message-center/using/about-transactional-messaging.md)。

要详细了解如何配置与消息中心模块相关的技术工作流，请参阅[此页面](../../message-center/using/technical-workflows.md)。

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

