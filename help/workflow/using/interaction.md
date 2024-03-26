---
product: campaign
title: 交互
description: 交互
feature: Workflows, Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 7%

---


# 交互{#interaction}



下面详细介绍的工作流将随 **优惠引擎（交互）** 默认情况下为加载项。

有关更多信息，根据您的Campaign版本，请参阅以下章节：

![](assets/do-not-localize/v7.jpeg)[Campaign v7文档](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">完全聚合计算（propositionrcp多维数据集）</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> 此工作流会更新 <strong>完整</strong> 的聚合 <strong>优惠建议</strong> 多维数据集。 默认情况下，此工作流于每日早上6点触发。 此聚合可捕获以下维度：渠道、投放、营销选件和日期。<br /> 此 <strong>优惠建议</strong> 然后，使用多维数据集根据选件生成报表。 有关多维数据集的更多信息，请参阅 <a href="../../reporting/using/ac-cubes.md">本节</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完全聚合计算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 此工作流会更新 <strong>完整</strong> 的聚合 <strong>消息中心</strong> 多维数据集。 默认情况下，此工作流于每日凌晨3点触发。 此聚合捕获以下维度：渠道、日期、状态和事件类型。<br /> 此 <strong>消息中心</strong> 然后，使用多维数据集根据事件生成报告。 有关多维数据集的更多信息，请参阅 <a href="../../reporting/using/ac-cubes.md">本节</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

