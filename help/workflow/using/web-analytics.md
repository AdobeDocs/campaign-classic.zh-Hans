---
title: Web分析
seo-title: Web分析
description: Web分析
seo-description: null
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Web分析{#web-analytics}

下面详细介绍的工作流默认为随 **Web Analytics连接器模块一起安装** 。 For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>标签</strong><br /> </td> 
   <td> <strong>内部名称</strong><br /> </td> 
   <td> <strong>说明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">发送指标和营销活动属性</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> 通过此工作流程，您可以通过Adobe® Genesis连接器将电子邮件营销活动指示器从Adobe Campaign发送到Adobe Experience Cloud Suite。 有关指标如下：已 <strong>发送</strong> (iSent)、已点击(iTotalRecipientOpen)、已点击(iTotalRecipientOpen)的总数 <strong>(iTotalClick)、</strong><strong></strong><strong></strong><strong></strong> Opt-Out(iError)、Opt-Out(iOptOut)的接收者的总数)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">转换的联系人的标识</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> 此工作流为在再营销活动后完成购买的站点访客建立索引。 通过此工作流恢复的数据可在再营销效 <span class="uicontrol">率报告中访问</span> (请参阅 <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> 此页</a>)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> 通过此工作流，您可以根据“寿命”字段中配置的期间从数据库字段中删除每 <span class="uicontrol">个事件</span> 。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Web事件的恢复</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> 该工作流每小时都会下载给定站点上Internet用户行为的细分，将其放入Adobe Campaign数据库并启动再营销工作流。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

