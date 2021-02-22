---
solution: Campaign Classic
product: campaign
title: 监控流程
description: 了解如何监控活动流程
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '3602'
ht-degree: 0%

---


# 监控流程{#monitoring-processes}

可以手动或自动监控应用服务器和重定向服务器（**跟踪**）。

## 手动监视{#manual-monitoring}

转至&#x200B;**[!UICONTROL Monitoring]**&#x200B;并单击&#x200B;**[!UICONTROL Overview]**&#x200B;链接以显示Adobe Campaign进程监视页。

![](assets/d_ncs_monitoring.png)

通过显示的页面，您可以视图已连接实例的状态，即：

* 有关实例的信息：版本，名称，数据库引擎，已安装的包，服务器系统指示器，
* 缺失进程和执行信息(开始日期、PID等)的列表,
* 视图工作流和投放。

[本页](../../production/using/monitoring-guidelines.md)中提供了监控不同活动过程的其他方法。

### 日志日志{#log-journal}

可以显示与进程相关的日志日志。 要执行此操作，请单击进程，例如&#x200B;**mta**，然后单击&#x200B;**[!UICONTROL Open the log journal]**。

![](assets/d_ncs_monitoring2.png)

### 系统指示器{#system-indicators}

系统指示器的列表使您能够显示有关计算机的信息，如其物理和虚拟内存、活动进程和可用磁盘空间。 Linux和Windows操作系统的指示器不同。 转到&#x200B;**[!UICONTROL Instance Monitoring]**&#x200B;页面并单击&#x200B;**[!UICONTROL Display]**&#x200B;链接以打开指示器列表

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]** :消息中心特 **定的指示符**。有关详细信息，请参阅[本节](../../message-center/using/monitoring-thresholds.md)。
* **[!UICONTROL Memory]** :有关物理内存(RAM)的信息。

   **[!UICONTROL Current value]** :实际内存消耗。

   **[!UICONTROL Max Value]** :安装的内存总量。

   **[!UICONTROL Available]** :可用内存量。

   **[!UICONTROL Warning]** :当内存消耗达到总量的80%时，将显示此指示器。

   **[!UICONTROL Alert]** :当内存消耗达到总量的90%时，将显示此指示器。

   当显示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指示器时，可以通过向安装Adobe Campaign服务器的计算机添加RAM来解决此问题。 您还可以决定在专用计算机上安装Adobe Campaign服务器。

* **[!UICONTROL Swap Memory]** :与与分页文件匹配的虚拟内存相关的信息：硬盘上的一个区域，Windows使用它，就像RAM一样。

   **[!UICONTROL Current value]** :实际内存消耗。

   **[!UICONTROL Max Value]** :内存总量。

   **[!UICONTROL Available]** :可用内存量。

   **[!UICONTROL Warning]** :当内存消耗达到总量的80%时，将显示此指示器。

   **[!UICONTROL Alert]** :当内存消耗达到总量的90%时，将显示此指示器。

   当显示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指示器时，您可以通过在高级Windows设置中增加交换文件的大小来解决问题。

* **[!UICONTROL Disk XXX]** :有关机器阅读器的信息。

   **[!UICONTROL Current value]** :实际使用的磁盘空间。

   **[!UICONTROL Max Value]** :磁盘总容量。

   **[!UICONTROL Available]** :可用磁盘空间

   **[!UICONTROL Used]** :已使用磁盘的百分比。

   **[!UICONTROL Warning]** :当可用磁盘空间达到总容量的80%时，将显示此指示器。

   **[!UICONTROL Alert]** :当可用磁盘空间达到总容量的90%时，将显示此指示器。

