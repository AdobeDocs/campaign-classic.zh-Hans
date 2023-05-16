---
product: campaign
title: 监控流程
description: 了解如何监控Campaign流程
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: 9ea7eea5a539407a17b0a11c942570cfa6c16f2f
workflow-type: tm+mt
source-wordcount: '3598'
ht-degree: 0%

---

# 监控流程{#monitoring-processes}


应用程序服务器和重定向服务器(**跟踪**)。

## 手动监控 {#manual-monitoring}

要访问Adobe Campaign进程监视页面，请浏览 **[!UICONTROL Monitoring]** ，然后单击 **[!UICONTROL Overview]** 链接。

![](assets/d_ncs_monitoring.png)

显示的页面允许您查看连接的实例的状态，即：

* 有关实例的信息：版本，名称，数据库引擎，已安装的包，服务器系统指示器，
* 缺少进程和执行信息（开始日期、PID等）的列表，
* 工作流和投放的视图。

有关监控Campaign流程的其他方法，请参阅 [本页](../../production/using/monitoring-guidelines.md).

### 日志日志 {#log-journal}

要显示与某个流程相关的日志日志，请单击该流程， **mta** 例如，选择 **[!UICONTROL Open the log journal]** .

![](assets/d_ncs_monitoring2.png)

### 系统指标 {#system-indicators}

