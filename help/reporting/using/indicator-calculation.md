---
product: campaign
title: 指标计算
description: 指标计算
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 2%

---

# 指标计算 {#indicator-calculation}

![](../../assets/common.svg)

## 用户活动 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主键@totalClicks等于1的所有值总和。<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL类型等@totalClicks于“电子邮件点击”的所有URL总和。<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL类型@totalClicks等于“Transaction”的所有URL总和。<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此报表基于 **[!UICONTROL Consolidated tracking]** 表(nms:trackingStats)。 此汇总表用于显示报表时的性能原因，而不是 **[!UICONTROL Recipient tracking logs]** 表(nms:trackingLogRcp)，且不会实时计算。 在检索跟踪日志后几分钟内会生成表。 如果指标是最新的，则结果与 **跟踪指标** 报表。 @totalclicks指示器表示在5分钟内的点击总数。

## 无法投放项和退回 {#non-deliverables-and-bounces-1}

**按错误类型划分**

此报表基于 **[!UICONTROL Delivery and tracking statistics]** 表(nms:deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已处理消息的总数<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 状态等于“就绪”、“已发送”或“失败”的消息总和。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 状态等于“失败”且原因等于“用户未知”的所有消息的计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 不可访问 <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 状态等于“失败”且原因等于“不可到达”的所有消息的计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 被拒绝<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 状态等于“失败”且原因等于“已拒绝”的所有消息的计数。 <br /> </td> 
   <td> Count(@status=2,msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 域无效<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 状态等于“失败”且原因等于“域无效”的所有消息计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 帐户已禁用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 状态等于“失败”且原因等于“帐户已禁用”的所有消息计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱已满<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 状态等于“失败”且原因等于“收件箱已满”的所有消息的计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误<br /> </td> 
   <td> @value<br /> </td> 
   <td> 此类型错误的失败消息数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason="错误类型的值")<br /> </td> 
  </tr> 
  <tr> 
   <td> 贡献<br /> </td> 
   <td> -<br /> </td> 
   <td> 与错误消息总数相比，此类型的错误百分比。<br /> </td> 
   <td> 百分比(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 划分<br /> </td> 
   <td> -<br /> </td> 
   <td> 与已处理消息的总数相比，此类型的错误百分比。<br /> </td> 
   <td> 百分比(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**按域划分**

报告的第二部分详细说明了按互联网域（而不是错误类型）划分失败消息的情况。 链接到的公式 **错误** 指示器(@value)在这种情况下为：Count(@status=2 and @domain=&quot;域名的值&quot;)，即此域状态失败的所有消息的计数。

## 浏览器 {#browsers-1}

此报表基于 **[!UICONTROL Internet Browser Statistics]** 表(nms:userAgentsStats)。

**全局统计**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 访客<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 此浏览器中点击了投放至少一次的目标收件人总数。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 页面查看次数<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 使用此浏览器进行所有投放的投放链接点击总数。<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此浏览器的访客百分比与访客总数之比。<br /> </td> 
   <td> 百分比(@totalVisitors，总和(@totalVisitors) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**每个浏览器的统计信息**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 使用此浏览器的每日访客数与在访问次数最多的一天中测量的访客数的百分比。<br /> </td> 
   <td> percent(sum(@visitors),max(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与使用所有浏览器的访客总数相比，此版本的访客百分比。<br /> </td> 
   <td> 百分比(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对权重<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的访客百分比与使用此浏览器的访客总数相比。<br /> </td> 
   <td> 百分比(@totalVisitors，总和(@totalVisitors) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共享到社交网络 {#sharing-to-social-networks-1}

此报表基于 **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats)和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要投放的消息数<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 在投放分析期间处理的消息总数。<br /> </td> 
   <td> sum([属性/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功投放的次数<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的消息数 <br /> </td> 
   <td> sum([指标/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL类@totalClicks等于“email”的所有总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL类@totalClicks等于“facebook”的所有项总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL类@totalClicks等于“twitter”的所有项总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL类@totalClicks等于“可口”的所有值的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL类@totalClicks等于“digg”的所有总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL类@totalClicks等于“google”的所有总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 林克丁<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL类@totalClicks等于“linkedin”的所有项总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**共享**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
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
   <td> 此社交网络上的分享次数与分享总数的百分比。<br /> </td> 
   <td> 百分比(@forward，总和(@forward)<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 与要发送的消息数相比，此网络上的共享次数。<br /> </td> 
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
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
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
   <td> 划分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交网络上的打开次数与总打开次数的百分比。<br /> </td> 
   <td> 百分比(@open，总和(@open)<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 此社交网络上的打开次数与要投放的消息总数相比。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 关于共享活动的统计资料 {#statistics-on-sharing-activities-1}

此报表基于 **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats)和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 新联系人<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 链接到收件人的访客数。<br /> </td> 
   <td> 公式：count(@id)<br /> 过滤器：@recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL类@ids等于“Open”的所有计数。<br /> </td> 
   <td> count(Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享<br /> </td> 
   <td> @shared<br /> </td> 
   <td> “电子邮件”、“facebook”、“twitter”、“可口”、“digg”、“google”、“linkedin”中包含的URL类别<br /> URL类别@totalClicks=“email”、“facebook”、“twitter”、“delicious”、“digg”、“google”或“linkedin”的所有计数。<br /> </td> 
   <td> count([url/@category] IN(email' 、 'facebook' 、 'twitter' 、 'delicious' 、 'digg' 、 'google' 、 'linkedin')、 @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 操作系统 {#operating-systems-1}

此报表基于 **[!UICONTROL Internet Browser Statistics]** 表(nms:userAgentsStats)。

**全局统计**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 访客<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 操作系统定向的至少单击一次投放的收件人总数的每日平均值。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 查看的页面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 所有投放中每个操作系统投放链接的每日平均点击次数。<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 按操作系统划分的访客数与访客总数之比。<br /> </td> 
   <td> 百分比(@totalVisitors，总和(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**每个操作系统的统计信息**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 此操作系统中每日的访客数与在访问次数最多的当天测量的访客数的百分比。<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每个版本的访客百分比，与所有操作系统上的访客总数相比。<br /> </td> 
   <td> 百分比(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每个版本的访客百分比，与使用此操作系统的访客总数相比。<br /> </td> 
   <td> 百分比(@totalVisitors，总和(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 订阅跟踪 {#subscription-tracking-1}

此报表基于 **[!UICONTROL Services]** 表(nms:service)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已注册<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 前一天的注册人员计数。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 前一天的订阅计数(@action = 1)。<br /> </td> 
   <td> sum(Iif(@action = 1, @date &gt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 前一天的取消订阅计数（操作= 0）。<br /> </td> 
   <td> sum(Iif(@action = 0, @date &gt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 进化<br /> </td> 
   <td> -<br /> </td> 
   <td> 订阅数减去取消订阅数。 速率是相对于订阅者总数计算的。<br /> </td> 
   <td> Iif(数字(@_subscription)&gt;数字(@_unsubscription)，“+”，“)+格式(@_subscription - @_unsubscription, '数字', '# #0')+ Iif(@_subscriber&gt;0,'(' +格式(100*percent(@_subscription - @_unsubscription, @_subscriber), '数字', '#,##0.00')+ '%',")<br /> </td> 
  </tr> 
  <tr> 
   <td> 忠诚度<br /> </td> 
   <td> -<br /> </td> 
   <td> 相关时段的订阅者忠诚度比率。<br /> </td> 
   <td> 1%(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟踪指标 {#tracking-indicators-1}

此报表基于 **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats)和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要投放的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 目标分析后broadLogs的数量计数。<br /> </td> 
   <td> sum([属性/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> “种子地址”字段等于“否”且状态等于“服务提供商已考虑”、“已发送”或“在移动设备上接收”的消息计数。<br /> </td> 
   <td> sum([指标/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 到达的群体上显示不同的打开数<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根据html格式电子邮件的非重复打开数量，推断所有电子邮件的非重复打开数。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@recipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 达到的群体的打开总数<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根据html格式的电子邮件总打开数推断所有电子邮件的打开总数。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@totalRecipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击退订链接<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类@ids等于“选择退出”的所有计数。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击指向镜像页面的链接<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL类@ids等于“Mirror page”的所有计数。<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 前向估计<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 独特访客数量与点击了电子邮件至少一次的独特收件人数量之间的差异。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> “种子地址”字段等于“否”且状态等于“收件人已考虑”、“已发送”或“在移动设备上接收”的消息计数。<br /> </td> 
   <td> sum([指标/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 投诉<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 状态等于“失败”且原因等于“地址”的消息阻止列表计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有跟@broadLog-ids日志中的所有计数。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“电@broadLog-ids点击”的非重复计数。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 点击了投放至少一次的收件人数量与打开了投放至少一次的收件人数量的百分比。<br /> </td> 
   <td> 百分比(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 对达到的群体的不同点击<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类@source-ids等于“电子邮件点击”的所有计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累计点击量<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL类@ids等于“电子邮件点击”的所有计数。<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人点击<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“电子邮@broadLog-ids点击”的非重复计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 估计反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 点击了至少一次投放的收件人数量与打开了该投放至少一次的预计收件人数量的比率。<br /> </td> 
   <td> 百分比(@recipientClick,@estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 访问过的页面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL类型@ids等于“Web”或“交易”的所有计数。<br /> </td> 
   <td> count(Iif([url/@type]=4或[url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL类型@ids等于“交易”的所有计数。<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 总金额<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL类型等于“Transaction”的WebTrackingLog/@amounts总和。 <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均交易金额<br /> </td> 
   <td> -<br /> </td> 
   <td> 总金额与交易次数之比。<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 项目<br /> </td> 
   <td> @article<br /> </td> 
   <td> URL类型等于“Transaction”的WebTrackingLog/@articles的总和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 每笔交易的平均项目数<br /> </td> 
   <td> -<br /> </td> 
   <td> 项目数与交易次数的比率。<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每条消息的平均金额<br /> </td> 
   <td> -<br /> </td> 
   <td> 总量与要投放的消息数量之比。<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL类@totalClicks等于“email”的所有URL总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL类@totalClicks等于“facebook”的所有总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL类@totalClicks等于“twitter”的所有总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL类@totalClicks等于“可口”的所有URL总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL类@totalClicks等于“digg”的所有总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL类@totalClicks等于“google”的所有URL总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 林克丁<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL类@totalClicks等于“linkedin”的所有总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和点击流 {#urls-and-click-streams-1}

此报表基于 **[!UICONTROL Delivery]** 表(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 反应性<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 点击了至少一次投放的目标收件人数量与至少打开了一次投放的预计目标收件人数量的比率。<br /> </td> 
   <td> 百分比([指标/@recipientClick], [指标/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 非重复点击<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 至少点击一次投放的独特访客数量与成功投放的消息数量之比。<br /> </td> 
   <td> 百分比([指标/@personClick], [指标/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累计点击量<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目标收件人点击总次数与成功投放消息数量之比。<br /> </td> 
   <td> 百分比([指标/@totalRecipientClick], [指标/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主键与@totalClicks 1不同的所有项计数<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击量(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 点击次数与累计点击总数的百分比。<br /> </td> 
   <td> 百分比(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放摘要 {#delivery-summary-1}

此报表基于 **[!UICONTROL Delivery]** 表(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 初始群体<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 投放所定向的收件人总数。<br /> </td> 
   <td> sum([属性/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 规则拒绝的消息<br /> </td> 
   <td> @reject<br /> </td> 
   <td> 在分析过程中根据分类规则忽略的地址数：未指定地址、已隔离地址、已阻止列表等。<br /> </td> 
   <td> sum([属性/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 要投放的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 投放分析后要投放的消息总数。<br /> </td> 
   <td> sum([属性/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的消息数。<br /> </td> 
   <td> sum([指标/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误<br /> </td> 
   <td> @error<br /> </td> 
   <td> 在投放和自动退件处理过程中累积的错误总数。<br /> </td> 
   <td> sum([指标/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> 新隔离<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 投放失败后隔离的地址数（用户未知，域无效）。<br /> </td> 
   <td> sum([指标/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 热门点击 {#hot-clicks-1}

此报告基于Delivery(nms:delivery)和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表。

此报表可显示每个链接上的消息内容(HTML和/或文本)，以及链接的点击百分比。 个性化块退订链接和镜像页面链接在累计的总点击量中会得到考虑，但不会显示在报表中。

## 跟踪统计信息 {#tracking-statistics-1}

此报表基于 **[!UICONTROL Delivery]** 表(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL类型@totalClicks为“Transaction”的所有URL总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL类型等于“电@totalClicks单击”的所有URL总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主键@totalClicks等于1的所有总和。<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放统计 {#delivery-statistics-1}

此报表基于 **[!UICONTROL Delivery and tracking statistics]** 表(nms:deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 处理的电子邮件<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 状态等于“已就绪”、“已发送”或“失败”的消息总数。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 已交付<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的消息数。<br /> </td> 
   <td> 指标/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 硬退回<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 状态等于“失败”且原因等于“用户未知”的消息总数。<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 软退回<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 状态等于“失败”且原因等于“不可访问”、“收件箱已满”、“域名无效”、“禁用帐户”、“未连接”或“已拒绝”的所有消息总数<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 跟踪日志@broadLog-ids的总数。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别@source-ids为“电子邮件点击”的总数。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类别@ids为“选择退出”的总数。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 打开次数的划分 {#breakdown-of-opens-1}

此报表基于 **投放** (nms:delivery)和 **跟踪日志** (nms:trackingLogRcp)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指标描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主键@id等于1的所有值总和（打开）。 <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指标 {#other-indicators}

的 **已发送** 指示器(@sent)，通过 **投放(nms:delivery)>指示器** 节点对应于发送给服务提供商的短信总数。 此指示器仅用于短信投放，不得用于其他类型的投放(请不要与 **@success** 和 **@processed** 指标)。

## 指示器同步 {#indicator-synchronization}

如果您遇到某些指标的取消同步或不一致情况，请在Adobe Campaign资源管理器中选择相关的投放，右键单击并选择 **[!UICONTROL Action>Recompute delivery and tracking indicators]**. 单击 **[!UICONTROL Next]**，然后单击 **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## 跟踪打开次数 {#tracking-opens-}

为了使Adobe Campaign检测到消息打开，收件人必须下载电子邮件中的图像。 HTML和多部分/替代电子邮件包含0像素图像，可让您检测已打开的消息。 由于文本格式的消息不包含任何图像，因此无法检测是否已打开它们。 根据消息打开次数计算的值始终是估计值，因为与图像显示关联的误差范围。

## 目标人员/收件人 {#targeted-persons---recipients}

在某些报表中，Adobe Campaign会区分目标人员和目标收件人。

定向收件人是将投放发送到的所有收件人。

人数包括定向收件人以及将电子邮件转发给的所有人员。 每次在新浏览器中打开或单击（消息尚未在中打开）时，系统都会向统计信息中添加另一个人。

例如，如果您在工作时收到一封电子邮件(由Adobe Campaign发送)，并且打开或单击它，则将被计为目标收件人（即recipient=1,person=1）。 如果将此电子邮件转发给两位好友，则定向收件人的数量仍将等于1，而人员数量将等于3。 值3与新浏览器中每次打开/单击的时间一致。