* **[!UICONTROL Number of processes too old]** :有关已活动一天以上的Adobe Campaign流程的信息。

   **[!UICONTROL Current value]** :当前处于活动状态的进程数。

   **[!UICONTROL Max Value]** :最大授权进程数(1)。

   **[!UICONTROL Alert]** :如果进程数等于1，则显示此指示器。

   当显示&#x200B;**[!UICONTROL Alert]**&#x200B;指示器时，可能是相关进程被SQL数据库引擎锁定，或者它卡在无限循环中。 Adobe Campaign提供的&#x200B;**watchdog**&#x200B;进程每天自动重新开始所有进程，使您能够解决此问题。 但是，您也可以自行停止相关过程以强制重新开始。

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]** :消息中心特 **定的指示符**。有关详细信息，请参阅[本节](../../message-center/using/monitoring-thresholds.md)。
* **[!UICONTROL Load average (1/5/15 minutes)]** :有关负载的信息，即在最后一分钟、五分钟或十五分钟内计算机上运行的进程对处理器的使用率

   **[!UICONTROL Current value]** :机器的实际负载。

   **[!UICONTROL Max value]** :机器上进程的最大使用负载

   **[!UICONTROL Warning]** :在最后一分钟、五分钟或十五分钟内，当负载达到最大授权值的80%时，将显示此指示器。

   **[!UICONTROL Alert]** :当负载达到最后一分钟、五分钟或十五分钟的最高授权值的90%时，将显示此指示器。

* **[!UICONTROL Memory]** :有关物理内存(RAM)的信息。

   **[!UICONTROL Current value]** :实际内存消耗。

   **[!UICONTROL Max Value]** :安装的内存总量。

   **[!UICONTROL Available]** :可用内存量。

   **[!UICONTROL Warning]** :当内存消耗达到总量的80%时，将显示此指示器。

   **[!UICONTROL Alert]** :当内存消耗达到总量的90%时，将显示此指示器。

   当显示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指示器时，可以通过向安装Adobe Campaign服务器的计算机添加RAM来解决此问题。 您还可以决定在专用计算机上安装Adobe Campaign服务器。

* **[!UICONTROL Swap Memory]** :与与分页文件匹配的虚拟内存相关的信息：硬盘上的一个区域，Windows使用它，就像RAM一样。

   **[!UICONTROL Current value]** :实际内存消耗。

   **[!UICONTROL Max Value]** :内存总量。

   **[!UICONTROL Available]** :可用内存量。

   **[!UICONTROL Warning]** :当内存消耗达到总量的80%时，将显示此指示器。

   **[!UICONTROL Alert]** :当内存消耗达到总量的90%时，将显示此指示器。

   当显示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指示器时，可以通过增加交换文件的大小来解决问题。

* **[!UICONTROL Core Files]** :有关在Adobe Campaign进程崩溃后生成的文件的信息。这些文件使您能够诊断崩溃的原因。

   **[!UICONTROL Current Value]** :现有文件数。

   **[!UICONTROL Max Value]** :最大授权文件数(1)。

   **[!UICONTROL Warning]** :当文件数接近1时，将显示此指示器。

   **[!UICONTROL Alert]** :当文件数等于1时，将显示此指示器。

   当由于崩溃而丢失进程时，进程在进程列表上以红色显示，并由Adobe Campaign提供的&#x200B;**watchdog**&#x200B;进程自动重新启动。

* **[!UICONTROL Number of shared memory segments]** :与所有Adobe Campaign进程共享的内存段相关的信息。

   **[!UICONTROL Current value]** :当前使用的内存段数。

   **[!UICONTROL Max Value]** :已授权的最大内存段数(2)。

   **[!UICONTROL Warning]** :当内存段数达到1时，将显示此指示器。

   **[!UICONTROL Alert]** :当内存段数达到2时，将显示此指示器。

* **[!UICONTROL Number of processes too old]** :已活动超过一天的进程的相关信息。

   **[!UICONTROL Current value]** :当前处于活动状态的进程数。

   **[!UICONTROL Max Value]** :最大授权进程数。

   **[!UICONTROL Warning]** :当进程数达到授权阈值的80%时，将显示此指示器。

   **[!UICONTROL Alert]** :当进程数达到授权阈值的90%时，将显示此指示器。

