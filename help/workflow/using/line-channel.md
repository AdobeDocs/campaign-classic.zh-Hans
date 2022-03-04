---
product: campaign
title: LINE 渠道
description: LINE 渠道
feature: Workflows
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 11%

---


# LINE 渠道{#line-channel}

![](../../assets/common.svg)

下面详述的工作流随 **LINE渠道** 模块。 有关此模块的更多信息，请参阅此 [部分](../../delivery/using/line-channel.md).

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
   <td> 此工作流将刷新LINE V2的访问令牌。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">删除已阻止的LINE用户</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> 此工作流可确保在LINE V2用户阻止LINE正式帐户180天后删除其数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">从MID迁移到LineUserID</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> 此工作流会生成从LINE V1迁移到LINE V2的LINE V2用户ID。<br /> </td> 
  </tr> 
 </tbody> 
</table>

