---
title: 线路渠道
seo-title: 线路渠道
description: 线路渠道
seo-description: null
page-status-flag: never-activated
uuid: 0b0e34b2-7ee9-456a-9ed9-7ede889584b6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 367314a2-eb6d-4710-8a47-5a51049ad924
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 线路渠道{#line-channel}

下面详细介绍的工作流默认情况下随 **LINE通道模块一起安装** 。 For more on this module, refer to this [section](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LINE V2访问令牌更新</span><br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> 此工作流将访问令牌刷新为LINE V2。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">删除已阻止的LINE用户</span><br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> 此工作流确保在LINE V2用户阻止LINE正式帐户180天后删除其数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID到LineUserID迁移</span><br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span><br /> </td> 
   <td> 此工作流会生成LINE V2用户的ID，以便从LINE V1迁移到LINE V2。<br /> </td> 
  </tr> 
 </tbody> 
</table>