* **[!UICONTROL File Handles]** :有关文件描述符的信息，即每个进程打开的文件数。

   **[!UICONTROL Current value]** :当前文件描述符数。

   **[!UICONTROL Max Value]** :操作系统授权的文件描述符的最大数量。

   **[!UICONTROL Warning]** :当授权文件描述符的数量达到80%阈值时，将显示此指示符。

   **[!UICONTROL Alert]** :当授权文件描述符的数量达到90%阈值时，将显示此指示符。

* **[!UICONTROL Processes]** :有关机器进程的信息。

   **[!UICONTROL Current value]** :当前处于活动状态的进程数。

   **[!UICONTROL Max Value]** :最大授权进程数。

   **[!UICONTROL Active Processes]** :活动进程数。

   **[!UICONTROL Inactive Processes]** :非活动进程数。

   **[!UICONTROL Warning]** :当授权进程数达到80%阈值时，将显示此指示器。

   **[!UICONTROL Alert]** :当授权进程数达到90%阈值时，将显示此指示器。

* **[!UICONTROL Zombie Processes]** :已停止但仍具有进程标识符(PID)且在进程表中仍然可见的进程的相关信息。

   **[!UICONTROL Current value]** :当前处于活动状态的僵尸进程数。

   **[!UICONTROL Max Value]** :授权僵尸进程的最大数量(2)。

   **[!UICONTROL Warning]** :当僵尸进程数接近2时显示此指示器。

   **[!UICONTROL Alert]** 当僵尸进程数达到2时，将显示此指示器。

#### 自定义指示器{#customized-indicators}

Adobe Campaign允许您自定义指示器。 操作步骤：

1. 创建一个&#x200B;**.sh**&#x200B;文件并将其命名为&#x200B;**[!UICONTROL cust_indicators.sh]**。
1. 将自定义指示器添加到此文件。 例如：

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   或者

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. 将文件放在&#x200B;**[!UICONTROL usr/local/neolane/nl6]**&#x200B;文件夹中。

此文件将由Adobe Campaign调用。

## SMTP报告{#smtp-reports}

SMTP投放监视报表集成到Adobe Campaign平台中。 可以通过控制台或通过Web访问访问它们。

这些报告按域显示SMTP投放统计和SMTP错误。

要访问它们，运营商必须具有“管理”权限。

它们分组在&#x200B;**监视** > &#39;SMTP监视&#39;下。

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* 仅当激活了电子邮件渠道时，与SMTP监视相关的信息才可用。
>* **[!UICONTROL SMTP sending statistics]**&#x200B;仅在实例上启动统计信息服务器时提供。
>



### SMTP发送统计数据{#smtp-sending-statistics}

**[!UICONTROL SMTP sending statistics]**&#x200B;报表允许您控制服务器活动。 它显示每个匹配子的合成。

![](assets/smtp_stats_report.png)

图表下方显示了此报表的指标列表。

1. 已发送邮件的总数。
1. 
   * 蓝线：已准备好发送已到达Shaper的邮件，即发送SMTP之前的最后一阶段（与传入数据一致）。

   * 绿线：消息已成功发送（与传出数据一致）。

   * 红线：由Shaper放弃的消息，返回到&#x200B;**mta**（与此恢复中拒绝的数据一致）。

   这些值以每小时的消息数表示。

1. 表示Shaper的两个队列：

   * 蓝色曲线：活动消息的队列。 这些消息将尽快发送。

   * 卡基曲线：“延迟”队列。 由于限制或没有可用的目标连接，暂时无法返回这些消息。 重试每5秒、10秒、20秒、40秒、2分钟等进行一次。 在放弃之前，为定义的&#x200B;**MaxAgeSec**&#x200B;时间。

