---
title: 交互
seo-title: 交互
description: 交互
seo-description: null
page-status-flag: never-activated
uuid: 5c8e2353-bb76-4e8d-95d7-61b6c111b6b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 1683477a-9233-4a25-b0d0-0c81051eb440
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# 交互{#interaction}

下面详细介绍的工作流默认 **情况下随优惠引擎** （交互）模块安装。 For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">完整聚合计算(propositionrcp多维数据集)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> 此工作流会更 <strong>新聚合</strong> 的“完 <strong>整优惠建议</strong> ”。 默认情况下，每天早上6点触发。 此聚合捕获以下维： 渠道、投放、营销优惠和日期。<br /> 然后 <strong>优惠建议</strong> 多维数据集用于根据优惠生成报表。 您可以在本节中进一步了 <a href="../../reporting/using/about-cubes.md">解多维数据集</a>。<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整聚合计算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

