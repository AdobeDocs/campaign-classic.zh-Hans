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

下面详细介绍的工作流默认 **情况下随Web** Analytics连接器模块安装。 For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

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
   <td> 通过此工作流程，您可以通过Adobe Campaign®活动连接器将电子邮件Adobe指示符从Genesis发送到Adobe Experience Cloud套件。 有关指标如下： <strong>已发送</strong> (iSent <strong>)、</strong> 打开总数(iTotalRecipientOpen)、单击 <strong>(iTotalRecipientClick)、</strong> Errors(iError <strong></strong><strong></strong> )、Opt-Out(iOpt-Out)(iOpt-Out)的收件人总数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已转换联系人的标识</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流为在再营销访客后完成购买的网站活动建立索引。 通过此工作流恢复的数据可以在再营 <span class="uicontrol">销效率报告中访问</span> (请参阅 <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> 此页</a>)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 通过此工作流，您可以根据“寿命”字段中配置的期间从事件库字段中删除每 <span class="uicontrol">个</span> 。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">恢复Web事件</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 该工作流每小时都会下载给定站点的Internet用户行为细分，将其放入Adobe Campaign库并启动再营销工作流。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