1. 此图表显示放弃消息的详细信息（第2个图表上的红色曲线）：与发送失败的消息（红色）相比，显示未重试消息(mauve)放弃的消息的比例。 这样，您就可以视图由于统计服务器的限制（限制）或由于远程服务器不可用而在授予的期限内未处理的邮件的比例。
1. 打开或正在打开SMTP连接。
1. **mtachild**&#x200B;的估计数。

>[!NOTE]
>
>此报表与电子邮件流量整形器组件的状态相关。

### 每个域的SMTP错误{#smtp-errors-per-domain}

此报表允许您视图按域划分的投放错误，在设定的时间段内。

>[!NOTE]
>
>**serverConf.xml**&#x200B;文件的&#x200B;**minConnectionsToLog**、**minErrorsToLog**&#x200B;和&#x200B;**minMessagesToLog**&#x200B;选项定义了将连接统计信息考虑到的阈值。

![](assets/smtp_error_report.png)

此报告的指标列表见表下。

* **域**&#x200B;列包含要向其发送消息的域的名称（例如，yahoo.fr的实际域名yahoo.com），
* **Cnx**&#x200B;列显示为此域打开的SMTP连接数，
* **Sent**&#x200B;列与发送到此域的消息数相对应，
* **Volume**&#x200B;列显示已尝试发送到此域的消息的卷（近似值），
* **Errors**&#x200B;列显示该域在该时间段内的错误的卷指示符，
* **最后响应**&#x200B;列显示收到的针对此域的最后一条SMTP响应消息，
* **Date**&#x200B;列显示该域上次收到的SMTP响应的日期。

>[!NOTE]
>
>根据在&#x200B;**[!UICONTROL Period]**&#x200B;字段中选择的周期，计算在&#x200B;**Cnx**、**Sent**&#x200B;和&#x200B;**Volume**&#x200B;列中显示的值。

单击某个域名以视图其错误。

它们按PublicId分类：此标识符对应于由路由器后面的多个Adobe Campaignmta共享的IP地址。 统计服务器使用该标识符来存储该起始点和投放服务器之间的连接和目标统计。

![](assets/smtp_error_report_details.png)

使用&#x200B;**[!UICONTROL Owner of domain]**&#x200B;字段，您可以在同一标签下对各种域名进行分组。 在初始报告视图中，所有MX域名都将与此所有者关联。

单击PublicId标识符可进一步视图详细信息。

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>错误百分比由两个图表表示。 第一个是黑色背景上的水平进度条。 第二张图表按时间顺序排列。 所选期间被分成十二个时间间隔，每个时间间隔由垂直进度条表示。 在这两个表示中，如果未检测到任何错误，则条为黑色。 条的颜色取决于遇到的错误百分比（黄色、橙色和最后红色）。 颜色灰色表示未找到任何重要的数据卷。 通过将光标放在图表上，可以显示错误的确切百分比。

>[!NOTE]
>
>有关SMTP错误以及在Adobe Campaign中管理它们的详细信息，请参阅[本节](../../installation/using/email-deliverability.md)。

## 帐单报表{#billing-report}

**[!UICONTROL Billing]**&#x200B;技术工作流通过电子邮件将系统活动报告发送给“billing”运营商。 默认为每月25日触发。

技术工作流位于以下节点的子文件夹中：**管理** > **生产** > **技术工作流**。

![](assets/billing.png)

每月25日启动该工作流后，您的账单操作员将在其收件箱中收到以下报表。

![](assets/billing_2.png)

可使用以下量度跟踪您的投放:

