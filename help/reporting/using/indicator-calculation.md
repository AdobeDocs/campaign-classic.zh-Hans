---
product: campaign
title: 指标计算
description: 指标计算
badge: label="v7" type="信息性" tooltip="仅适用于Campaign Classicv7"
feature: Reporting
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '2983'
ht-degree: 7%

---

# 指标计算 {#indicator-calculation}



## 用户活动 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @打开次数<br /> </td> 
   <td> URL主键等于1的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([@url-id]=1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击次数<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL类型等于“Email click”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type]=1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @交易<br /> </td> 
   <td> URL类型等于“Transaction”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type]=5， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此报表基于 **[!UICONTROL Consolidated tracking]** 表(nms：trackingStats)。 显示报告时，出于性能原因，使用此汇总表代替 **[!UICONTROL Recipient tracking logs]** 表(nms：trackingLogRcp)并且不会实时计算。 表会在检索跟踪日志后的几分钟内生成。 如果各项指标是最新的，则结果将与以下各项指标相同： **跟踪指标** 报告。 @totalclicks指示器表示5分钟内的总点击次数。

## 无法投放项和退回 {#non-deliverables-and-bounces-1}

**按错误类型细分**

此报表基于 **[!UICONTROL Delivery and tracking statistics]** 表(nms：deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已处理的消息总数<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 状态等于“就绪”、“已发送”或“失败”的消息总数。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 状态等于“失败”且原因等于“用户未知”的所有消息计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 不可到达 <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 状态等于“失败”且原因等于“不可访问”的所有消息计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒绝<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 状态等于“失败”且原因等于“已拒绝”的所有消息计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 无效域<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 状态等于“失败”且原因等于“无效域”的所有消息计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 帐户被禁用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 状态等于“失败”且原因等于“帐户已禁用”的所有邮件的计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱已满<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 状态等于“失败”且原因等于“收件箱已满”的所有邮件计数。 <br /> </td> 
   <td> Count(@status=2和msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误<br /> </td> 
   <td> @值<br /> </td> 
   <td> 此类错误的失败消息数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason="错误类型的值")<br /> </td> 
  </tr> 
  <tr> 
   <td> 贡献<br /> </td> 
   <td> -<br /> </td> 
   <td> 相对于错误消息总数的此类型错误百分比。<br /> </td> 
   <td> percent(@value，@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 细分<br /> </td> 
   <td> -<br /> </td> 
   <td> 相对于已处理消息总数的此类型错误百分比。<br /> </td> 
   <td> percent(@value，@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**按域细分**

报告的第二部分详细列出了按Internet域而不是错误类型划分的失败消息。 链接到 **错误** 在此例中，指示符(@value)为：Count(@status=2和@domain=&quot;Value of the domain name&quot;)，即此域的所有状态为失败的消息计数。

## 浏览器 {#browsers-1}

此报表基于 **[!UICONTROL Internet Browser Statistics]** 表(nms：userAgentsStats)。

**全局统计信息**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 访客<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 此浏览器中至少点击过一次投放的目标收件人总数。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 页面查看次数<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 对于所有投放，使用此浏览器的投放链接的总点击次数。<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 相较于访客总数，此浏览器的访客百分比。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**每个浏览器的统计信息**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 每日使用此浏览器的访客数与当天访问次数最多的访客数的百分比。<br /> </td> 
   <td> 百分比(sum(@visitors)，max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 相较于使用所有浏览器的访客总数，此版本的访客百分比。<br /> </td> 
   <td> percent(@totalVisitors， @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对权重<br /> </td> 
   <td> -<br /> </td> 
   <td> 相对于使用此浏览器的访客总数的此版本访客百分比。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 分享到社交网络 {#sharing-to-social-networks-1}

此报表基于 **[!UICONTROL Delivery]** (nms：delivery)， **[!UICONTROL Consolidated tracking]** (nms：trackingStats)，和 **[!UICONTROL Web tracking]** (nms：webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要投放的消息数<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 投放分析期间处理的消息总数。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功投放的数量<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功处理的消息数 <br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @电子邮件<br /> </td> 
   <td> URL类别等于“email”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL类别等于“facebook”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL类别等于“twitter”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 好吃<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL类别等于“delicious”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL类别等于“digg”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL类别等于“google”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL类别等于“linkedin”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin'，@totalClicks，0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**共享**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 股份数量<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 在此社交网络上共享的邮件总数。<br /> </td> 
   <td> Sum(iIf([url/@category]="社交网络类型的值"，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 细分<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 此社交网络上的股份数相对于股份总数的百分比。<br /> </td> 
   <td> percent(@forward， sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 此网络上的共享数量与要发送的消息数量相比。<br /> </td> 
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
   <th> <strong>指示器描述</strong> <br /> </th> 
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
   <td> 细分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交网络上的打开数占总打开数的百分比。<br /> </td> 
   <td> percent(@open， sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 相较于要投放的消息总数，此社交网络上的打开数。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共享活动的统计数据 {#statistics-on-sharing-activities-1}

此报表基于 **[!UICONTROL Delivery]** (nms：delivery)， **[!UICONTROL Consolidated tracking]** (nms：trackingStats)，和 **[!UICONTROL Web tracking]** (nms：webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 新联系人<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 链接到收件人的访客总数。<br /> </td> 
   <td> 公式： count(@id)<br /> 筛选器：@recipient-id！= 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL类型等于“Open”的所有@ids的计数。<br /> </td> 
   <td> count (Iif([url/@type] = 2， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享<br /> </td> 
   <td> @shared<br /> </td> 
   <td> “电子邮件”、“facebook”、“twitter”、“delicious”、“digg”、“google”、“linkedin”中包含的URL类别<br /> URL类别等于“email”、“facebook”、“twitter”、“delicious”、“digg”、“google”或“linkedin”的所有@totalClicks的计数。<br /> </td> 
   <td> count (Iif([url/@category] IN (email' 、 'facebook' 、 'twitter' 、 'delicious' 、 'digg' 、 'google' 、 'linkedin')， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 操作系统 {#operating-systems-1}

此报表基于 **[!UICONTROL Internet Browser Statistics]** 表(nms：userAgentsStats)。

**全局统计信息**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 访客<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 操作系统定向的收件人中至少点击一次投放的每日平均总数。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已查看的页面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 所有投放中每个操作系统的投放链接每日平均点击总数。<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与访客总数相比的每个操作系统的访客细分。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**每个操作系统的统计信息**

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 该操作系统上每天的访客数与当天访问次数最多的访客数的百分比。<br /> </td> 
   <td> 百分比(sum(@visitors)， max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 相对于所有操作系统上的访客总数的每个版本的访客百分比。<br /> </td> 
   <td> percent(@totalVisitors， @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与使用此操作系统的访客总数相比，每个版本的访客百分比。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 订阅跟踪 {#subscription-tracking-1}

此报表基于 **[!UICONTROL Services]** 表(nms：service)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已注册<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 前一天已注册人员的数量。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate()， (-1))， 1， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 前一天订阅的次数(@action = 1)。<br /> </td> 
   <td> sum(Iif(@action = 1和@date &gt; addDays(getDate()， (-1))， 1， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 前一天取消订阅的次数（操作= 0）。<br /> </td> 
   <td> sum(Iif(@action = 0和@date &gt; addDays(getDate()， (-1))， 1， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 演变<br /> </td> 
   <td> -<br /> </td> 
   <td> 订阅数减去取消订阅数。 比率根据订阅者总数计算。<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription)， '+'， ")+format(@_subscription - @_unsubscription， 'number'， '# ##0')+ Iif(@_subscriber&gt;0，' (' + format(100*percent(@_subscription - @_unsubscription， @_subscriber)， 'number'， '#，##0.00')+ '%)'，")<br /> </td> 
  </tr> 
  <tr> 
   <td> 忠诚度<br /> </td> 
   <td> -<br /> </td> 
   <td> 相关期间的订阅者忠诚度比率。<br /> </td> 
   <td> 1%(@_unsubscription，@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟踪指标 {#tracking-indicators-1}

此报表基于 **[!UICONTROL Delivery and tracking statistics]** (nms：deliveryLogStats)和 **[!UICONTROL Consolidated tracking]** (nms：trackingStats)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要发送的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 目标分析后的broadLog数量计数。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> “种子地址”字段等于“否”且状态等于“服务提供商已考虑”、“已发送”或“已在移动设备上接收”的消息计数。<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 所访问群体的不同打开次数<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根据html格式电子邮件的不同打开数推断所有电子邮件的不同打开数。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0， 0， round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text])， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 达到的群体的打开次数总和<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根据html格式的电子邮件打开总数推断所有电子邮件的打开总数。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0， 0， round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text])， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击退订链接<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类别等于“选择退出”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=3， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击指向镜像页面的链接<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL类别等于“镜像页面”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=6， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 转发数量估计<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 不同用户数与至少在电子邮件中点击过一次的不同收件人数之间的差异。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> “种子地址”字段等于“否”且状态等于“收件人已考虑”、“已发送”或“已在移动设备上接收”的消息计数。<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 投诉<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 状态等于“失败”且原因等于“阻止列表时的地址”的邮件数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有跟踪日志中的所有@broadLog-ids计数。<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击次数<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“Email click”的@broadLog-ids的不同计数。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @broadLog-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 与至少打开投放一次的收件人人数相比，至少点击一次投放的收件人人数的百分比。<br /> </td> 
   <td> percent(@recipientClick，@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 所达到群体的不同点击次数<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别等于“Email click”的所有@source-ids的计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @source-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累计点击次数<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL类别等于“Email click”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=1， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人点击次数<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“Email click”的@broadLog-ids的非重复计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @broadLog-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 预计的反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 至少点击一次投放的收件人数量与至少打开投放一次的收件人估计数的比率。<br /> </td> 
   <td> percent(@recipientClick， @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 已访问页面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL类型等于“Web”或“Transaction”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=4或[url/@type]=5， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL类型等于“事务”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=5， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 总金额<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL类型等于“Transaction”的webTrackingLog/@amounts的总和。 <br /> </td> 
   <td> Sum(Iif([url/@type]=5， webTrackingLog/@amount， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均交易金额<br /> </td> 
   <td> -<br /> </td> 
   <td> 总金额与交易数量之比。<br /> </td> 
   <td> div(@amount， @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 项目<br /> </td> 
   <td> @article<br /> </td> 
   <td> URL类型等于“Transaction”的webTrackingLog/@articles的总和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5， webTrackingLog/@article， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 每笔交易的平均项目数<br /> </td> 
   <td> -<br /> </td> 
   <td> 项目数与交易数之比。<br /> </td> 
   <td> div(@article， @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每条消息的平均数量<br /> </td> 
   <td> -<br /> </td> 
   <td> 总数量与要投放的消息数量的比率。<br /> </td> 
   <td> div(@amount， @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @电子邮件<br /> </td> 
   <td> URL类别等于“email”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL类别等于“facebook”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL类别等于“twitter”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 好吃<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> 具有等于“delicious”的URL类别的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL类别等于“digg”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL类别等于“google”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL类别等于“linkedin”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin'，@totalClicks，0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和点击流 {#urls-and-click-streams-1}

此报表基于 **[!UICONTROL Delivery]** 表(nms：delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 反应度<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 至少点击一次投放的目标收件人数量与至少打开投放一次的估计目标收件人数量的比率。<br /> </td> 
   <td> percent([指示器/@recipientClick]， [指示器/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 不同的点击次数<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 与成功投放的消息数相比，已单击投放至少一次的不同用户数的比率。<br /> </td> 
   <td> percent([指示器/@personClick]， [指示器/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累计点击次数<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目标收件人的点击总数与成功投放的消息数之间的比率。<br /> </td> 
   <td> percent([指示器/@totalRecipientClick]， [指示器/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击次数<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主键与1不同的所有@totalClicks的计数<br /> </td> 
   <td> count(Iif([@url-id]] ！= 1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击次数 (%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 点击数相对于累计点击总数的百分比。<br /> </td> 
   <td> percent(@_click， @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放摘要 {#delivery-summary-1}

此报表基于 **[!UICONTROL Delivery]** 表(nms：delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 初始群体<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 投放所定向的收件人总数。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 规则拒绝的消息<br /> </td> 
   <td> @reject<br /> </td> 
   <td> 根据分类规则，分析期间忽略的地址数：未指定地址、被隔离、阻止列表时等。<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 要发送的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 投放分析后要投放的消息总数。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的消息数。<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误<br /> </td> 
   <td> @error<br /> </td> 
   <td> 投放和自动退回处理期间累计的错误总数。<br /> </td> 
   <td> sum([indicators/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> 新隔离<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 投放失败（用户未知，无效域）后隔离的地址数。<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 热门点击 {#hot-clicks-1}

此报表基于投放(nms：delivery)和 **[!UICONTROL Consolidated tracking]** (nms：trackingStats)表。

此报告显示邮件内容（HTML 和/或文本）以及每个链接的点击百分比。个性化块退订链接和镜像页面链接在总累计点击量中会被考虑在内，但不会显示在报表中。

## 跟踪统计信息 {#tracking-statistics-1}

此报表基于 **[!UICONTROL Delivery]** 表(nms：delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @交易<br /> </td> 
   <td> URL类型等于“Transaction”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击次数<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL类型等于“Email click”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @打开次数<br /> </td> 
   <td> URL主键等于1的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([@url-id] = 1， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放统计信息 {#delivery-statistics-1}

此报表基于 **[!UICONTROL Delivery and tracking statistics]** 表(nms：deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已处理电子邮件<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 状态等于“就绪”、“已发送”或“失败”的消息总数。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 已送达<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功处理的消息数。<br /> </td> 
   <td> 指示器/@success<br /> </td> 
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
   <td> 状态等于“失败”且原因等于“不可访问”、“收件箱已满”、“无效域”、“帐户已禁用”、“未连接”或“已拒绝”的所有邮件的总数<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 跟踪日志中的@broadLog-ids动总数。<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击次数<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别等于“电子邮件点击”的@source-ids的总数。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @source-id， 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类别等于“选择退出”的@ids的总数。<br /> </td> 
   <td> count(Iif([url/@type]=3， @id， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 打开的细分 {#breakdown-of-opens-1}

此报表基于 **投放** (nms：delivery)和 **跟踪日志** (nms：trackingLogRcp)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>标签</strong> <br /> </th> 
   <th> <strong>字段名称</strong> <br /> </th> 
   <th> <strong>指示器描述</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主键等于1（打开）的所有@id的总和。 <br /> </td> 
   <td> count(Iif([@url-id] = 1， @id， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指标 {#other-indicators}

此 **已发送** 指示器(@sent)，可通过 **投放(nms：delivery) >指标** 节点对应于发送到服务提供商的SMS总数。 此指示器仅用于短信投放，不得用于其他类型的投放(切勿与 **@success** 和 **@processed** 指示器)。

## 指示器同步 {#indicator-synchronization}

如果某些指示器出现不同步或不一致情况，请在Adobe Campaign资源管理器中选择相关的投放，右键单击并选择 **[!UICONTROL Action>Recompute delivery and tracking indicators]**. 单击 **[!UICONTROL Next]**，然后单击 **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## 跟踪打开次数 {#tracking-opens-}

为了让Adobe Campaign检测邮件打开，收件人必须下载电子邮件中的图像。 HTML和多部分/替代电子邮件包括0像素图像，可让您检测已打开的邮件。 由于文本格式的消息不包含任何图像，因此无法检测这些消息是否已打开。 由于与图像显示相关的误差，根据消息打开度计算的值始终为估计值。

## 目标人员/收件人 {#targeted-persons---recipients}

在一些报表中，Adobe Campaign会区分目标人员和目标收件人。

目标收件人是指接收投放的所有收件人。

人数包括定向收件人以及转发电子邮件的所有人员。 每次在新浏览器中打开或单击时（消息尚未在其中打开），都会将另一个人添加到统计数据中。

例如，如果您在工作时收到一封电子邮件(由Adobe Campaign发送)，并在其中打开或单击该电子邮件，则您将被计为定向收件人（即recipient=1， person=1）。 如果您将此电子邮件转发给两个好友，则定向收件人数量将仍等于一，而人数将等于三。 值3与新浏览器中的每次打开/单击一致。
