---
solution: Campaign Classic
product: campaign
title: 版本 18.10
description: 版本 18.10
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2366'
ht-degree: 7%

---


# 版本 18.10{#release-18-10}

## 版本 18.10.6 - 版本 8985{#release-18-10-6-build-8985}

2019年7月12日

**改进**

* 现在，我们允许在导入工作流程期间删除在Microsoft Dynamics中创建的虚拟记录。
* 修复了文件收集器工作流活动的一个问题，该问题可能导致在拒绝访问文件时在循环中记录错误。 (NEO-12085)
* 修复了导致用户报告与打开的投放指示器的跟踪报告之间出现活动差异的问题。 (NEO-11742)
* 改进了使用内部帐户时执行安全区包的权限。
* 修复了在匹配域日志中可能导致错误的问题。 (NEO-8978)

## 版本 18.10.5 - 版本 8984{#release-18-10-5-build-8984}

2019年4月23日

**改进**

* 修复了SQL死锁问题，该问题导致投放分析在同步分析/发送(同时分析两个投放时)时失败。 (NEO-13026)
* 已删除工作流热图中的10,000记录限制，以修复缺少的数据问题。 (NEO-12329)
* 修复了在扩充工作流活动中使用“从主集保留所有其他数据”选项时的问题。 (NEO-13291)

## 版本 18.10.4 - 版本 8983{#release-18-10-4-build-8983}

2019年4月15日

**改进**

* 修复了事务消息跟踪指示器的计算过程的问题。 (NEO-12529, NEO-12581)
* 修复了HTTPRequest API的一个问题，该问题未等待所有回调完成。 (NEO-12628)
* 在优惠券临时表中添加了索引以优化投放发送。 (NEO-12437)
* 修复了分析消息时瞄准日语(.JP)域的收件人的问题。 (NEO-12246)
* 在Analytics集成中，现在允许检索包含%字符的AAM区段数据。 (NEO-12025)
* 修复了使用HTTP2发送推送通知时的Tomcat崩溃问题。 (NEO-12701)

## 版本 18.10.3 - 版本 8981{#release-18-10-3-build-8981}

2019年1月29日