* **[!UICONTROL Start date]** :开始投放的日期。请注意，该日期可能早于报表的“开始”日期。
* **[!UICONTROL Label]** :投放的标签。要发送的消息少于100条的投放被认为太小，因此会按开始日期聚合，在这种情况下，标签会显示聚合的数量，例如[3个小投放的集合]。
* **[!UICONTROL Total volume]** :为投放传输的字节总量。
* **[!UICONTROL Avg volume]** :传输的字节的平均卷。这是以下公式&#x200B;**（总卷/消息）**&#x200B;的结果，它是&#x200B;**[!UICONTROL Multiplier]**&#x200B;量度的计算基础。
* **[!UICONTROL Messages]** :已发送消息的数量。这包括已成功发送的消息和重试（在收到联系服务器的弹回消息后）。
* **[!UICONTROL Multiplier (x)]** :从消息的平均体积推导出乘数的值。
* **[!UICONTROL Count]** :消息和乘数的乘法结果。

## 自动监视{#automatic-monitoring}

Adobe Campaign优惠了几种自动监控方法，如下所示。

### 命令行{#command-line}

命令

**nlserver监视器**

允许您列表Adobe Campaign模块和系统上的一组指示器。

它以易于处理的XML格式生成输出。

此命令还可以使用&#x200B;**-missing**&#x200B;参数运行，该参数将列表配置文件说应执行时此实例中缺少的进程。

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### 服务器发布的信息{#information-published-by-the-server}

#### /r/test {#r-test}

**http(s)://`<application>`/r/test**&#x200B;页用于测试重定向服务器。 我们建议使用相同的方法来测试用于跟踪的前端服务器。 此页还可用于测试负载调度程序。

它以XML格式显示如下行：

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**频率**:此测试不使用任何负载，因此可以经常运行（例如每秒运行一次）。

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

此&#x200B;**http(s)://`<Application server url>`/nl/jsp/ping.jsp**&#x200B;页面的操作方式与其网络对应页面相同：它测试一个完整的查询，它通过apache/tomcat/web module/database上传到客户端。 如果一切正常，则返回“OK”。 我们建议在可访问数据库(例如mta和调查)的计算机上运行此测试。

