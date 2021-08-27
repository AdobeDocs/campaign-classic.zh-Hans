---
product: campaign
title: 互动
description: 互动
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 6%

---


# 互动{#interaction}

![](../../assets/common.svg)

默认情况下，下面详述的工作流随&#x200B;**选件引擎（交互）**&#x200B;加载项一起安装。

有关更多信息，请根据您的Campaign版本，参阅以下章节：

![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文档](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[  Campaign v8 文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


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
   <td> 此工作流更新<strong>Full</strong>多维数据集的<strong>选件建议</strong>聚合。 默认情况下，此工作流于每日早上6点触发。 此聚合会捕获以下维度：渠道、投放、营销选件和日期。<br /> 然后， <strong>选</strong> 件配置文件多维数据集用于根据选件生成报表。您可以在<a href="../../reporting/using/about-cubes.md">此部分</a>中了解有关多维数据集的更多信息。<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整聚合计算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 此工作流更新<strong>消息中心</strong>多维数据集的<strong>Full</strong>聚合。 默认情况下，此工作流于每日凌晨3点触发。 此聚合会捕获以下维度：渠道、日期、状态和事件类型。<br /> 然后， <strong>消</strong> 息中心多维数据集用于根据事件生成报告。您可以在<a href="../../reporting/using/about-cubes.md">此部分</a>中了解有关多维数据集的更多信息。<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

