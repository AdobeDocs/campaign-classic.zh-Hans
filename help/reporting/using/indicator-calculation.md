---
product: campaign
title: 指标计算
description: 指标计算
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3049'
ht-degree: 3%

---

# 指标计算 {#indicator-calculation}



## 用户活动 {#user-activities-1}

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
   <td> URL主键等于1的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([@url-id]=1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL类型等于“Email click”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type]=1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL类型等于“Transaction”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type]=5， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此报表基于&#x200B;**[!UICONTROL Consolidated tracking]**&#x200B;表(nms：trackingStats)。 在显示报表时，出于性能原因，使用此聚合表代替&#x200B;**[!UICONTROL Recipient tracking logs]**&#x200B;表(nms：trackingLogRcp)，并且不会实时计算它。 该表将在检索跟踪日志后几分钟生成。 如果指标是最新的，则结果将与&#x200B;**跟踪指标**&#x200B;报告的指标相同。 @totalclicks指示器表示5分钟内的点击总数。

## 无法投放项和退回 {#non-deliverables-and-bounces-1}

**按错误类型划分**

此报表基于&#x200B;**[!UICONTROL Delivery and tracking statistics]**&#x200B;表(nms：deliveryLogStats)。

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
   <td> 已处理的消息总数<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 状态等于“就绪”、“已发送”或“失败”的消息总数。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 状态等于“失败”且原因等于“用户未知”的所有消息计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 无法访问<br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 状态等于“失败”且原因等于“不可访问”的所有消息计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒绝<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 状态等于“失败”且原因等于“已拒绝”的所有邮件计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 域<br />无效 </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 状态等于“失败”且原因等于“无效域”的所有消息计数。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 帐户已禁用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 状态等于“失败”且原因等于“帐户已禁用”的所有邮件的计数。<br /> </td> 
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
   <td> 此错误类型的失败消息数。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason="错误类型的值")<br /> </td> 
  </tr> 
  <tr> 
   <td> 贡献<br /> </td> 
   <td> -<br /> </td> 
   <td> 相对于错误消息总数的此类型错误百分比。<br /> </td> 
   <td> percent(@value，@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 划分<br /> </td> 
   <td> -<br /> </td> 
   <td> 相对于已处理消息总数的此类型错误百分比。<br /> </td> 
   <td> percent(@value，@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**按域划分**

报告的第二部分详细列出了按Internet域而非错误类型划分的失败消息。 在此例中，链接到&#x200B;**Error**&#x200B;指示器(@value)的公式为：Count(@status=2和@domain=&quot;Value of the domain name&quot;)，即此域的所有状态为失败的消息计数。

## 浏览器 {#browsers-1}

此报表基于&#x200B;**[!UICONTROL Internet Browser Statistics]**&#x200B;表(nms：userAgentsStats)。

**全局统计信息**

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
   <td> 此浏览器中至少点击过一次投放的目标收件人总数。<br /> </td> 
   <td> 总@visitors<br /> </td> 
  </tr> 
  <tr> 
   <td> 页面查看次数<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 对于所有投放，使用此浏览器的投放链接的总点击次数。<br /> </td> 
   <td> 总@pages<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此浏览器的访客相对于访客总数的百分比。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

每个浏览器的&#x200B;**统计信息**

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
   <td> 每日使用此浏览器的访客数与当天测量访问次数最多的访客数的百分比。<br /> </td> 
   <td> percent(sum(@visitors)，max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与使用所有浏览器的访客总数相比，此版本的访客百分比。<br /> </td> 
   <td> 百分比(@totalVisitors， @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相对权重<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的访客与使用此浏览器的访客总数相比的百分比。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 分享到社交网络 {#sharing-to-social-networks-1}

此报表基于&#x200B;**[!UICONTROL Delivery]** (nms：delivery)、**[!UICONTROL Consolidated tracking]** (nms：trackingStats)和&#x200B;**[!UICONTROL Web tracking]** (nms：webTrackingLog)表。

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
   <td> 要投放的消息数<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 传递分析期间处理的邮件总数。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功投放的数量<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功处理的邮件数<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL类别等于“email”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL类别等于“facebook”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL类别等于“twitter”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
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
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 共享数量<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 在此社交网络上共享的邮件总数。<br /> </td> 
   <td> Sum(iIf([url/@category]="社交网络类型的值"，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 划分<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 此社交网络上的股份数相对于股份总数的百分比。<br /> </td> 
   <td> percent(@forward， sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共享率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 与要发送的消息数相比，此网络上的共享数。<br /> </td> 
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
   <td> Web跟踪表中的跟踪行总数。<br /> </td> 
   <td> 计数<br /> </td> 
  </tr> 
  <tr> 
   <td> 划分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交网络上的打开数相对于打开总数的百分比。<br /> </td> 
   <td> percent(@open， sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 与要发送的邮件总数相比，此社交网络上的打开数。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共享活动统计信息 {#statistics-on-sharing-activities-1}

此报表基于&#x200B;**[!UICONTROL Delivery]** (nms：delivery)、**[!UICONTROL Consolidated tracking]** (nms：trackingStats)和&#x200B;**[!UICONTROL Web tracking]** (nms：webTrackingLog)表。

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
   <td> 链接到收件人的访客计数。<br /> </td> 
   <td> 公式： count(@id)<br />筛选器： @recipient-id！= 0<br /> </td> 
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
   <td> 包含在“email”、“facebook”、“twitter”、“delicious”、“digg”、“google”、“linkedin”中的URL类别数<br />所有URL类别等于“email”、“facebook”、“twitter”、“delicious”、“digg”、“google”或“linkedin”的@totalClicks数。<br /> </td> 
   <td> count (Iif([url/@category] IN (email' ， 'facebook' ， 'twitter' ， 'delicious' ， 'digg' ， 'google' ， 'linkedin')， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 操作系统 {#operating-systems-1}

此报表基于&#x200B;**[!UICONTROL Internet Browser Statistics]**&#x200B;表(nms：userAgentsStats)。

**全局统计信息**

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
   <td> 操作系统所定向的收件人中至少点击过一次投放的每日平均总数。<br /> </td> 
   <td> 总@visitors<br /> </td> 
  </tr> 
  <tr> 
   <td> 已查看的页面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 所有投放的每个操作系统上的投放链接每日平均点击总数。<br /> </td> 
   <td> 总@pages<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与访客总数相比，每个操作系统的访客细分。<br /> </td> 
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
   <th> <strong>指示器说明</strong> <br /> </th> 
   <th> <strong>指标计算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 该操作系统上每天的访客数与当天测量访问次数最多的访客数的百分比。<br /> </td> 
   <td> percent(sum(@visitors)， max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 与所有操作系统上的访客总数相比，每个版本的访客百分比。<br /> </td> 
   <td> 百分比(@totalVisitors， @globalVisitors)<br /> </td> 
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

此报表基于&#x200B;**[!UICONTROL Services]**&#x200B;表(nms：service)。

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
   <td> 前一天已注册人员的数量。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate()， (-1))， 1， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 订阅<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 前一天的订阅计数(@action = 1)。<br /> </td> 
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
   <td> 订阅数减去退订数。 比率是相对于订阅者总数计算的。<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription)， '+'， ")+format(@_subscription - @_unsubscription， 'number'， '# ##0')+ Iif(@_subscriber&gt;0，' (' +格式(100*percent(@_subscription - @_unsubscription， @_subscriber)， 'number'， '#，##0.00')+ '%)'，")<br /> </td> 
  </tr> 
  <tr> 
   <td> 忠诚度<br /> </td> 
   <td> -<br /> </td> 
   <td> 相关期间的订阅者忠诚度比率。<br /> </td> 
   <td> 百分之1(@_unsubscription，@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟踪指标 {#tracking-indicators-1}

此报表基于&#x200B;**[!UICONTROL Delivery and tracking statistics]** (nms：deliveryLogStats)和&#x200B;**[!UICONTROL Consolidated tracking]** (nms：trackingStats)表。

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
   <td> 要传递的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 目标分析后的broadLog数量计数。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> “种子地址”字段等于“否”且状态等于“服务提供商已考虑”、“已发送”或“移动设备已接收”的消息计数。<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 到达的群体<br />上存在不同的打开次数 </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根据html格式的电子邮件非重复打开数推断所有电子邮件的非重复打开数。<br /> </td> 
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
   <td> URL类别等于“选择退出”的所有@ids计数。<br /> </td> 
   <td> count(Iif([url/@type]=3， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 单击指向镜像页面的链接<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL类别等于“镜像页面”的所有@ids计数。<br /> </td> 
   <td> count(Iif([url/@type]=6， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 转发的估计<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 不同人员数与至少点击一次电子邮件的不同收件人数之间的差异。<br /> </td> 
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
   <td> 点击次数<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“Email click”的@broadLog-ids的不同计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @broadLog-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 与至少打开一次投放的收件人数量相比，至少点击一次投放的收件人数量的百分比。<br /> </td> 
   <td> percent(@recipientClick，@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 达到的群体的不同点击次数<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别等于“Email click”的所有@source-ids的计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @source-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累计点击次数<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL类别等于“电子邮件点击”的所有@ids计数。<br /> </td> 
   <td> count(Iif([url/@type]=1， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人点击<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL类型等于“Email click”的@broadLog-ids的非重复计数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @broadLog-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 估计的反应性<br /> </td> 
   <td> -<br /> </td> 
   <td> 与至少打开一次投放的收件人估计人数相比，已至少点击一次投放的收件人人数的比率。<br /> </td> 
   <td> 百分比(@recipientClick， @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 已访问页面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL类型等于“Web”或“Transaction”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=4或[url/@type]=5， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL类型等于“Transaction”的所有@ids的计数。<br /> </td> 
   <td> count(Iif([url/@type]=5， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 总金额<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL类型等于“Transaction”的webTrackingLog/@amounts的总和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5， webTrackingLog/@amount， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均交易金额<br /> </td> 
   <td> -<br /> </td> 
   <td> 总金额与交易数之比。<br /> </td> 
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
   <td> 项数与事务数的比率。<br /> </td> 
   <td> div(@article， @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每封邮件的平均数量<br /> </td> 
   <td> -<br /> </td> 
   <td> 总金额与要投放的消息数之比。<br /> </td> 
   <td> div(@amount， @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 电子邮件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL类别等于“email”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL类别等于“facebook”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL类别等于“twitter”的所有@totalClicks的总和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
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

## URL 和点击流 {#urls-and-click-streams-1}

此报表基于&#x200B;**[!UICONTROL Delivery]**&#x200B;表(nms：delivery)。

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
   <td> 与至少打开一次投放的目标收件人的估计数量相比，已至少点击一次投放的目标收件人数量比率。<br /> </td> 
   <td> percent([indicators/@recipientClick]， [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 非重复点击<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 与成功投放的消息数相比，已至少点击一次投放的不同用户数的比率。<br /> </td> 
   <td> percent([indicators/@personClick]， [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累计点击次数<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目标收件人的点击总数与成功传递的邮件数的比率。<br /> </td> 
   <td> percent([indicators/@totalRecipientClick]， [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主键不同于1<br />的所有@totalClicks的计数 </td> 
   <td> count(Iif([@url-id] ！= 1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 点击数相对于累计点击总数的百分比。<br /> </td> 
   <td> 百分比(@_click， @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放摘要 {#delivery-summary-1}

此报表基于&#x200B;**[!UICONTROL Delivery]**&#x200B;表(nms：delivery)。

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
   <td> 初始群体<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 投放定向的收件人总数。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 规则<br />拒绝的消息 </td> 
   <td> @reject<br /> </td> 
   <td> 根据类型规则在分析期间忽略的地址数：未指定地址、已隔离、阻止列表时忽略的地址等。<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 要传递的消息<br /> </td> 
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
   <td> 新建隔离<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 投放失败（用户未知，无效域）后隔离的地址数。<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 热门点击 {#hot-clicks-1}

此报表基于Delivery(nms：delivery)和&#x200B;**[!UICONTROL Consolidated tracking]** (nms：trackingStats)表。

此报告显示邮件内容（HTML 和/或文本）以及每个链接的点击百分比。个性化块退订链接和镜像页面链接在总累计点击量中会被考虑在内，但不会显示在报表中。

## 跟踪统计数据 {#tracking-statistics-1}

此报表基于&#x200B;**[!UICONTROL Delivery]**&#x200B;表(nms：delivery)。

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
   <td> URL类型等于“Transaction”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL类型等于“Email click”的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([url/@type] = 1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主键等于1的所有@totalClicks的总和。<br /> </td> 
   <td> sum(Iif([@url-id] = 1， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放统计信息 {#delivery-statistics-1}

此报表基于&#x200B;**[!UICONTROL Delivery and tracking statistics]**&#x200B;表(nms：deliveryLogStats)。

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
   <td> 已处理电子邮件<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 状态为“就绪”、“已发送”或“失败”的消息总数。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 已投放<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功处理的消息数。<br /> </td> 
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
   <td> 状态等于“失败”且原因等于“不可访问”、“收件箱已满”、“无效域”、“帐户已禁用”、“未连接”或“已拒绝”的所有邮件总数<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 打开<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 跟踪日志中的@broadLog-ids总数。<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 点击次数<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL类别等于“Email click”的@source-ids件总数。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @source-id， 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 取消订阅<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL类别等于“选择退出”的@ids总数。<br /> </td> 
   <td> count(Iif([url/@type]=3， @id， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 打开的细分 {#breakdown-of-opens-1}

此报表基于&#x200B;**投放** (nms：delivery)和&#x200B;**跟踪日志** (nms：trackingLogRcp)表。

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
   <td> URL主键等于1（打开）的所有@id的总和。<br /> </td> 
   <td> count(Iif([@url-id] = 1， @id， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指标 {#other-indicators}

通过&#x200B;**投放(nms：delivery) > Indicators**&#x200B;节点访问的&#x200B;**已发送**&#x200B;指示器(@sent)对应于发送到服务提供商的SMS总数。 此指示器仅用于SMS投放，不得用于其他类型的投放(不要与&#x200B;**@success**&#x200B;和&#x200B;**@processed**&#x200B;指示器混淆)。

## 指示器同步 {#indicator-synchronization}

如果某些指标出现去同步或不一致情况，请在Adobe Campaign资源管理器中选择相关投放，右键单击并选择&#x200B;**[!UICONTROL Action>Recompute delivery and tracking indicators]**。 单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Finish]**。

![](assets/s_ncs_user_recalculate_indicators.png)

## 跟踪打开次数 {#tracking-opens-}

为了让Adobe Campaign检测邮件打开，收件人必须下载电子邮件中的图像。 HTML 和多部分/替代电子邮件包含 0 像素图像，可让您检测已打开的消息。由于采用文本格式的消息不包含任何图像，因此，无法检测它们是否已打开。由于与图像显示相关的误差范围，基于消息打开次数计算的值始终是估计值。

## 目标人员/收件人 {#targeted-persons---recipients}

在一些报表中，Adobe Campaign会区分目标人员和目标收件人。

定向收件人是指接收投放的所有收件人。

人数，包括定向收件人以及电子邮件转发给的所有人员。 每次打开或单击新浏览器（消息尚未在其中打开）时，都会将另一个人添加到统计数据中。

例如，如果您在工作时收到一封电子邮件(由Adobe Campaign发送)，并且打开或单击该电子邮件，则您将被计为定向收件人（即，recipient=1， person=1）。 如果您将此电子邮件转发给两位好友，则定向收件人数量将仍等于1，而人员数量将等于3。 值3与新浏览器中的每次打开/单击一致。
