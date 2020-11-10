---
title: 隐私数据保护规定工作流
description: 进一步了解隐私数据保护规定工作流
page-status-flag: never-activated
uuid: cb5f5d79-52ac-4ce4-abc7-a3a1f0a001cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 050c804e-87b7-4d68-b787-c396fec329d2
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 10%

---


# 隐私数据保护规定{#general-data-protection-regulation-gdpr}

下面详述的工作流默认随 **隐私数据保护规** 定模块安装。 For more on this module, refer to this [article](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">收集隐私请求</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> 此工作流生成存储在Adobe Campaign中的收件人数据，并在隐私请求的屏幕中提供下载。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">删除隐私请求数据</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> 此工作流将删除收件人中存储的Adobe Campaign数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">隐私请求清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> 此工作流会删除90天以前的访问请求文件。<br /> </td> 
  </tr> 
 </tbody> 
</table>