>[!CAUTION]
>
>这栋建筑已被收回。 请升 [级到最新版本](../../production/using/build-upgrade.md) ，或与 [Adobe客户服务联系](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**改进**

* 修复了s3文件传输工作流活动的问题。 (NEO-12473)
* 修复了跟踪工作流可能失败的问题。 (NEO-12520)
* 修复了IMS登录的问题。
* 修复了使用大预览ID时事务消息传递中的优惠和内容审批问题。
* 修复了中间源(投放计数器)工作流的问题。
* 修复了数据库结构更新的问题，该问题导致NmsRecipient上丢弃新索引。
* 修复了在投放的主目标使用外部文件中的定义选项时可能发生的控制台崩溃。 (NEO-12349)
* 修复了多个InMail崩溃。
* 修复了使用“更新”数据工作流活动删除联合数据访问Teradata数据库中存储的记录时的问题。
* 修复了密钥管理中的不一致问题。
* 修复了将字段键入为时的扩充活动问题：xml=true并且calculated=true
* 修复了在移动应用程序上发送推送通知时的字符转义问题。
* 修复了在联合数据访问外部帐户中阻止从中间源切换到SOAP同步方法的问题。

## 版本 18.10.2 - 版本 8978{#release-18-10-2-build-8978}

2018年12月6日

>[!CAUTION]
>
>这栋建筑已被收回。 请升 [级到最新版本](../../production/using/build-upgrade.md) ，或与 [Adobe客户服务联系](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**改进**

* 修复了在工作流上使用MySQL运行联合数据访问时的各种问题。 (NEO-11652)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了在投放中使用种子地址时ID耗尽的问题。 (NEO-11842)
* 修复了使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了在1:N链接中使用值分布时的显示问题。 (NEO-11820)
* 修复了Worflow热图中的Oracle错误。
* 修复了在优惠建议活动中添加扩充时的正确问题。
* 修复了SQL数据管理连接问题。
* 修复了负ID情况下生成临时工作流表名称的问题。
* 修复了工作流热图中工作流持续时间的计算问题。


## 版本 18.10 - 版本 8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>这栋建筑已被收回。 请升 [级到最新版本](../../production/using/build-upgrade.md) ，或与 [Adobe客户服务联系](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 说明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Push notification improvements<br /> </td> 
   <td> 在Adobe Campaign中已对推送通知实施了多项增强：<br /> 
    <ul> 
     <li> <p>在iOS中跟踪静默通知 </p> </li> 
     <li> <p>在iOS中实施注册呼叫反馈</p> </li> 
     <li> <p>提高iOS投放准备速度</p> </li> 
    </ul> <p>作为Google GCM折旧的一部分，Android V2连接器现在仅允许与FCM服务器连接。</p><p>有关详细信息，请参阅<a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">详细文档</a>。本文详细介绍了FCM的手 <a href="https://helpx.adobe.com/cn/campaign/kb/migrate-to-fcm.html">动升级</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td> SQL数据管理活动<br /> </td> 
   <td> <p>已添加新的数据管理工作流活动。 使用 <strong>SQL数据管理</strong> 活动，您可以编写或复制粘贴自己的SQL脚本，以创建和填充工作表(仅联合数据访问)。 </p> <p>有关详细信息，请参阅<a href="../../workflow/using/sql-data-management.md">详细文档</a>。</p></td> 
  </tr> 
  <tr> 
   <td> 工作流监视<br /> </td> 
   <td> <p>借助新的Adobe Campaign工作流热图，平台管理员可以快速以图形形式呈现所有并发工作流，这使他们能够监控实例的负载并相应地规划工作流。</p> <p>有关详细信息，请参阅<a href="../../workflow/using/heatmap.md">详细文档</a>。</p> <p>Workflow HeatMap软件包也可根据需要在8977之前（从8700开始）进行构建。 有关请求和安装它的详细信息，请参 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">阅本页</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 修复了一个安全问题，该问题可能导致服务器端请求伪造(SSRF)攻击和拒绝服务(DoS)攻击的漏洞。 (NEO-11453)
* 内容(跟踪重定向、镜像页面、调查等) 现在将由X-Robots-Tag的活动提供：无缓存头。 这可防止通过Internet搜索引擎对此内容进行索引。 (NEO-11101)
* 修复了订阅API(nms:订阅：取消订阅和nms:订阅：订阅)中的XTK注入问题。
* 修复了退订Web应用程序中的XTK注入问题。
* 删除了某些SMS日志中不安全显示的密码。

**改进**

* Campaign Classic API 现在可在[专用页面](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)中使用。如果您使用的是 jsapi.chm 文件，您现在应该参阅新的在线版本。
* 现在支持PostgreSQL 10、Debian 9和Teradata16.20。 请参阅[兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)。
* 创建SFTP连接时，您现在可以使用代理身份验证。 For more information, refer to the [detailed documentation](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration) (NEO-9868)
* 使 **用直邮投放** 创建单个投放时，投放模板属性中现在提供“日期计算公式”选项。 (NEO-9792)
* 对cookie跟踪和Web应用程序的域名管理进行了改进。 有关详细信息，请参阅下面的“技术演变”部分。
* Adobe Marketing Cloud在投放或登陆页共用资产的进口在安全性和性能方面都得到改进。
* 移动渠道外部帐户中有一个新的复选框，用于在日志文件中启用详细的SMPP跟踪，这使得可以从Adobe Campaign界面直接访问该输出。
* 在广播中，现在区别于每小时的最大连接数和最大消息数。 当达到这些限制时，就可以知道为什么吞吐量受到限制。 以前，同一消息（“配额已满”）适用于两种情况。
* 您现在可以指定在从池获取连接时执行的SQL脚本。 此脚本可用于设置默认模式。 此脚本将在查询条带后应用。 (NEO-11256)
* 活动SDK不再存储用户ID以符合我们的PII规定。 数据现在以哈希存储。
* 在导入包导出XML文件时，活动现在支持文件中存在BOM，即使在文件中明确声明了编码也是如此。

**技术演进**

客户端和服务器升级

>[!CAUTION]
>
>如果您的服务器已更新为18.10，则必须使用18.10客户端才能访问您的服务器。 18.10客户端将能够连接到旧版服务器。

域名管理

对cookie跟踪和Web应用程序的域名管理进行了改进。

现在，默认支持所有双字母二级域名（例如。aa.com）。 对于更复杂的域名（例如，三个字母的二级域，如。com.au），您需要将它们添加到serverConf的 **cookieDomains** 选项中（在重定向标记下）。 以下是一个示例：

```
<redirection cookiedomain="http://toureiffel.paris">
```

索引增强功能

NmsRecipient上的索引已重新工作。 这应会提高使用此表的查询的性能。 如果已扩展NmsRecipient，则可能需要验证是否没有重复新索引的索引（以最大限度地减少数据库服务器上的空间使用）。 (NEO-8228)

在PostgreSql上，当使用UTF-8归类时，现在可以创建索引，以优化“LIKE &#39;string%&#39;”(或“开始与”)操作。 如果对同一列执行其他操作（例如，按顺序或连接），则需要另一个标准索引。 在模式端，将通过在索引定义上添加indexOption=&quot;searchFromStart&quot;来完成此操作（它将创建varchar_pattern_ops索引，而不是标准btree索引）。 例如（在NmsRecipient上）:

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

新索引已添加到NmsRtEvent和NmsEventHisto（在“计划”列上），这应会缩短相应表单上的显示时间(NEO-11738)。

这些索引更改可能导致执行升级后所需的时间增加。

**修补程序**

* 修复了阻止下载Web下载工作 **流活动** 中的文件的错误。 (NEO-11105)
* 修复了偶尔将“发送指示 **器”和“活动属性** ”工作流保留为“失败”状态的错误(NEO-10820)。
* 修复了删除在工作流中运行收件人更新列表后创建的列表活动的问题。 (NEO-11696)
* 修复了在活动日历（日语实例）中提前一个月错误显示活动的问题。 (NEO-11445)
* 修复了导致Analytics配置无法显示在投放属性的“Web分析”选项卡中的问题。 (NEO-11619)
* 修复了尝试编辑和保存nms:投放输入表单时显示的错误。 (NEO-10973)
* 修复了运行包含文件传输外部帐户的工作流时发生的活动配置问题。 (NEO-11012)
* 修复了在数据加载活动中使用zcat函数加载文件时返回空行的问题。 (NEO-11273)
* 修复了在分析投放期间生成重复的广泛日志的问题。 (NEO-11360)
* 修复了在工作流中执行投放活动后，由于缺少外联链接密钥而导致扩充失败的问题。 (NEO-11537)
* 修复了安装路径包含特定GB18030汉字时，无法正确卸载或修复Adobe Campaign的问题。
* 修复了将某些跟踪日志链接到错误投放的问题。 (NEO-11412)
* 修复了可能导致某些投放日志部分的挂起状态保留时间长于预期的问题。 (NEO-11336)
* 修复了编辑查询以向投放添加优惠券时发生的错误。 (NEO-11037)
* 修复了报告中的一个问题，该问题导致无论选择哪个聚集运算符，图表都始终计算值的总和。 (NEO-10913)
* 由于“request.scheme”函数已弃用，因此已从JSAPI文档中删除它。 (NEO-10828)
* 修复了阻止某些具有特定时区配置的用户登录Adobe Campaign的问题。 (NEO-10712)
* 修复了使用扩展通用SMPP连接器设置移动渠道外部帐户时发生的问题：如果为接收器指定了不同的参数，则发送器将错误地使用这些参数而不是自己的参数。
* 修复了在为压力规则设置频率时导致计划投放失败的问题，因为在第一次仲裁后，投放会不断重新计算。 (NEO-10016)
* 修复了在应用程序池循环过程（在nlsrvmod.dll库中）期间导致IIS Web服务器崩溃的问题。 (NEO-10862)
* 修复了一个问题，该问题可能会阻止在收件人和 **目标屏幕中搜** 索用户档案。 (NEO-8228)
* 修复了在记录数量较多的情况下访问事件历史记录文件夹时可能导致超时错误的问题。 (NEO-11738)
* 修复了可能导致LINE投放收件人错误地返回为“不可到达”的问题。 (NEO-10833)
* 修复了在Oracle上用附加列执行工作流查询时的问题。 (NEO-11615)
* 已进行了增强，以确保关闭的连接不会在连接池中保留太长时间。 (NEO-11392)
* 修复了使用定位工作流活动(查询、数据加载(RDBMS)等)时的问题 通过联合数据访问连接到包含UTF8字符（在表名、字段名称等中）的外部Oracle表。 还包含一个主键约束，该约束具有系统生成的缺省约束名称。 (NEO-10714)
* 修复了可能无法删除投放的HTML内容的问题。 (NEO-11327)
* 修复了在运行预览后，直接邮件中XML和CSV文件的活动问题。 (NEO-11290)
* 修复了在扩充工作流活动中对数据排序时的问题。 (NEO-11394)
* 修复了在自定义报告中对数据排序时的问题。 (NEO-10896)
* 修复了在将useVault设置与Teradata一起使用时导致错误的问题。 (NEO-11399)
* 修复了在删除多个Adobe Campaign行时导致查询客户端控制台崩溃的问题。 (NEO-10744)
* 修复了在传送直接邮件时在某些情况下无法应用压力规则的问题。 (NEO-9004)
* 修复了使用数据加载活动导入数据类型为“time”的列时发生的问题：即使删除时间分隔符后，也会重置时间分隔符。 (NEO-10743)
* 修复了在编辑循环投放时，投放文件夹无法从投放属性的执行文件夹列表中显示的问题。 (NEO-11094)
* 修复了导致视图填充窗口无法在工作流中显示200个以上记录作为查询活动的结果目标的问题。 (NEO-11195)
* 修复了Oracle的一个问题，该问题导致在选择1000个以上元素时无法执行DELETE查询。 (NEO-11171)
* 修复了导致在Android推送通知投放的其他参数中将URL编码为跟踪URL的问题。 (NEO-11468)
* 修复了将参数设置为“一天间隔”和“打开”时“用户活动”报告中出现的脚本错误。 (NEO-11655)
* 修复了通过已验证的Web代理连接到中间源服务器或消息中心时发生的问题。 (NEO-11309)
* 修复了在基于SQL视图选择特定模式的元素后保存新投放组合时 **发生的Oracle错误**。 (NEO-11682)
* 修复了在使用解压缩选项通过加载文件活动处理包含。csv的zip文件时，导致生成包含误报的拒绝文件的问题。
* xtkjoblog现在由清除清除。

