---
title: 指标计算
seo-title: 指标计算
description: 指标计算
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7655cd93a7dc8ecd35cd379da350ad279cae725

---


# 指标计算 {#indicator-calculation}

## 用户活动 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主键等于1的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击量<br /> </td> 
   <td> @单击<br /> </td> 
   <td> URL类型等于“电子邮件单击”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL类型等于“Transaction”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此报告基于表(nms: **[!UICONTROL Consolidated tracking]** trackingStats)。 此汇总表用于显示报表时的性能原因，它代替表 **[!UICONTROL Recipient tracking logs]** (nms:trackingLogRcp)，并且不实时计算。 在检索跟踪日志后几分钟即会生成表。 如果指标是最新的，则结果将与跟踪指标报告的指标 **相同** 。 @totalclicks指示符表示在5分钟时间段内的点击总数。

## 无法投放项和退回 {#non-deliverables-and-bounces-1}

**按错误类型划分**

此报告基于表(nms:deliveryLogStats)。 **[!UICONTROL Delivery and tracking statistics]**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已处理消息的总数<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 状态等于“就绪”、“已发送”或“已失败”的消息总和。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 状态为“失败”且原因为“用户未知”的所有消息的计数。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=1）<br /> </td> 
  </tr> 
  <tr> 
   <td> 无法访问 <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 状态等于“失败”且原因等于“无法访问”的所有消息计数。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=3）<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒绝<br /> </td> 
   <td> @已拒绝<br /> </td> 
   <td> 状态为“已失败”且原因为“已拒绝”的所有消息的计数。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=20）<br /> </td> 
  </tr> 
  <tr> 
   <td> 域无效<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 状态为“失败”且原因为“无效域”的所有消息的计数。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=2）<br /> </td> 
  </tr> 
  <tr> 
   <td> 帐户已禁用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 状态等于“已失败”且原因等于“帐户已禁用”的所有消息的计数。<br /> </td> 
   <td> Count（@status=2和msg/@failureReason=4）<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱已满<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 状态等于“已失败”且原因等于“收件箱已满”的所有消息的计数。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=5）<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误<br /> </td> 
   <td> @value<br /> </td> 
   <td> 此类型错误的失败消息数。<br /> </td> 
   <td> Count（@status=2和msg/@failureReason="错误类型的值"）<br /> </td> 
  </tr> 
  <tr> 
   <td> 贡献<br /> </td> 
   <td> -<br /> </td> 
   <td> 与错误消息总数相比，此类型的错误百分比。<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 细分<br /> </td> 
   <td> -<br /> </td> 
   <td> 与已处理消息的总数相比，此类型的错误百分比。<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**按域划分**

报告的第二部分按Internet域（而非错误类型）详细列出了故障消息的细分。 在此例中，链接到 **错误** 指示符(@value)的公式为：Count（@status=2和@domain=&quot;域名的值&quot;），即此域状态为失败的所有消息的计数。

## 浏览器 {#browsers-1}

此报告基于表(nms: **[!UICONTROL Internet Browser Statistics]** userAgentsStats)。