**用法**:要远程登录，必须将与操作员登录关联的会话令牌作为参数传递(请参阅通过Adobe Campaign脚本自 [动监视中的提示](#automatic-monitoring-via-adobe-campaign-scripts))。

例如：

![](assets/ncs_monitoring_ping.png)

操作员名称和登录名需要先前在Adobe Campaign客户端控制台中配置数据库权限。

![](assets/ncs_operators_rights_01.png)

**频率**:这是一个使用很少带宽的测试。因此，它可以相当频繁地运行，但每分钟不会多次。

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

这是一项测试，旨在检查操作员是否可以通过网页访问Adobe Campaign服务器；与通过客户端控制台菜单访问的网页相同。 您可以通过监视工具（Tivoli、Nagios等）调用此页面。

![](assets/ncs_monitoring_web.png)

**用法**:与操作符登录关联的会话令牌，它允许您连接到需要用作参数的实例(请参阅通过Adobe Campaign脚本自 [动监视中的提示](#automatic-monitoring-via-adobe-campaign-scripts))。

操作员及其登录名需要先在Adobe Campaign客户端控制台中配置相应的数据库权限和限制。

**频率**:这是一个完整的服务器测试，不需要经常运行（例如，可以每十分钟执行一次）。

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

此&#x200B;**jsp**&#x200B;表示Adobe Campaign应用程序API的入口点。 因此，它可以提供对应用程序的详细监控。 它还可用于监控Adobe Campaign Web服务。 它用于我们的监视脚本，但请注意，它仅供高级用户使用。

### 基于部署类型进行监视{#monitoring-based-on-deployment-types}

Adobe Campaign启用各种部署配置（有关详细信息，请参阅[本节](../../installation/using/hosting-models.md)）。 本部分根据您的安装类型，详细介绍要应用的各种自动监控技术。

<table> 
 <thead> 
  <tr> 
   <th> 部署类型 </th> 
   <th> 监控 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 独立 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand <span class="uicontrol">/nl/jsp/monitor.</span> jsponAdobe Campaign服务器</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 标准 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/ping.</span> jspon前沿服务器</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.</span> jspon应用程序服务器</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 企业 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/ping.</span> jspon前沿服务器</p> </li> 
     <li><p> <span class="uicontrol">/r/</span> testand <span class="uicontrol">/nl/jsp/monitor.</span> jspon应用服务器</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 中间源 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.</span> jspon应用程序服务器</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 通过Adobe Campaign脚本自动监视{#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign可以提供一个实例监视工具(netreport)，它允许您通过电子邮件发送有关检测到的异常的报告。

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>此工具可用于监视您的实例，但Adobe Campaign不支持。 有关详细信息，请与活动管理员联系。

### 所需元素{#required-elements}

自动监控需要以下安装前预防措施：

* 您必须具有&#x200B;**netreport.tgz**（Linux安装）或&#x200B;**netreport.zip**（Windows安装）文件，
* 我们强烈建议您不要在要监视的计算机上安装监视，
* 它必须安装在带有JRE或JDK的计算机上，
* 在Linux中，要监视的计算机必须具有&#x200B;**bc**&#x200B;包。 如需详细信息，请参阅[此部分](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages)。

### 安装过程{#installation-procedure}

安装过程如下：

1. 在控制台中，根据需要创建一个新运算符（“监视”用户已存在），但不分配任何权限。
1. 运行存档提取。
1. 阅读&#x200B;**readme**&#x200B;文件。
1. 更新&#x200B;**netconf.xml**&#x200B;配置文件。
1. 更新&#x200B;**netreport.bat**(Windows)或&#x200B;**netreport.sh**(Linux)文件。

### 配置netconf.xml文件{#configuring-the-netconf-xml-file}

XML配置文件包含以下元素：

* [“属性”元素](#properties--element)
* [“Instance”元素](#instance--element)
* [“Host”元素](#host--element)
* [子元素](#sub-elements)

以下是配置示例：

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>可以通过向&#x200B;**netconf.xml**&#x200B;文件添加后缀来指定各种配置，例如&#x200B;**netconf-dev.xml**、**netconf-prod.xml**&#x200B;等。 然后，通过添加&#x200B;**$JAVA_HOME/bin/java netreport dev**&#x200B;或&#x200B;**@%JAVA_HOME%binjava netreport&lt;a7，指定用于在** netreport.bat **或** netreport.sh **文件中执行netreport的配置/>。**

>[!IMPORTANT]
>
>要使&#x200B;**monitoring**&#x200B;运算符正常工作，执行Netreport的计算机必须位于处于&#x200B;**sessionTokenOnly**&#x200B;模式的安全区中。 如果尚未为此运算符指定可信的IP掩码，则安全区域还必须处于&#x200B;**allowEmptyPassword**&#x200B;和&#x200B;**allowUserPassword**&#x200B;模式。

#### “属性”元素{#properties--element}

此元素用于填充电子邮件的配置，即

* **mailServer**:用于发送电子邮件的SMTP服务器(例如：smtp.domain.net)。
* **mailFrom**:报表发送者的电子邮件地址(例如：monitoring@domain.net)。
* **recipientList**:列表监控收件人的电子邮件地址。地址必须用逗号分隔（无空格）。
* “**night**”模式（可选）用于避免在指定时间段之间发送电子邮件。 相反，数据会被整合，并在结束时间之后（默认为7:00）发送一封有关夜间活动的电子邮件。
* 使用&#x200B;**buildRange**&#x200B;子元素（可选）可以指定最小和最大内部版本号。 将为内部版本号未在此范围内的所有计算机生成错误

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* 可以在&#x200B;**properties**&#x200B;元素中添加&#x200B;**`<sla>`**（可选）子元素。 每次执行Netreport时都会生成日志文件。 文件的名称包含配置名称以及日期和时间，例如&#x200B;**dev_06_12_13_16_47_05.tmp**。 该文件包含以下信息：实例名称、计算机名称、严重性级别、（0到3，从最不严重到最严重）、日期（时间戳格式）、查询与响应之间经过的时间（以毫秒为单位）、使用的服务(http、ncs、ncsex、redir)。 在每项服务结束时，这些信息以表格标记和换行符分隔。

>[!NOTE]
>
>**`<property>`**&#x200B;元素上具有值“true”的&#x200B;**persistHtmlFile**&#x200B;属性用于在文件&#x200B;**netreport.md**&#x200B;中记录最新的监视状态。 此文件保存在安装目录中。

#### “Instance”元素{#instance--element}

通过此元素，您可以将多台计算机（主机）重新组合到同一实例中。 实例名称显示在监视电子邮件的第一部分中。 您可以单击实例的名称来访问有关每台计算机的详细信息。

```
instance name="instanceName" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **name**:将在电子邮件第一部分中显示的实例名称。
* **recipientList** （可选）：允许您通过电子邮件发送有关特定实例的监视报告。

#### “Host”元素{#host--element}

此元素配置主机上给定服务器的监视，即

* **name**:要监视的计算机的名称。
* **alias** （可选）：监视的计算机的名称，如同它将显示在报告中一样。
* **sessionToken**:通过授权会话令牌提供登录身份验证。

   要配置会话令牌，请在Adobe Campaign控制台中选择&#x200B;**monitoring**&#x200B;运算符。 在&#x200B;**访问权限**&#x200B;选项卡中，指定授权监视此实例的计算机的IP地址。 然后，您将能够使用&#x200B;**monitoring**&#x200B;标识符从这些计算机连接到监视页面，而无需指定密码。

   ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** （可选）：允许您按严重性级别对要显示的错误进行排序。可能的值为“0”（显示所有级别）、“1”（仅显示高错误和严重错误）和“2”（仅显示严重错误）。 如果未提供此属性，则显示所有错误级别。
* **filter** （可选）：允许您排除某些工作流错 **误，例如filter=&quot;wkf;wkf1&quot;**。工作流标签必须以分号分隔。

#### 子元素{#sub-elements}

* **tcp**:检查服务器是处于开启或关闭状态。必须输入端口号。
* **http**:检查Web服务器是否存在（应用程序服务器可运行）。
* **ncs**:检查在“instance”属性中输入的实例上的进程（工作流错误、内存使用情况等）。**includead**（必填）属性为您提供显示死进程（“true”或“false”值）的选项。
* **redir**:检查跟踪。

在大多数情况下，只能保留&#x200B;**ncs**&#x200B;和&#x200B;**redir**&#x200B;子元素。

在任何情况下，某些节点都可能在子元素中过载（例如，节点&#x200B;**port=75**&#x200B;以使用于http、ncs或redir连接的端口过载）：

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

在&#x200B;**ncs**、**redir**&#x200B;和&#x200B;**http**&#x200B;子元素中，可添加&#x200B;**isSecure**&#x200B;属性（可选）以选择是否使用https协议（“true”或“false”值）。 如果未提供此属性，则使用http协议。

### 配置netreport.bat或netreport.sh文件{#configuring-the-netreport-bat-or-netreport-sh--file}

要配置它，请编辑此文件并指示JRE或JDK安装在的目录。

### 正在启动监视{#launching-monitoring}

要启动监视，请通过脚本定期执行&#x200B;**netreport.bat**&#x200B;或&#x200B;**netreport.sh**&#x200B;文件。 在第一次执行后，仅在状态更改事件发送报告。

### 正在测试监视{#testing-monitoring}

要测试监视，请执行&#x200B;**netreport.bat**&#x200B;或&#x200B;**netreport.sh**&#x200B;文件。

将向&#x200B;**netconf.xml**&#x200B;文件的&#x200B;**recipientList**&#x200B;中指定的收件人发送电子邮件。
