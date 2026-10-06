---
product: campaign
title: 网站分析
description: 了解关于网站分析包的更多信息
hide: true
feature: Workflows, Analytics Integration
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 3%
---

# 网站分析{#web-analytics}



默认情况下，下面详细介绍的工作流随&#x200B;**Web Analytics连接器**&#x200B;模块一起安装。 有关此模块的详细信息，请参阅此[部分](../../integrations/using/gs-aa.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">发送指标和营销活动属性</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> 此工作流可让您通过® Analytics连接器，将电子邮件营销活动指标从Adobe Campaign发送到Adobe Experience Cloud套件。 相关指标如下： <strong>已发送</strong> (iSent)、<strong>打开总计数</strong> (iTotalRecipientOpen)、<strong>点击的收件人总数</strong> (iTotalRecipientClick)、<strong>错误</strong> (iError)、<strong>选择退出</strong> （选择退出） (iOptOut)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已转换联系人的标识</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流对再营销活动后完成购买的网站访客编制索引。 可在<span class="uicontrol">再营销效率报表</span>中访问由此工作流恢复的数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 此工作流允许您根据<span class="uicontrol">生命周期</span>字段中配置的时段，从数据库字段中删除每个事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">恢复Web事件</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 每小时，此工作流会下载给定网站上的Internet用户行为区段，将它们放入Adobe Campaign数据库并启动再营销工作流。<br /> </td> 
  </tr> 
 </tbody> 
</table>

