---
product: campaign
title: 消息中心（控制）
description: 消息中心（控制）
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 1%
---

# 消息中心（控制）{#message-center-control}



下面详细介绍的工作流计划每小时运行一次。 默认情况下，它与&#x200B;**消息中心 — Control**&#x200B;模块一起安装。


有关更多信息，根据您的Campaign版本，请参阅以下章节：

![](assets/do-not-localize/v7.jpeg) [Campaign v7文档](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png) [Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 消息中心&lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;外部帐户名称&gt;<br /> </td> 
   <td> 此工作流：<br /> 
    <ul> 
     <li> <p>恢复操作处理的事件列表。</p> </li> 
     <li> <p>与NmsBroadLogMsg表同步，以恢复投放消息资格。</p> </li> 
     <li> <p>与NmsBroadLogMsg表的同步完成后，立即恢复事件投放日志。</p> </li> 
     <li> <p>与NmsTrackingUrl表同步，以恢复对投放URL的跟踪。</p> </li> 
     <li> <p>与NmsTrackingUrl表的同步完成后，立即恢复事件跟踪URL。</p> </li> 
     <li> <p>用于在发送投放后，每三小时恢复一次所有被隔离的电子邮件地址。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

