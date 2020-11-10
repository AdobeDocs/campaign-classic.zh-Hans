---
title: 传输到中间源
description: 了解有关传输到中间源工作流的更多信息
page-status-flag: never-activated
uuid: 6b5be5a0-d1ea-428b-a755-74dd34b1d53d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 57b873e9-e934-410b-b966-040cebd94e3e
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# 传输到中间源{#transfer-to-mid-sourcing}

下面详细介绍的工作流默认 **情况下随“传输到中间源** ”模块一起安装。 For more on this module, refer to this [section](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中间源(投放计数器)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>此工作流收集投放服务器上的计数信息。 计数信息包括一般投放指标，如发送的投放数等。</p> <p>不包括打开等跟踪信息。</p> <p>默认情况下，每十分钟触发一次。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中间源(投放日志)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> 此工作流在中间源服务器上收集投放日志。 默认情况下，每小时触发一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

