---
solution: Campaign Classic
product: campaign
title: 互动
description: 互动
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: affc541c480ad7e618120fe90270841add06b711
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# 互动{#interaction}

下面详细介绍的工作流默认安装在&#x200B;**优惠引擎(Interaction)**&#x200B;模块中。 有关此模块的详细信息，请参阅此[部分](../../interaction/using/interaction-and-offer-management.md)。

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
   <td> 此工作流更新<strong>优惠建议</strong>多维数据集的<strong>Full</strong>聚合。 默认情况下，每天早上6点触发。 此聚合捕获以下维：渠道、投放、营销优惠和日期。<br /> 然后 <strong>使用</strong> 优惠配置多维数据集生成基于优惠的报表。您可以在<a href="../../reporting/using/about-cubes.md">本节</a>中进一步了解多维数据集。<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整聚合计算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 此工作流更新<strong>消息中心</strong>聚合的<strong>完整</strong>多维数据集。 默认情况下，每天凌晨3点触发。 此聚合捕获以下维：渠道、日期、状态和事件类型。<br /> 然后 <strong>使用</strong> 消息中心多维数据集生成基于事件的报表。您可以在<a href="../../reporting/using/about-cubes.md">本节</a>中进一步了解多维数据集。<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

