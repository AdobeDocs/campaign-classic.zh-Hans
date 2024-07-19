---
product: campaign
title: Web 分析
description: 了解关于网站分析包的更多信息
feature: Workflows, Analytics Integration
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 3%

---


# Web 分析{#web-analytics}



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
   <td> 此工作流可让您通过Adobe® Analytics连接器，将电子邮件营销活动指标从Adobe Campaign发送到Adobe Experience Cloud套件。 相关指标如下： <strong>已发送</strong> (iSent)、<strong>打开总计数</strong> (iTotalRecipientOpen)、<strong>点击的收件人总数</strong> (iTotalRecipientClick)、<strong>错误</strong> (iError)、<strong>选择退出</strong> （选择退出） (iOptOut)。<br /> </td> 
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

