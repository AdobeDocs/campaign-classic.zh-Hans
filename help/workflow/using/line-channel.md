---
solution: Campaign Classic
product: campaign
title: LINE 渠道
description: LINE 渠道
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 11%

---


# LINE 渠道{#line-channel}

下面详细介绍的工作流默认安装在&#x200B;**LINE渠道**&#x200B;模块中。 有关此模块的详细信息，请参阅此[部分](../../delivery/using/line-channel.md)。

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
   <td> 此工作流确保在LINE V2用户阻止LINE官方帐户180天后删除其数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID到LineUserID迁移</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDM集成</span> <br /> </td> 
   <td> 此工作流生成LINE V2用户的ID，用于从LINE V1迁移到LINE V2。<br /> </td> 
  </tr> 
 </tbody> 
</table>

