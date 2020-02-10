---
title: 消息中心（控制）
seo-title: 消息中心（控制）
description: 消息中心（控制）
seo-description: null
page-status-flag: never-activated
uuid: bdb3610b-a893-4e60-a9f7-f21d90b66919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 69e3e99f-d392-4316-926c-3c3c675415ad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 消息中心（控制）{#message-center-control}

下面详细介绍的工作流计划每小时运行一次。 默认情况下，它随消 **息中心——控制模块一起** 安装。 For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

要了解有关如何配置与消息中心模块相关的技术工作流程的更多信息，请参 [阅本页](../../message-center/using/technical-workflows.md)。

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
     <li> <p>恢复由操作处理的事件列表。</p> </li> 
     <li> <p>与NmsBroadLogMsg表同步，以恢复传送消息资格。</p> </li> 
     <li> <p>一旦与NmsBroadLogMsg表的同步完成，将恢复事件交付日志。</p> </li> 
     <li> <p>与NmsTrackingUrl表同步，以恢复对交付URL的跟踪。</p> </li> 
     <li> <p>完成与NmsTrackingUrl表的同步后，将立即恢复事件跟踪URL。</p> </li> 
     <li> <p>允许您在发送邮件后每三小时恢复隔离的所有电子邮件地址。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

