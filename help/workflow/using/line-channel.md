---
title: LINE 渠道
seo-title: LINE 渠道
description: LINE 渠道
seo-description: null
page-status-flag: never-activated
uuid: 0b0e34b2-7ee9-456a-9ed9-7ede889584b6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 367314a2-eb6d-4710-8a47-5a51049ad924
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 13%

---


# LINE 渠道{#line-channel}

下面详细介绍的工作流默认 **情况下随LINE** 渠道模块一起安装。 For more on this module, refer to this [section](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LINE V2访问令牌更新</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> 此工作流将访问令牌刷新为LINE V2。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">删除阻止的LINE用户</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> 此工作流确保LINE V2用户在阻止LINE官方帐户180天后删除数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID到LineUserID迁移</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDM集成</span> <br /> </td> 
   <td> 此工作流生成LINE V2用户ID，用于从LINE V1迁移到LINE V2。<br /> </td> 
  </tr> 
 </tbody> 
</table>

