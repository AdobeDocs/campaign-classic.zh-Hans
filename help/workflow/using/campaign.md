---
product: campaign
title: 营销活动
description: 营销活动
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# 营销活动{#campaign}

![](../../assets/common.svg)

默认情况下，下面详述的工作流随&#x200B;**Campaign**&#x200B;模块一起安装。 有关此模块的更多信息，请参阅此[部分](../../campaign/using/designing-marketing-campaigns.md)。

>[!CAUTION]
>
>必须启动这些工作流，营销活动流程才能在营销活动级别执行。

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
   <td> 此工作流开始计算预算、计划、项目、营销策划、投放和任务中的费用和成本行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">股票：订单和警报</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> 此工作流会启动订单行上的库存计算并管理警告警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">营销活动中投放的作业</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> 此工作流会触发已批准的投放，并启动外部投放的服务提供商的后处理。 它还会发送批准通知和提醒。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">营销活动作业</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> 此工作流可管理营销活动的作业（启动项定位、文件提取等）。 它还会创建与定期和定期营销活动相关的工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">服务提供商上的作业</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> 在投放获得批准后，此工作流将开始处理提供程序（向路由器发送电子邮件并进行后处理）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

