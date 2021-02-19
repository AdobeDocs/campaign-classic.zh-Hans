---
solution: Campaign Classic
product: campaign
title: 网络分析
description: 进一步了解Web Analytics包
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# 网络分析{#web-analytics}

以下详细工作流默认随&#x200B;**Web Analytics connectors**&#x200B;模块一起安装。 有关此模块的详细信息，请参阅此[部分](../../platform/using/adobe-analytics-data-connector.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">发送指示符和活动属性</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> 通过此工作流，您可以通过Adobe® 活动连接器将电子邮件Genesis指示器从Adobe Campaign发送到Adobe Experience Cloud Suite。 有关指标如下：<strong>Sent</strong>(iSent)、<strong>打开总数</strong>(iTotalRecipientOpen)、<strong>单击</strong>(iTotalRecipientClick)、<strong>Errors</strong>(iError)、<strong>退出</strong>（退出）（iOpt退出）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已转换联系人的标识</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流对在再营销活动后完成购买的站点访客进行索引。 可通过<span class="uicontrol">再营销效率报表</span>（请参阅此<a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign">页面</a>）访问此工作流恢复的数据。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 通过此工作流，您可以根据在<span class="uicontrol">Life</span>字段中配置的期间，从事件库字段中删除每个。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">恢复Web事件</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 每小时，此工作流都会下载给定站点的Internet用户行为细分，将其放入Adobe Campaign数据库并启动再营销工作流。<br /> </td> 
  </tr> 
 </tbody> 
</table>