浏览系统指示器列表，以显示有关计算机的信息，如其物理和虚拟内存、活动进程和可用磁盘空间。 Linux和Windows操作系统的指示器不同。 转到 **[!UICONTROL Instance Monitoring]** 页面，然后单击 **[!UICONTROL Display]** 链接以打开指标列表。

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]**:特定于 **消息中心**. [了解详情](../../message-center/using/additional-configurations.md#monitoring-thresholds)

* **[!UICONTROL Memory]**:有关物理内存(RAM)的信息。

   **[!UICONTROL Current value]**:当前内存消耗。

   **[!UICONTROL Max Value]**:安装的内存总量。

   **[!UICONTROL Available]**:可用内存量。

   **[!UICONTROL Warning]**:当内存消耗达到总量的80%时，将显示此指示器。

   **[!UICONTROL Alert]**:当内存消耗达到总量的90%时，将显示此指示器。

   当 **[!UICONTROL Warning]** 和 **[!UICONTROL Alert]** 显示指示器，您可以通过将RAM添加到安装了Adobe Campaign服务器的计算机来解决此问题。 您还可以决定在专用计算机上安装Adobe Campaign服务器。

* **[!UICONTROL Swap Memory]**:与与分页文件匹配的虚拟内存相关的信息：Windows使用的硬盘上的区域，如同RAM。

   **[!UICONTROL Current value]**:实际内存消耗。

   **[!UICONTROL Max Value]**:内存总量。

   **[!UICONTROL Available]**:可用内存量。

   **[!UICONTROL Warning]**:当内存消耗达到总量的80%时，将显示此指示器。

   **[!UICONTROL Alert]**:当内存消耗达到总量的90%时，将显示此指示器。

   当 **[!UICONTROL Warning]** 和 **[!UICONTROL Alert]** 显示指示器时，您可以通过在高级Windows设置中增加exchange文件的大小来解决此问题。

* **[!UICONTROL Disk XXX]**:有关机器读取器的信息。

   **[!UICONTROL Current value]**:实际使用的磁盘空间。

   **[!UICONTROL Max Value]**:磁盘总容量。

   **[!UICONTROL Available]**:可用磁盘空间。

   **[!UICONTROL Used]**:已用磁盘的百分比。

   **[!UICONTROL Warning]**:当可用磁盘空间达到总容量的80%时，将显示此指示器。

   **[!UICONTROL Alert]**:当可用磁盘空间达到总容量的90%时，将显示此指示器。

* **[!UICONTROL Number of processes too old]**:有关Adobe Campaign进程一天以上活动的信息。

   **[!UICONTROL Current value]**:当前活动的进程数。

   **[!UICONTROL Max Value]**:授权进程的最大数量(1)。

   **[!UICONTROL Alert]**:如果进程数等于1，则显示此指示器。

   当 **[!UICONTROL Alert]** 显示指示器时，可能是相关进程被SQL数据库引擎锁定，或者它陷入无限循环。 的 **监视** 由Adobe Campaign提供的流程每天自动重新启动所有流程，并使您能够解决此问题。 但是，您也可以自行停止相关流程以强制重新启动。

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]**:特定于 **消息中心**. 请参阅 [此部分](../../message-center/using/additional-configurations.md#monitoring-thresholds) 以了解更多信息。

* **[!UICONTROL Load average (1/5/15 minutes)]**:与负载有关的信息，即处理器在机器上运行的进程在最后一分钟、五分钟或十五分钟内的使用率

   **[!UICONTROL Current value]**:机器的实际负载。

   **[!UICONTROL Max value]**:计算机上进程的最大使用负载

   **[!UICONTROL Warning]**:当负载在最后一分钟、五分钟或十五分钟内达到最大授权值的80%时，会显示此指示器。

   **[!UICONTROL Alert]**:当负载达到最后一分钟、五分钟或十五分钟的最大授权值的90%时，将显示此指示器。

* **[!UICONTROL Memory]**  有关物理内存(RAM)的信息。

   **[!UICONTROL Current value]**:实际内存消耗。

   **[!UICONTROL Max Value]**:安装的内存总量。

   **[!UICONTROL Available]**:可用内存量。

   **[!UICONTROL Warning]**:当内存消耗达到总量的80%时，将显示此指示器。

   **[!UICONTROL Alert]**:当内存消耗达到总量的90%时，将显示此指示器。

   当 **[!UICONTROL Warning]** 和 **[!UICONTROL Alert]** 显示指示器，您可以通过将RAM添加到安装了Adobe Campaign服务器的计算机来解决此问题。 您还可以决定在专用计算机上安装Adobe Campaign服务器。

* **[!UICONTROL Swap Memory]**:与与分页文件匹配的虚拟内存相关的信息：Windows使用的硬盘上的区域，如同RAM。

   **[!UICONTROL Current value]**:实际内存消耗。

   **[!UICONTROL Max Value]**:内存总量。

   **[!UICONTROL Available]**:可用内存量。

   **[!UICONTROL Warning]**:当内存消耗达到总量的80%时，将显示此指示器。

   **[!UICONTROL Alert]**:当内存消耗达到总量的90%时，将显示此指示器。

   当 **[!UICONTROL Warning]** 和 **[!UICONTROL Alert]** 显示指示器时，您可以通过增加exchange文件的大小来解决问题。

* **[!UICONTROL Core Files]**:有关在Adobe Campaign进程崩溃后生成的文件的信息。 这些文件可让您诊断崩溃的原因。

   **[!UICONTROL Current Value]**:现有文件的数量。

   **[!UICONTROL Max Value]**:授权文件的最大数量(1)。

   **[!UICONTROL Warning]**:当文件数接近1时，将显示此指示器。

   **[!UICONTROL Alert]**:当文件数等于1时，将显示此指示器。

   当因崩溃而丢失进程时，该进程将在进程列表中以红色显示，并由 **监视** 流程由Adobe Campaign提供。

* **[!UICONTROL Number of shared memory segments]**:有关所有Adobe Campaign进程共享的内存段的信息。

   **[!UICONTROL Current value]**:当前正在使用的内存段数。

   **[!UICONTROL Max Value]**:已授权的最大内存段数(2)。

   **[!UICONTROL Warning]**:当内存段数量达到1时，将显示此指示器。

   **[!UICONTROL Alert]**:当内存段数量达到2时，将显示此指示器。

* **[!UICONTROL Number of processes too old]**:有关活动超过一天的进程的信息。

   **[!UICONTROL Current value]**:当前活动的进程数。

   **[!UICONTROL Max Value]**:授权进程的最大数量。

   **[!UICONTROL Warning]**:当进程数达到授权阈值的80%时，将显示此指示器。

   **[!UICONTROL Alert]**:当进程数达到授权阈值的90%时，将显示此指示器。

* **[!UICONTROL File Handles]**:有关文件描述符的信息，即每个进程打开的文件数。

   **[!UICONTROL Current value]**:文件描述符的当前数量。

   **[!UICONTROL Max Value]**:操作系统授权的文件描述符的最大数量。

   **[!UICONTROL Warning]**:当授权文件描述符的数量达到80%阈值时，将显示此指示符。

   **[!UICONTROL Alert]**:当授权文件描述符的数量达到90%阈值时，将显示此指示符。

* **[!UICONTROL Processes]**:有关机器进程的信息。

   **[!UICONTROL Current value]**:当前活动的进程数。

   **[!UICONTROL Max Value]**:授权进程的最大数量。

   **[!UICONTROL Active Processes]**:活动进程数。

   **[!UICONTROL Inactive Processes]**:不活动的进程数。

   **[!UICONTROL Warning]**:当授权进程数达到80%阈值时，将显示此指示器。

   **[!UICONTROL Alert]**:当授权进程数达到90%阈值时，将显示此指示器。

* **[!UICONTROL Zombie Processes]**:有关已停止但仍具有进程标识符(PID)且在进程表中仍可见的进程的信息。

   **[!UICONTROL Current value]**:当前处于活动状态的僵尸进程数。

   **[!UICONTROL Max Value]**:授权僵尸进程的最大数量(2)。

   **[!UICONTROL Warning]**:当僵尸进程数接近2时，将显示此指示器。

   **[!UICONTROL Alert]**:当僵尸进程数达到2时，将显示此指示器。

#### 自定义指示器 {#customized-indicators}

Adobe Campaign允许您自定义指标，如下所述：

1. 创建 **.sh** 文件和名称 **[!UICONTROL cust_indicators.sh]** .
1. 将您的自定义指示器添加到此文件。 例如：

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

1. 在 **[!UICONTROL usr/local/neolane/nl6]** 文件夹。

此文件由Adobe Campaign调用。

## SMTP报表 {#smtp-reports}

SMTP投放监控报表已集成到Adobe Campaign平台中。 可以通过控制台或使用Web访问来访问它们。

这些报表按域显示SMTP投放统计信息和SMTP错误。 要访问这些权限，运算符必须具有 **管理** 权限。

它们按 **监控** >“SMTP监视”。

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* 仅当激活了电子邮件渠道时，与SMTP监控相关的信息才可用。
>* 的 **[!UICONTROL SMTP sending statistics]** 仅当实例上启动统计信息服务器时才提供。
>


### SMTP发送统计信息 {#smtp-sending-statistics}

的 **[!UICONTROL SMTP sending statistics]** 报表允许您控制服务器活动。 它显示每个匹配项的合成。

![](assets/smtp_stats_report.png)

此报表的指标列表如图表下所示。

1. 发送的消息总数.
1. 表示输入/输出消息：

   * 蓝线：已准备好发送且已到达Shaper的消息，即发送SMTP之前的最后一步（与传入数据一致）。

   * 绿线：已成功发送消息（与传出数据一致）。

   * 红线：由Shaper丢弃的邮件，返回到 **mta** （与此恢复中拒绝的数据一致）。

   这些值以每小时消息数表示。

1. 表示Shaper的两个队列：

   * 蓝色曲线：活动消息的队列。 这些消息将尽快发送。

   * 卡基曲线：“延期”队列。 由于限制或目标连接不可用，当前无法返回这些消息。 重试次数为每5秒、10秒、20秒、40秒、2分钟等。 的 **MaxAgeSec** 才被放弃。

1. 下图显示了已放弃消息的详细信息（第2个图表上的红色曲线）：与发送失败（红色）的消息相比，它显示了未重试(mauve)而放弃的消息的比例。 这样，您就可以查看由于统计信息服务器的限制（限制）或由于远程服务器不可用而在授予的期限内未处理的邮件比例。
1. 打开或正在打开SMTP连接。
1. 估计的 **母乳**.

>[!NOTE]
>
>此报表与电子邮件流量整形器组件的状态相关。

### 每个域的SMTP错误 {#smtp-errors-per-domain}

此报表允许您查看在设定的时间段内按域划分的投放错误。

>[!NOTE]
>
>的 **minConnectionsToLog**, **minErrorsToLog** 和 **minMessagesToLog** 选项 **serverConf.xml** 文件定义要考虑连接统计信息的阈值。

![](assets/smtp_error_report.png)

本报告的指标清单见下表。

* 的 **域** 列包含消息被发送到的域名（例如，yahoo.com的实际域名），
* 的 **Cnx** 列显示此域打开的SMTP连接数，
* 的 **已发送** 列对应于发送到此域的消息数，
* 的 **卷** 列显示尝试发送到此域的消息量（近似值），
* 的 **错误** 列显示该域中该时段出现错误的卷指示器，
* 的 **上次响应** 列显示收到的该域的最后一个SMTP响应消息，
* 的 **日期** 列显示该域收到的上次SMTP响应的日期。

>[!NOTE]
>
>在 **Cnx**, **已发送**&#x200B;和 **卷** 列是根据 **[!UICONTROL Period]** 字段。

单击域名可查看其错误。

它们按PublicId进行分类：此标识符对应于路由器后面的多个Adobe Campaign mta共享的IP地址。 统计信息服务器使用此标识符来存储此起始点和目标服务器之间的连接和传递统计信息。

![](assets/smtp_error_report_details.png)

的 **[!UICONTROL Owner of domain]** 字段，您可以在同一标签下对各种域名进行分组。 在初始报表视图中，所有MX域名都将与此所有者关联。

单击PublicId标识符可查看更多详细信息。

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>错误百分比由两个图表表示。 第一个是黑色背景中的水平进度条。 第二张图表是按时间顺序排列的。 所选时段被划分为十二个时间间隔，每个时间间隔由垂直进度条表示。 在这两个表示中，如果未检测到任何错误，则条为黑色。 条的颜色取决于遇到的错误百分比（黄色、橙色、最后是红色）。 颜色灰色表示未找到任何显着数据量。 通过将光标放在图表上，可显示错误的确切百分比。

>[!NOTE]
>
>有关SMTP错误以及在Adobe Campaign中管理这些错误的详细信息，请查阅 [此部分](../../installation/using/email-deliverability.md).

## 计费报告 {#billing-report}

的 **[!UICONTROL Billing]** 技术工作流通过电子邮件将系统活动报告发送给“billing”操作员。 默认情况下，每月25日在营销实例上触发。

技术工作流可在以下节点的子文件夹中找到： **管理** > **生产** > **技术工作流**.

![](assets/billing.png)

工作流每月25日启动一次后，您的账单运营商将在其收件箱中收到以下报表。

![](assets/billing_2.png)

以下量度可用于跟踪投放：

* **[!UICONTROL Start date]** :投放的开始日期。 请注意，它可能早于报表的“开始”日期。
* **[!UICONTROL Label]** :投放的标签。 要发送的消息少于100个的投放被认为太小，因此会按开始日期聚合，在这种情况下，标签会显示聚合的数量，例如 [3个小型投放的聚合].
* **[!UICONTROL Total volume]** :传送的字节总量。
* **[!UICONTROL Avg volume]** :传输的平均字节数。 这是以下公式的结果 **（总卷/报文）**，这是 **[!UICONTROL Multiplier]** 量度。
* **[!UICONTROL Messages]** :已发送消息的数量。 这包括成功发送的消息和重试的消息（在从联系的服务器收到退回消息后）。
* **[!UICONTROL Multiplier (x)]** :从消息的平均体积推导乘数值。
* **[!UICONTROL Count]** :消息和乘数的乘法结果。

## 自动监控 {#automatic-monitoring}

Adobe Campaign提供了多种自动监控方法，如下所示。

### 命令行 {#command-line}

命令

**nlserver监视器**

允许您在Adobe Campaign模块和系统中列出一组指标。

它以易于处理的XML格式生成输出。

此命令还可以使用 **— 缺失** 参数，该参数列出了当配置文件表示应执行时此实例中缺少的进程。

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### 服务器发布的信息 {#information-published-by-the-server}

#### /r/test {#r-test}

的 **http(s)://`<application>`/r/test** 页面用于测试重定向服务器。 我们建议使用相同的方法来测试用于跟踪的前端服务器。 此页面还可用于测试加载调度程序。

它以XML格式显示如下行：

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**频率**:此测试不使用任何负载，因此可以经常运行（例如每秒运行一次）。

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

此 **http(s)://`<Application server url>`/nl/jsp/ping.jsp**  页面的操作方式与其网络对应方相同：它测试通过apache/tomcat/web模块/数据库的完整查询并上传到客户端。 如果一切正常，则返回“OK”。 我们建议在具有数据库访问权限的计算机上（例如，mta和调查）运行此测试。

**使用情况**:与操作员登录关联的会话令牌必须作为参数传递，才能远程登录（请参阅提示） [通过Adobe Campaign脚本自动监控](#automatic-monitoring-via-adobe-campaign-scripts))。

例如：

![](assets/ncs_monitoring_ping.png)

以前，需要在Adobe Campaign客户端控制台中为操作员名称和登录配置数据库权限。

![](assets/ncs_operators_rights_01.png)

**频率**:这是一个使用很少带宽的测试。 因此，它可以相当频繁地运行，但每分钟不会多次。

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

这是一项测试，用于检查操作员是否可以通过网页访问Adobe Campaign服务器；与通过客户端控制台菜单访问的网页相同。 您可以从监视工具（Tivoli、Nagios等）中调用此页。

![](assets/ncs_monitoring_web.png)

**使用情况**:与操作员登录关联的会话令牌，允许您连接到实例，该令牌需要用作参数(请参阅 [通过Adobe Campaign脚本自动监控](#automatic-monitoring-via-adobe-campaign-scripts))。

以前，需要在Adobe Campaign客户端控制台中为操作员及其登录配置适当的数据库权限和限制。

**频率**:这是一项完整的服务器测试，无需经常运行（例如，每10分钟可执行一次）。

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

此 **jsp** 表示Adobe Campaign应用程序API的入口点。 因此，它可以提供对应用程序的详细监控。 它还可用于监控Adobe Campaign Web服务。 它用在我们的监视脚本中，但请注意，它仅供高级用户使用。

### 基于部署类型进行监控 {#monitoring-based-on-deployment-types}

Adobe Campaign支持各种部署配置(有关更多信息，请参阅 [此部分](../../installation/using/hosting-models.md))。 本节详细介绍根据您的安装类型而应用的各种自动监控技术。

<table> 
 <thead> 
  <tr> 
   <th> 部署类型 </th> 
   <th> 监测 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 独立 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> 和 <span class="uicontrol">/nl/jsp/monitor.jsp</span> Adobe Campaign服务器上</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 标准 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> 和 <span class="uicontrol">/nl/jsp/ping.jsp</span> 前端服务器上</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> 应用程序服务器上</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 企业 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> 和 <span class="uicontrol">/nl/jsp/ping.jsp</span> 前端服务器上</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> 和 <span class="uicontrol">/nl/jsp/monitor.jsp</span> 应用程序服务器上</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 中间源 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> 应用程序服务器上</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 通过Adobe Campaign脚本自动监控 {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign可以提供实例监控工具(netreport)，让您通过电子邮件发送有关检测到的异常的报表。

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>此工具可用于监视实例，但Adobe Campaign不支持。 有关详细信息，请与Campaign管理员联系。

### 必需元素 {#required-elements}

自动监控需要以下安装前注意事项：

* 您必须拥有 **netreport.tgz** （Linux安装）或 **netreport.zip** （Windows安装）文件、
* 我们强烈建议您不要在要监视的计算机上安装监视，
* 它必须安装在带有JRE或JDK的计算机上，
* 在Linux中，要监视的计算机必须具有 **bc** 包。 如需详细信息，请参阅[此部分](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages)。

### 安装过程 {#installation-procedure}

安装步骤如下：

1. 在控制台中，根据需要创建新运算符（“监视”用户已存在），但不分配任何权限。
1. 运行存档提取。
1. 阅读 **readme** 文件。
1. 更新 **netconf.xml** 配置文件。
1. 更新 **netreport.bat** (Windows)或 **netreport.sh** (Linux)文件。

### 配置netconf.xml文件 {#configuring-the-netconf-xml-file}

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
>您可以通过向 **netconf.xml** 例如， **netconf-dev.xml**, **netconf-prod.xml**&#x200B;等。 然后，在中指定用于执行Netreport的配置 **netreport.bat** 或 **netreport.sh** 通过添加 **$JAVA_HOME/bin/java Netreport开发人员** 或 **@%JAVA_HOME%binjava netreport prod** 例如。

>[!IMPORTANT]
>
>对于 **监测** 要使用运算符，执行netreport的计算机必须位于 **sessionTokenOnly** 模式。 如果尚未为此运算符指定可信的IP掩码，则安全区域还必须位于 **allowEmptyPassword** 和 **allowUserPassword** 模式。

#### “属性”元素 {#properties--element}

此元素用于填充电子邮件的配置，即

* **mailServer**:用于发送电子邮件的SMTP服务器(例如：smtp.domain.net)。
* **mailFrom**:报表发送者的电子邮件地址(例如：monitoring@domain.net)。
* **recipientList**:监控收件人的电子邮件地址列表。 地址必须用逗号分隔（无空格）。
* &#39;**夜晚**“模式（可选）用于避免在指定时间段之间发送电子邮件。 相反，会合并数据，并在结束时间（默认为7:00）之后发送有关夜间活动的电子邮件。
* 的 **buildRange** 子元素（可选）允许您指定最小和最大内部版本号。 将为版本号未在此范围内的所有计算机生成错误

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* 您可以添加 **`<sla>`** （可选） **属性** 元素。 每次执行Netreport时都会生成日志文件。 文件名包含配置名称以及日期和时间，例如 **dev_06_12_13_16_47_05.tmp**. 文件包含以下信息：实例名称、计算机名称、严重性级别、（0到3，从最不重要到最关键）、日期（时间戳格式）、查询与响应之间经过的时间（以毫秒为单位）、使用的服务(http、ncs、ncsex、redir)。 此信息在每项服务结束时用表格标记和换行符分隔。

>[!NOTE]
>
>的 **persistHtmlFile** 值为“true”的 **`<property>`** 元素用于在文件中记录最新的监视状态 **netreport.md**. 此文件保存在安装目录中。

#### “Instance”元素 {#instance--element}

利用此元素，可将多台计算机（主机）重组到同一实例中。 实例名称显示在监视电子邮件的第一部分中。 您可以单击实例的名称以访问有关每台计算机的详细信息。

```
instance name="instance-name" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **name**:将在电子邮件第一部分中显示的实例名称。
* **recipientList** （可选）：允许您通过电子邮件发送有关特定实例的监控报告。

#### “Host”元素 {#host--element}

此元素配置主机上给定服务器的监控，即

* **name**:要监控的计算机的名称。
* **别名** （可选）：监视的计算机名称，该名称将显示在报表中。
* **sessionToken**:通过授权的会话令牌提供登录身份验证。

   要配置会话令牌，请选择 **监测** 运算符。 在 **访问权限** 选项卡，指定有权监视此实例的计算机的IP地址。 然后，您将能够使用 **监测** 标识符，而无需指定密码。

   ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** （可选）：允许您按严重性级别对要显示的错误进行排序。 可能的值为“0”（显示所有级别）、“1”（仅显示高错误和严重错误）和“2”（仅显示严重错误）。 如果未提供此属性，则会显示所有错误级别。
* **过滤器** （可选）：例如， **filter=&quot;wkf;wkf1&quot;**. 工作流标签必须以分号分隔。

#### 子元素 {#sub-elements}

* **tcp**:检查服务器是处于开启状态还是关闭状态。 必须输入端口号。
* **http**:检查Web服务器是否存在（应用程序服务器可运行）。
* **ncs**:检查在“实例”属性中输入的实例上的进程（工作流错误、内存使用情况等）。 的 **包含** （必需）属性允许您选择显示无效进程（“true”或“false”值）。
* **redir**:检查跟踪。

在大多数情况下，仅 **ncs** 和 **redir** 子元素可以保留。

在任何情况下，某些节点都可以在子元素（例如，节点）中重载 **port=75** 要使用于http、ncs或redir连接的端口过载，请执行以下操作：

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

在 **ncs**, **redir** 和 **http** 子元素中，您可以在 **isSecure** 属性（可选）来选择是否使用https协议（“true”或“false”值）。 如果未提供此属性，则使用http协议。

### 配置netreport.bat或netreport.sh文件 {#configuring-the-netreport-bat-or-netreport-sh--file}

要配置它，请编辑此文件并指示JRE或JDK安装在哪个目录中。

### 启动监控 {#launching-monitoring}

要启动监控，请执行 **netreport.bat** 或 **netreport.sh** 文件（通过脚本定期发送）。 报表在首次执行后发送，然后仅在状态发生更改时发送。

### 测试监控 {#testing-monitoring}

要测试监控，请执行 **netreport.bat** 或 **netreport.sh** 文件。

系统会向 **recipientList** 的 **netconf.xml** 文件。
