---
title: 营销活动
seo-title: 营销活动
description: 营销活动
seo-description: null
page-status-flag: never-activated
uuid: 9e5cf203-e5e9-4383-b628-aa6f131491e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: de892ec4-c378-4b22-875e-aa9345f82552
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0d687b57f75b432547baef57021b716a8ce37ad4

---


# 营销活动{#campaign}

下面详细介绍的工作流默认随 **Campaign** 模块安装。 For more on this module, refer to this [section](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>必须启动这些工作流，才能在营销活动级别执行营销活动流程。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">成本计算</span><br /> </td> 
   <td> <span class="uicontrol">预算管理</span><br /> </td> 
   <td> 此工作流开始计算预算、计划、计划、营销活动、交货和任务上的费用和成本行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock:订单和警报</span><br /> </td> 
   <td> <span class="uicontrol">stockMgt</span><br /> </td> 
   <td> 此工作流会启动订单行上的库存计算并管理警告警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">营销活动中的提交任务</span><br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span><br /> </td> 
   <td> 此工作流会触发已批准的交付，并开始对外部交付的服务提供商进行后期处理。 它还会发送批准通知和提醒。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">营销活动作业</span><br /> </td> 
   <td> <span class="uicontrol">operationMgt</span><br /> </td> 
   <td> 此工作流管理营销活动（启动项定位、文件提取等）的作业。 它还创建与重复和定期营销活动相关的工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">服务提供商上的作业</span><br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span><br /> </td> 
   <td> 批准发送后，此工作流会开始处理提供商（向路由器发送电子邮件并进行后处理）。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

