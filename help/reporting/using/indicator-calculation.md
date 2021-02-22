---
solution: Campaign Classic
product: campaign
title: 指标计算
description: 指标计算
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 1%

---


# 指标计算 {#indicator-calculation}

## 用户活动{#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主键等于1的@totalClicks总和。<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL类型等于“Email click”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL类型等于"Transaction"的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此报表基于&#x200B;**[!UICONTROL Consolidated tracking]**&#x200B;表(nms:trackingStats)。 此聚合表用于显示报表时的性能原因，而不是实时计算。 **[!UICONTROL Recipient tracking logs]**&#x200B;检索跟踪日志后几分钟即会生成表。 如果指标是最新的，则结果将与&#x200B;**跟踪指标**&#x200B;报表的指标相同。 @totalclicks指示符表示在5分钟内的点击总数。

## 无法投放项和退回 {#non-deliverables-and-bounces-1}

**按错误类型划分**

此报告基于&#x200B;**[!UICONTROL Delivery and tracking statistics]**&#x200B;表(nms:deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已处理邮件的总数<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 状态等于“就绪”、“已发送”或“失败”的消息总和。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 状态等于“失败”且原因等于“用户未知”的所有邮件计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 不可到达<br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 状态等于“失败”且原因等于“不可到达”的所有邮件计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 被拒绝<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 状态等于“失败”且原因等于“被拒绝”的所有邮件计数。<br /> </td> 
   <td> Count(@status=2,msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 无效域<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 状态等于“失败”且原因等于“无效域”的所有邮件计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 帐户已禁用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 状态等于“失败”且原因等于“帐户已禁用”的所有邮件计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱已满<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 状态等于“失败”且原因等于“收件箱已满”的所有邮件计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误<br /> </td> 
   <td> @value<br /> </td> 
   <td> 此类型错误的失败消息数。<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason="Value of the error type")<br /> </td> 
  </tr> 
  <tr> 
   <td> 贡献<br /> </td> 
   <td> -<br /> </td> 
   <td> 此类型的错误与错误消息总数的百分比。<br /> </td> 
   <td> 百分比(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 划分<br /> </td> 
   <td> -<br /> </td> 
   <td> 与已处理邮件总数相比，此类型的错误百分比。<br /> </td> 
   <td> 百分比(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**按域划分**

报告的第二部分按Internet域（而不是错误类型）详细列出了失败消息的划分。 链接到&#x200B;**Error**&#x200B;指示符(@value)的公式为：计数(@status=2和@domain=&quot;域名的值&quot;)，即对于此域，状态为失败的所有消息的计数。

## 浏览器 {#browsers-1}

此报告基于&#x200B;**[!UICONTROL Internet Browser Statistics]**&#x200B;表(nms:userAgentsStats)。

**全球统计**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 访客<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 此浏览器中至少单击一次收件人的目标投放总数。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 页面视图<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 对所有投放使用此浏览器的投放链接的点击总数。<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此浏览器的访客与总访客的百分比。<br /> </td> 
   <td> 百分比(@totalVisitors, sum(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**每个浏览器的统计信息**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 使用此浏览器的每日访客数与访问次数最多的一天中测量的访客数的百分比。<br /> </td> 
   <td> 百分比(sum(@visitors),max(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的访客与使用所有浏览器的访客总数的百分比。<br /> </td> 
   <td> 百分比(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对权重<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的访客与使用此浏览器的访客总数的百分比。<br /> </td> 
   <td> 百分比(@totalVisitors, sum(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共享到社交网络{#sharing-to-social-networks-1}

此报告基于&#x200B;**[!UICONTROL Delivery]**(nms:投放)、**[!UICONTROL Consolidated tracking]**(nms:trackingStats)和&#x200B;**[!UICONTROL Web tracking]**(nms:webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要传送的消息数<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 在投放分析期间处理的邮件总数。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功投放数<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功处理的邮件数<br /> </td> 
   <td> sum([indicators/@success)<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL类别等于“email”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL类别等于“facebook”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL类别等于"twitter"的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL类别等于“可口”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL类别等于"digg"的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL类别等于"google"的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL类别等于“linkedin”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**股份**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 股份数<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 此社交网络上共享的消息总数。<br /> </td> 
   <td> Sum(iIf([url/@category]="社交网络类型的值",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 划分<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 此社交网络上的股份数与股份总数的百分比。<br /> </td> 
   <td> 百分比(@forward, sum(@forward)<br /> </td> 
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
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开次数<br /> </td> 
   <td> @open<br /> </td> 
   <td> Web跟踪表中跟踪行的总数。<br /> </td> 
   <td> 计数<br /> </td> 
  </tr> 
  <tr> 
   <td> 划分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交网络上的打开次数与打开总数的百分比。<br /> </td> 
   <td> 百分比(@open, sum(@open)<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 此社交网络上的打开次数与要传送的消息总数相比。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共享活动的统计信息{#statistics-on-sharing-activities-1}

此报告基于&#x200B;**[!UICONTROL Delivery]**(nms:投放)、**[!UICONTROL Consolidated tracking]**(nms:trackingStats)和&#x200B;**[!UICONTROL Web tracking]**(nms:webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 新联系人<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 链接到收件人的访客数。<br /> </td> 
   <td> 公式：count(@id)<br />过滤器：@recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL类型等于“Open”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 股份<br /> </td> 
   <td> @shared<br /> </td> 
   <td> URL类别包含在“email”、“facebook”、“twitter”、“dicious”、“google”、“linkedin”<br />中，其URL类别等于“email”、“facebook”、“twitter”、“dicious”、“google”或“linkedin”。<br /> </td> 
   <td> count([url/@category] IN(email', 'facebook', 'twitter', 'delicious', 'digg', 'google', 'linkedin'), @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 操作系统 {#operating-systems-1}

此报告基于&#x200B;**[!UICONTROL Internet Browser Statistics]**&#x200B;表(nms:userAgentsStats)。

**全球统计**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 访客<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 操作系统在投放中点击至少一次的目标收件人总数的每日平均值。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 查看的页面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 每个操作系统上所有投放的点击总数的每日平均值。<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与访客总数相比，每个操作系统的访客细分。<br /> </td> 
   <td> 百分比(@totalVisitors, sum(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**每个操作系统的统计**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 此操作系统每天的访客数与访问次数最多的一天中测量的访客数的百分比。<br /> </td> 
   <td> 百分比(sum(@visitors), max(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每个版本的访客与所有操作系统上的访客总数的百分比。<br /> </td> 
   <td> 百分比(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每个版本的访客与使用此操作系统的访客总数的百分比。<br /> </td> 
   <td> 百分比(@totalVisitors, sum(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 订阅跟踪{#subscription-tracking-1}

此报告基于&#x200B;**[!UICONTROL Services]**&#x200B;表(nms:service)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已注册<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 前一天注册人数。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 前一天的订阅计数(@action = 1)。<br /> </td> 
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 前一天的退订计数（操作= 0）。<br /> </td> 
   <td> sum(Iif(@action = 0 and @date &gt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 进化<br /> </td> 
   <td> -<br /> </td> 
   <td> 订阅数减去退订数。 该速率是根据用户总数计算的。<br /> </td> 
   <td> If(number(@_subscription)&gt; number(@_unsubscription), '+', ')+format(@_subscription - @_unsubscription, 'number', '# #0')+ Iif(@_subscriber&gt;0,'(' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), '#,##0.000')+ '%',")<br /> </td> 
  </tr> 
  <tr> 
   <td> 忠诚度<br /> </td> 
   <td> -<br /> </td> 
   <td> 相关期间的订阅者忠诚度比率。<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟踪指标 {#tracking-indicators-1}

此报告基于&#x200B;**[!UICONTROL Delivery and tracking statistics]**(nms:deliveryLogStats)和&#x200B;**[!UICONTROL Consolidated tracking]**(nms:trackingStats)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
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
   <td> “种子地址”字段等于“否”且状态等于“服务提供商考虑”、“已发送”或“在移动设备上接收”的邮件计数。<br /> </td> 
   <td> sum([indicators/@success)<br /> </td> 
  </tr> 
  <tr> 
   <td> 到达<br />的人口上打开的不同 </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根据html格式电子邮件的不同打开次数推断所有电子邮件的不同打开次数。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@recipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 达到的人口的打开总数<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根据以html格式打开的电子邮件总数推断所有电子邮件的打开总数。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@totalRecipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击退订链接<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类别等于“退出”的所有@ids计数。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击指向镜像页面<br />的链接 </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL类别等于“镜像页面”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 前向估计<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 不同人数与至少点击一次电子邮件的不同收件人数之间的差异。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> “种子地址”字段等于“否”且状态等于“被收件人考虑”、“已发送”或“在移动设备上接收”的消息计数。<br /> </td> 
   <td> sum([indicators/@success)<br /> </td> 
  </tr> 
  <tr> 
   <td> 投诉<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 状态等于“失败”且原因等于“地址”的阻止列表邮件计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有@broadLog-id的计数。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“电子邮件单击”的@broadLog-id的独特计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 在投放中点击至少一次的收件人数与打开投放至少一次的收件人数的百分比。<br /> </td> 
   <td> 百分比(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 对达到的人口的不同点击量<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别等于“电子邮件单击”的所有@source-id计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累积的点击量<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL类别等于“电子邮件单击”的所有@ids计数。<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人单击<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“电子邮件单击”的@broadLog-id的独特计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 估计反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 在投放中点击至少一次的收件人数与至少打开该投放一次的收件人估计数的比率。<br /> </td> 
   <td> 百分比(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 已访问页面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL类型等于"Web"或"Transaction"的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=4或[url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL类型等于"Transaction"的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 总额<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL类型等于“事务”的webTrackingLog/@amounts的总和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均事务金额<br /> </td> 
   <td> -<br /> </td> 
   <td> 总金额与事务数之比。<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 项目<br /> </td> 
   <td> @article<br /> </td> 
   <td> webTrackingLog/@articles的URL类型等于“Transaction”。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每个事务的平均项数<br /> </td> 
   <td> -<br /> </td> 
   <td> 项目数与事务数的比率。<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每条消息的平均金额<br /> </td> 
   <td> -<br /> </td> 
   <td> 总量与要传送的消息数之比。<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL类别等于“email”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL类别等于"facebook"的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL类别等于"twitter"的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL类别等于“可口”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL类别等于"digg"的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL类别等于"google"的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL类别等于"linkedin"的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和点击流 {#urls-and-click-streams-1}

此报告基于&#x200B;**[!UICONTROL Delivery]**&#x200B;表(nms:投放)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 反应性<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 在投放中点击至少一次的目标收件人数与至少打开一次投放的估计目标收件人数的比率。<br /> </td> 
   <td> percent([indicators/@recipientClick], [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 独特点击量<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 在投放中点击至少一次的独特人数与成功传递的消息数之比。<br /> </td> 
   <td> percent([indicators/@personClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累积的点击量<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目标收件人的总点击量与成功传递的消息数的比率。<br /> </td> 
   <td> percent([indicators/@totalRecipientClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主键与1<br />不同的@totalClicks的全部计数 </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 点击次数与累计点击总数的百分比。<br /> </td> 
   <td> 百分比(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放摘要 {#delivery-summary-1}

此报告基于&#x200B;**[!UICONTROL Delivery]**&#x200B;表(nms:投放)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 初始人口<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 投放所针对的收件人总数。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 规则<br />拒绝的消息 </td> 
   <td> @reject<br /> </td> 
   <td> 分析期间忽略的地址数与类型规则一致：未指定地址、隔离阻止列表地址、地址等。<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 要传送的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 投放分析后要传送的邮件总数。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的邮件数。<br /> </td> 
   <td> sum([indicators/@success)<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误<br /> </td> 
   <td> @error<br /> </td> 
   <td> 在投放和自动跳出处理期间累积的错误总数。<br /> </td> 
   <td> sum([indicators/@error)<br /> </td> 
  </tr> 
  <tr> 
   <td> 新隔离<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 投放失败后隔离的地址数(用户未知，无效域)。<br /> </td> 
   <td> sum([indicators/@newQuarantine)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 热门点击 {#hot-clicks-1}

此报告基于投放(nms:投放)和&#x200B;**[!UICONTROL Consolidated tracking]**(nms:trackingStats)表。

此报表显示每个链接上具有点击链接百分比的消息内容（HTML和/或文本）。 个性化块退订链接和镜像页面链接在累计的总点击量中会被考虑在内，但不会显示在报表中。

## 跟踪统计数据{#tracking-statistics-1}

此报告基于&#x200B;**[!UICONTROL Delivery]**&#x200B;表(nms:投放)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 事务<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL类型等于"Transaction"的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL类型等于“Email click”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主键等于1的@totalClicks总和。<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放统计{#delivery-statistics-1}

此报告基于&#x200B;**[!UICONTROL Delivery and tracking statistics]**&#x200B;表(nms:deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已处理的电子邮件<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 状态为“就绪”、“已发送”或“失败”的邮件总数。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 已传送<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功处理的邮件数。<br /> </td> 
   <td> indicators/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 硬弹回<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 状态为“失败”且原因为“用户未知”的邮件总数。<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 软弹回<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 状态等于“失败”且原因等于“不可到达”、“收件箱已满”、“无效域”、“禁用帐户”、“未连接”或“已拒绝”的所有邮件总数<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled +  + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 跟踪日志中的@broadLog-id总数。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别等于“电子邮件单击”的@source-id总数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类别等于“退出”的@ids的总数。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 打开的划分{#breakdown-of-opens-1}

此报告基于&#x200B;**投放**(nms:投放)和&#x200B;**跟踪日志**(nms:trackingLogRcp)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主键等于1（打开）的@id总和。<br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指标{#other-indicators}

通过&#x200B;**投放(nms:投放)>指示器**&#x200B;节点访问的&#x200B;**已发送**&#x200B;指示器(@sent)对应于发送到服务提供商的SMS总数。 此指示器仅用于SMS投放，不得用于其他类型的投放(请勿与&#x200B;**@success**&#x200B;和&#x200B;**@processed**&#x200B;指示器混淆)。

## 指示器同步{#indicator-synchronization}

如果您遇到某些指示器的取消同步或不一致情况，请在Adobe Campaign浏览器中选择相关投放，右键单击并选择&#x200B;**[!UICONTROL Action>Recompute delivery and tracking indicators]**。 单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Finish]**。

![](assets/s_ncs_user_recalculate_indicators.png)

## 跟踪打开{#tracking-opens-}

为了让Adobe Campaign检测邮件打开，收件人必须下载电子邮件中的图像。 HTML和多部件/替代电子邮件包含0像素图像，使您能够检测已打开的消息。 由于文本格式的消息不包含任何图像，因此无法检测是否已打开它们。 由于链接到图像显示的误差范围，根据消息打开次数计算的值始终是估计值。

## 目标人员/收件人{#targeted-persons---recipients}

在某些报告中，Adobe Campaign区分目标人和目标收件人。

目标收件人是投放发送给的所有收件人。

人数包括目标收件人和转发邮件的所有人。 每次在新浏览器中打开或单击（消息尚未在中打开）时，都会向统计信息中添加其他人。

例如，如果您在工作时收到一封(由Adobe Campaign发送)电子邮件并打开或单击它，则您将被计为目标收件人(即收件人=1,person=1)。 如果您将此电子邮件转发给两位朋友，目标收件人的数量仍等于1，而人员数量将等于3。 值3与新浏览器中每次打开/单击的时间一致。