**全球统计**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 访客<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 此浏览器中点击分发一次的目标收件人总数。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 页面查看次数<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 使用此浏览器的所有分发的分发链接总点击次数。<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此浏览器的访客百分比与访客总数之比。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**每浏览器的统计信息**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 使用此浏览器的每日访客数与当天访问量最大的访客数的百分比。<br /> </td> 
   <td> percent(sum(@visitors),max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与使用所有浏览器的访客总数相比，此版本的访客百分比。<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对重量<br /> </td> 
   <td> -<br /> </td> 
   <td> 与使用此浏览器的访客总数相比，此版本的访客百分比。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共享到社交网络 {#sharing-to-social-networks-1}

此报告基于 **[!UICONTROL Delivery]** (nms:delivery)、 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要传送的消息数<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 在分发分析过程中处理的消息总数。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功交付的次数<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的消息数 <br /> </td> 
   <td> sum（[指示器/@success]）<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
   <td> 其URL类别等于“email”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> 其URL类别等于“facebook”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> 其URL类别等于“twitter”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味可口<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> 其URL类别等于“可口”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> 其URL类别等于“digg”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> 其URL类别等于“google”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> 其URL类别等于“linkedin”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**股份**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 股份数目<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 此社交网络上共享的消息总数。<br /> </td> 
   <td> Sum(iIf（[url/@category]="社交网络类型的值",@totalClicks,0）)<br /> </td> 
  </tr> 
  <tr> 
   <td> 细分<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 此社交网络上的股份数量与总股份数量的百分比。<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 与要传送的消息数相比，此网络上的共享数。<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**打开**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开次数 <br /> </td> 
   <td> @open<br /> </td> 
   <td> Web跟踪表中的跟踪行总数。<br /> </td> 
   <td> 计数<br /> </td> 
  </tr> 
  <tr> 
   <td> 细分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交网络上的打开次数与打开总数的百分比。<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 此社交网络上的打开次数与要传送的消息总数相比较。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 关于共享活动的统计数据 {#statistics-on-sharing-activities-1}

此报告基于 **[!UICONTROL Delivery]** (nms:delivery)、 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 新联系人<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 链接到收件人的访客数。<br /> </td> 
   <td> 公式：count(@id)<br /> Filter:@recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @已打开<br /> </td> 
   <td> URL类型等于“Open”的所有@id的计数。<br /> </td> 
   <td> count(Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 股份<br /> </td> 
   <td> @shared<br /> </td> 
   <td> URL类别包括在“email”、“facebook”、“twitter”、“delicious”、“digg”、“google”、“linkedin'<br /> Count of all @totalClicks”中，URL类别等于“email”、“facebook”、“twitter”、“delicious”、“digg”、“google”或“linkedin”。<br /> </td> 
   <td> count(Iif([url/@category] IN(email', 'facebook', 'twitter', 'delicious', 'digg', 'google', 'linkedin'), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 操作系统 {#operating-systems-1}

此报告基于表(nms: **[!UICONTROL Internet Browser Statistics]** userAgentsStats)。

**全球统计**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 访客<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 操作系统点击交付的目标收件人总数的每日平均值，至少单击一次。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 查看的页面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 所有交付的每个操作系统的交付链接的每日总点击次数平均数。<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与访客总数相比，每个操作系统的访客细分。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**每个操作系统的统计数据**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 此操作系统中每日访客数的百分比，与当天访问次数最多的访客数相比。<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每个版本的访客百分比与所有操作系统上的访客总数之比。<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每个版本的访客百分比与使用此操作系统的访客总数相比。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 订阅跟踪 {#subscription-tracking-1}

此报告基于表(nms: **[!UICONTROL Services]** service)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已注册<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 前一天的注册人数。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 前一天的订阅计数(@action = 1)。<br /> </td> 
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 前一天的取消订阅计数（操作= 0）。<br /> </td> 
   <td> sum(Iif(@action = 0和@date &gt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 进化<br /> </td> 
   <td> -<br /> </td> 
   <td> 订阅数减去取消订阅数。 该速率相对于用户总数来计算。<br /> </td> 
   <td> 如果(number(@_subscription)&gt; number(@_unsubscription), '+', ")+format（@_unsubscription - @_unsubscription, '编号', '###0'）+ Iif(@_subscriber&gt;0,','(' + format(100*percent(@_subscription - @_unsubscription, @_subscription)), @_subscriber))), ', ', '编号'), '#, '#0.0.0')')', '#, ')+ '%)',")<br /> </td> 
  </tr> 
  <tr> 
   <td> 忠诚度<br /> </td> 
   <td> -<br /> </td> 
   <td> 相关时段的订阅者忠诚度率。<br /> </td> 
   <td> 1%(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟踪指标 {#tracking-indicators-1}

此报告基于 **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats)和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要传送的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 目标分析后broadLogs的计数。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> “种子地址”字段等于“否”且状态等于“由服务提供商考虑”、“已发送”或“在移动设备上接收”的消息计数。<br /> </td> 
   <td> sum（[指示器/@success]）<br /> </td> 
  </tr> 
  <tr> 
   <td> 在到达的人口中打开不同的<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根据HTML格式的电子邮件的不同打开次数推断出所有电子邮件的不同打开次数。<br /> </td> 
   <td> Iif([@toDeliver] - [@text])= 0, 0, round(toDouble(@recipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 达到的人口的打开总数<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根据HTML格式的电子邮件的打开总数推断所有电子邮件的打开总数。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@totalRecipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击取消订阅链接<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类别等于“退出”的所有@id的计数。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击指向镜像页面的链接<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL类别等于“镜像页面”的所有@id的计数。<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 转发估计<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 不同人数与至少点击一次电子邮件的不同收件人数之间的差异。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> “种子地址”字段等于“否”且状态等于“收件人考虑”、“已发送”或“在移动设备上接收”的消息计数。<br /> </td> 
   <td> sum（[指示器/@success]）<br /> </td> 
  </tr> 
  <tr> 
   <td> 投诉<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 状态为“已失败”且原因为“列入黑名单的地址”的消息计数。<br /> </td> 
   <td> Count（@status=2和msg/@failureReason=8）<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有跟踪日志中所有@broadLog-id的计数。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击量<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“电子邮件单击”的@broadLog-id的独特计数。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 至少单击一次分发的收件人数与至少打开一次分发的收件人数的百分比。<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 对到达人群的明显点击<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别等于“电子邮件单击”的所有@source-id的计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累积的单击<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL类别为“电子邮件单击”的所有@id的计数。<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人单击<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“电子邮件单击”的@broadLog-id的独特计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 估计反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 与至少打开一次递送的接收者的估计相比，点击了递送的至少一次的接收者人数的比例。<br /> </td> 
   <td> percent(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 访问过的页面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL类型等于“Web”或“Transaction”的所有@id的计数。<br /> </td> 
   <td> count(Iif（[url/@type]=4或[url/@type]=5, @id, 0）)<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL类型等于“事务”的所有@id的计数。<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 总额<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL类型等于“事务”的webTrackingLog/@amounts的总和。 <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均事务处理金额<br /> </td> 
   <td> -<br /> </td> 
   <td> 总金额与事务处理数之比。<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 项目<br /> </td> 
   <td> @article<br /> </td> 
   <td> URL类型等于“Transaction”的webTrackingLog/@articles的总和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 每笔交易的平均项目数<br /> </td> 
   <td> -<br /> </td> 
   <td> 项目数与事务处理数的比率。<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每条消息的平均数量<br /> </td> 
   <td> -<br /> </td> 
   <td> 总量与要传送的消息数的比率。<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
   <td> 所有@totalClicks与等于“email”的URL类别的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> 所有@totalClicks与等于“facebook”的URL类别的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> 所有@totalClicks与等于“twitter”的URL类别的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味可口<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> 所有@totalClicks与等于“可口”的URL类别的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> 所有@totalClicks与等于“digg”的URL类别的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> 所有@totalClicks与等于“google”的URL类别的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> 所有@totalClicks与等于“linkedin”的URL类别的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和点击流 {#urls-and-click-streams-1}

此报告基于表(nms: **[!UICONTROL Delivery]** delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 反应性<br /> </td> 
   <td> @反应性<br /> </td> 
   <td> 至少点击一次递送的目标收件人数与至少打开过递送的估计目标收件人数的比率。<br /> </td> 
   <td> percent([indicators/@recipientClick], [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 独特点击<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 至少点击一次分发的不同人数与成功发送的消息数的比率。<br /> </td> 
   <td> percent([indicators/@personClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累积的单击<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目标收件人点击总次数与成功发送的消息数的比率。<br /> </td> 
   <td> percent([indicators/@totalRecipientClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击量<br /> </td> 
   <td> @_click<br /> </td> 
   <td> 所有@totalClicks的计数（URL主键不同于1）<br /> </td> 
   <td> count(Iif([@url-id]] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击量(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 点击次数与累计点击总数的百分比。<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放摘要 {#delivery-summary-1}

此报告基于表(nms: **[!UICONTROL Delivery]** delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 初始人口<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 交付所针对的收件人总数。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 被规则拒绝的消息<br /> </td> 
   <td> @拒绝<br /> </td> 
   <td> 在分析过程中根据类型学规则忽略的地址数：未指定地址、隔离地址、黑名单等。<br /> </td> 
   <td> sum（[属性/@reject]）<br /> </td> 
  </tr> 
  <tr> 
   <td> 要传送的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 分发分析后要传送的消息总数。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的消息数。<br /> </td> 
   <td> sum（[指示器/@success]）<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误<br /> </td> 
   <td> @error<br /> </td> 
   <td> 在提交和自动弹回处理过程中累积的错误总数。<br /> </td> 
   <td> sum（[指示符/@error）<br /> </td> 
  </tr> 
  <tr> 
   <td> 新的隔离<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 传送失败后隔离的地址数（用户未知，无效域）。<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 热门点击 {#hot-clicks-1}

此报告基于Delivery(nms:delivery)和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表。

此报告显示消息内容（HTML和／或文本），每个链接上包含点击链接的百分比。 个性化区块取消订阅链接和镜像页面链接在累计的总点击量中会被考虑在内，但不会显示在报告中。

## 跟踪统计数据 {#tracking-statistics-1}

此报告基于表(nms: **[!UICONTROL Delivery]** delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL类型等于“事务”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击量<br /> </td> 
   <td> @单击<br /> </td> 
   <td> URL类型等于“电子邮件单击”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主键等于1的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 交付统计 {#delivery-statistics-1}

此报告基于表(nms:deliveryLogStats)。 **[!UICONTROL Delivery and tracking statistics]**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已处理电子邮件<br /> </td> 
   <td> @已处理<br /> </td> 
   <td> 状态为“就绪”、“已发送”或“已失败”的消息总数。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的消息数。<br /> </td> 
   <td> 指示器/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 硬弹回<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 状态为“失败”且原因为“用户未知”的消息总数。<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 软弹回<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 状态等于“已失败”和原因等于“无法访问”、“收件箱已满”、“无效域”、“禁用帐户”、“未连接”或“已拒绝”的所有邮件总数<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @resubled<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 跟踪日志中的@broadLog-id总数。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击量<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别等于“电子邮件单击”的@source-id总数。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类别等于“退出”的@id总数。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 打开次数细分 {#breakdown-of-opens-1}

此报告基于 **Deliveries** (nms:delivery)和 **Tracking logs** (nms:trackingLogRcp)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong><br /> </th> 
   <th> <strong>字段名称</strong><br /> </th> 
   <th> <strong>指示器说明</strong><br /> </th> 
   <th> <strong>指示器计算公式</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主键等于1（打开）的所有@id的总和。 <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指标 {#other-indicators}

“已 **发送** ”指示符(@sent)，通过“ **Deliveries(nms:delivery)”>“Indicators** ”节点访问，对应于发送给服务提供商的SMS总数。 此指示器仅用于SMS发送，不得用于其他类型的发送(不得与 **@success** 和 **@processed** 指示符混淆)。

## 指示器同步 {#indicator-synchronization}

如果您遇到某些指标的取消同步或不一致情况，请在Adobe Campaign资源管理器中选择相关的交付，然后右键单击并选择 **[!UICONTROL Action>Recompute delivery and tracking indicators]**。 单 **[!UICONTROL Next]**&#x200B;击，然后单击 **[!UICONTROL Finish]**。

![](assets/s_ncs_user_recalculate_indicators.png)

## 跟踪打开 {#tracking-opens-}

为了使Adobe Campaign能够检测邮件打开，收件人必须下载电子邮件中的图像。 HTML和多部件／替代电子邮件包含0像素图像，这使您能够检测已打开的消息。 由于文本格式的消息不包含任何图像，因此无法检测是否已打开它们。 根据消息打开次数计算的值始终是估计值，因为与图像显示链接的误差范围。

## 目标人员／收件人 {#targeted-persons---recipients}

在某些报告中，Adobe Campaign可区分目标人员和目标收件人。

目标收件人是将分发发送到的所有收件人。

人数包括目标收件人以及将电子邮件转发给的所有人员。 每次在新浏览器中打开或单击（消息尚未在中打开）时，都会向统计信息中添加另一个人。

例如，如果您在工作时收到电子邮件（由Adobe Campaign发送）并打开或点击它，您将被计为目标收件人（即收件人=1，人员=1）。 如果您将此电子邮件转发给两位朋友，则目标收件人的数量仍等于1，而人数将等于3。 值3与新浏览器中每次打开／单击的时间一致。
