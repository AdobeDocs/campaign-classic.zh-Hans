---
product: campaign
title: 网络分析
description: 进一步了解Web分析包
feature: Workflows, Analytics Integration
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# 网络分析{#web-analytics}

![](../../assets/common.svg)

下面详述的工作流随 **Web Analytics连接器** 模块。 有关此模块的更多信息，请参阅此 [部分](../../platform/using/adobe-analytics-connector.md).

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
   <td> 此工作流允许您通过Analytics®连接器将电子邮件促销活动指示器从Adobe Campaign发送到Adobe Experience Cloud Suite。 有关指标如下： <strong>已发送</strong> （已发送）、 <strong>打开总数</strong> (iTotalRecipientOpen), <strong>点击的收件人总数</strong> (iTotalRecipientClick), <strong>错误</strong> (iError)、 <strong>选择退出</strong> （选择禁用）(iOptOut)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已转换联系人的标识</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流可为在再营销活动后完成购买的网站访客建立索引。 可通过 <span class="uicontrol">再营销效率报表</span> (请参阅 <a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign"> 页面</a>)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 利用此工作流，可根据 <span class="uicontrol">生命周期</span> 字段。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Web事件的恢复</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 此工作流每小时会下载给定网站上Internet用户行为的区段，并将其放入Adobe Campaign数据库并启动再营销工作流。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

