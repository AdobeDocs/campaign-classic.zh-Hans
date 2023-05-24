---
product: campaign
title: 网络分析
description: 了解有关Web Analytics包的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Analytics Integration
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 4%

---


# 网络分析{#web-analytics}



下面详述的工作流将随 **网站分析连接器** 默认模块。 有关此模块的更多信息，请参阅此 [部分](../../platform/using/adobe-analytics-connector.md).

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
   <td> 此工作流允许您通过Adobe® Analytics连接器，将电子邮件促销活动指标从Adobe Campaign发送到Adobe Experience Cloud Suite。 有关指标如下： <strong>已发送</strong> (iSent)， <strong>打开次数总计</strong> (iTotalRecipientOpen)， <strong>点击的收件人总数</strong> (iTotalRecipientClick)， <strong>错误</strong> (iError)、 <strong>选择禁用</strong> （选择退出） (iOptOut)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已转换联系人的标识</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流会为再营销活动后完成购买的网站访客编制索引。 通过此工作流恢复的数据可在 <span class="uicontrol">再营销效率报表</span> (请参阅此 <a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign"> 页面</a>)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 此工作流允许您根据中配置的时段，从数据库字段删除每个事件 <span class="uicontrol">生命周期</span> 字段。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Web事件的恢复</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 每小时，此工作流都会下载指定网站上Internet用户行为的区段，将其放入Adobe Campaign数据库并启动再营销工作流。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

