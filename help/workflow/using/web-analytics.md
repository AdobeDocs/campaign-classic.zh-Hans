---
product: campaign
title: 网络分析
description: 进一步了解Web分析包
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# 网络分析{#web-analytics}

默认情况下，下面详述的工作流与&#x200B;**Web Analytics连接器**&#x200B;模块一起安装。 有关此模块的更多信息，请参阅此[部分](../../platform/using/adobe-analytics-data-connector.md)。

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
   <td> 利用此工作流，可通过Adobe®Genesis连接器，从Adobe Campaign向Adobe Experience Cloud Suite发送电子邮件促销活动指示器。 有关指标如下：<strong>Sented</strong>(iSent)、<strong>打开总数</strong>(iTotalRecipientOpen)、<strong>单击</strong>(iTotalRecipientClick)、<strong>Errors</strong>(iError)、<strong>Opt-Out</strong>(opt-out)(iOptOut)的收件人总数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已转换联系人的标识</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流可为在再营销活动后完成购买的网站访客建立索引。 可通过<span class="uicontrol">再营销效率报表</span>（请参阅此<a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign">页面</a>）访问此工作流取回的数据。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 利用此工作流，可根据<span class="uicontrol">Life</span>字段中配置的句点，从数据库字段中删除每个事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Web事件的恢复</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 此工作流每小时会下载给定网站上Internet用户行为的区段，并将其放入Adobe Campaign数据库并启动再营销工作流。<br /> </td> 
  </tr> 
 </tbody> 
</table>

