---
product: campaign
title: 传输到中间源
description: 了解有关传输到中间源工作流的更多信息
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 1%

---


# 传输到中间源{#transfer-to-mid-sourcing}



默认情况下，下面详述的工作流随&#x200B;**传输到中间源**&#x200B;模块一起安装。 有关此模块的详细信息，请参阅[Campaign Classic v7安装指南](../../installation/using/mid-sourcing-deployment.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中间源（投放计数器）</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>此工作流收集中间源服务器上投放的计数信息。 计数信息包括常规投放指标，如已发送的投放数量等。</p> <p>不包括打开等跟踪信息。</p> <p>默认情况下，每10分钟触发一次。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中间源（投放日志）</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> 此工作流在中间源服务器上收集投放日志。 默认情况下每小时触发一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

