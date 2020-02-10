---
title: 转移至中间采购
seo-title: 转移至中间采购
description: 转移至中间采购
seo-description: null
page-status-flag: never-activated
uuid: 6b5be5a0-d1ea-428b-a755-74dd34b1d53d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 57b873e9-e934-410b-b966-040cebd94e3e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 转移至中间采购{#transfer-to-mid-sourcing}

默认情况下，下面详细介绍的工作流 **会随“转移到中间采购** ”模块一起安装。 For more on this module, refer to this [section](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中间采购（交货计数器）</span><br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span><br /> </td> 
   <td> <p>此工作流会收集在中间采购服务器上的交货的计数信息。 计数信息包括一般的传送指标，如发送的传送数量等。</p> <p>不包括打开等跟踪信息。</p> <p>默认情况下，每10分钟触发一次。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中间采购（交付日志）</span><br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span><br /> </td> 
   <td> 此工作流在中间采购服务器上收集交付日志。 默认情况下，每小时触发一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

