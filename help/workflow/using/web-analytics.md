---
solution: Campaign Classic
product: campaign
title: 网络分析
description: 进一步了解Web分析包
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

下面详细介绍的工作流默认安装在&#x200B;**Web分析连接器**&#x200B;模块中。 有关此模块的详细信息，请参阅此[部分](../../platform/using/adobe-analytics-data-connector.md)。

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
   <td> 通过此工作流程，您可以通过Adobe Campaign®活动连接器将电子邮件Adobe指示符从Genesis发送到Adobe Experience Cloud套件。 有关指标如下：<strong>已发送</strong>(iSent)、<strong>打开总数</strong>(iTotalRecipientOpen)、<strong>单击</strong>(iTotalRecipientClick)、<strong>错误</strong>(iError)、&lt;a8的收件人总数/&gt;退出</strong>（退出）（iOpt退出）。<br /><strong> </strong></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已转换联系人的标识</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流为在再营销访客后完成购买的网站活动建立索引。 通过此工作流恢复的数据可在<span class="uicontrol">再营销效率报告</span>（请参阅此<a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign">页面</a>）中访问。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 通过此工作流，您可以根据<span class="uicontrol">Lifemity</span>字段中配置的句点，从事件库字段中删除每个。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">恢复Web事件</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 该工作流每小时都会下载给定站点的Internet用户行为细分，将其放入Adobe Campaign库并启动再营销工作流。<br /> </td> 
  </tr> 
 </tbody> 
</table>

