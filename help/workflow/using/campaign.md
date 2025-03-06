---
product: campaign
title: 营销活动
description: 营销活动
feature: Workflows
hide: true
hidefromtoc: true
topic-tags: technical-workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# 营销活动{#campaign}



默认情况下，下面详细介绍的工作流将与&#x200B;**Campaign**&#x200B;模块一起安装。 有关此模块的详细信息，请参阅此[部分](../../campaign/using/designing-marketing-campaigns.md)。

>[!CAUTION]
>
>为了在营销活动级别执行营销活动流程，必须启动这些工作流。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">成本计算</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> 此工作流开始计算预算、计划、方案、营销活动、投放和任务中的费用和成本行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">库存：订单和警报</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> 此工作流在订单行上启动库存计算，并管理警告警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> 营销活动中的投放<span class="uicontrol">作业</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> 此工作流会触发批准的投放，并开始后处理外部投放的服务提供程序。 它还会发送批准通知和提醒。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">营销活动作业</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> 此工作流用于管理营销活动（启动项定位、文件提取等）的作业。 它还创建与循环和定期活动相关的工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> 服务提供者上的<span class="uicontrol">作业</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> 在投放获得批准后，此工作流将开始处理提供程序（通过电子邮件发送到路由器并进行后处理）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

