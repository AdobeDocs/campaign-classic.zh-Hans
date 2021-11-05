---
product: campaign
title: Campaign 18.10发行说明
description: Campaign 18.10发行说明
feature: Overview
role: User
level: Beginner
exl-id: 57996f77-4ac2-402a-95db-b75d4bea4eeb
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '2369'
ht-degree: 7%

---

# 18.10 版{#release-18-10}

![](../../assets/v7-only.svg)

## 18.10.6 版 - 版本 8985{#release-18-10-6-build-8985}

2019年7月12日

**改进**

* 现在，允许在导入工作流期间删除在Microsoft Dynamics中创建的虚拟记录。
* 修复了文件收集器工作流活动的问题，该问题在拒绝访问文件时可能会循环记录错误。 (NEO-12085)
* 修复了导致用户活动与打开投放指示器的跟踪报表之间存在报表差异的问题。 (NEO-11742)
* 改进了在使用内部帐户时执行安全区域包的权限。
* 修复了可能导致匹配字段日志中出现错误的问题。 (NEO-8978)

## 18.10.5 版 - 版本 8984{#release-18-10-5-build-8984}

2019年4月23日

**改进**

* 修复了SQL死锁的问题，该问题在同时分析/发送（同时分析两个投放）的情况下导致投放分析失败。 (NEO-13026)
* 删除了工作流热图中的10,000条记录限制，以修复缺失的数据问题。 (NEO-12329)
* 修复了在扩充工作流活动中使用“从主集中保留所有其他数据”选项时的问题。 (NEO-13291)

## 18.10.4 版 - 版本 8983{#release-18-10-4-build-8983}

2019年4月15日

**改进**

* 修复了事务型消息的跟踪指标的计算过程中存在的问题。 (NEO-12529, NEO-12581)
* 修复了HTTPRequest API未等待所有回调完成的问题。 (NEO-12628)
* 在优惠券临时表中添加了索引，以优化投放发送。 (NEO-12437)
* 修复了分析日语(.JP)域的目标收件人的消息时的问题。 (NEO-12246)
* 在Analytics集成中，现在允许检索包含%字符的AAM区段数据。 (NEO-12025)
* 修复了使用HTTP2发送推送通知时的Tomcat崩溃问题。 (NEO-12701)

## 18.10.3 版 - 版本 8981{#release-18-10-3-build-8981}

2019年1月29日

>[!CAUTION]
>
>这栋建筑已被召回。 请 [升级到最新内部版本](../../production/using/build-upgrade.md)  或联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**改进**

* 修复了s3文件传输工作流活动的问题。 (NEO-12473)
* 修复了跟踪工作流可能失败的问题。 (NEO-12520)
* 修复了IMS登录问题。
* 修复了使用大型选件ID时事务性消息传递中的预览和内容批准问题。
* 修复了中间源（投放计数器）工作流的问题。
* 修复了数据库结构更新中丢弃NmsRecipient上新索引的问题。
* 修复了在外部文件中为投放主要目标使用定义选项时可能发生的控制台崩溃。 (NEO-12349)
* 修复了InMail的几次崩溃。
* 修复了使用更新数据工作流活动删除FDATeradata数据库中存储的记录时的问题。
* 修复了密钥管理中的不一致问题。
* 修复了在键入字段为时扩充活动的问题：xml=true， calculated=true
* 修复了在移动应用程序上发送推送通知时的字符转义问题。
* 修复了中间源外部帐户中无法从FDA切换到SOAP同步方法的问题。

## 18.10.2 版 - 版本 8978{#release-18-10-2-build-8978}

2018年12月6日

>[!CAUTION]
>
>这栋建筑已被召回。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**改进**

* 修复了在FDA上使用MySQL运行工作流时的各种问题。 (NEO-11652)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了在投放中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了在使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了在1:N链接中使用值分布时的显示问题。 (NEO-11820)
* 修复了工作流热图中的Oracle错误。
* 修复了在扩充活动中添加优惠建议时的正确问题。
* 修复了SQL数据管理连接问题。
* 修复了在ID为负时生成临时工作流表名称的问题。
* 修复了工作流热图中计算工作流持续时间的问题。


## 18.10 版 - 版本 8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>这栋建筑已被召回。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> 推送通知改进<br /> </td> 
   <td> 在Adobe Campaign中为推送通知实施了多项增强功能：<br /> 
    <ul> 
     <li> <p>在iOS中跟踪静默通知 </p> </li> 
     <li> <p>在iOS中实施有关注册调用的反馈</p> </li> 
     <li> <p>提高iOS交付准备速度</p> </li> 
    </ul> <p>作为遭Google弃用的GCM的一部分，Android V2连接器现在只能连接到FCM服务器。</p><p>有关详细信息，请参阅<a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">有详细说明的文档</a>。本文详细介绍了向FCM升级的手动 <a href="https://helpx.adobe.com/cn/campaign/kb/migrate-to-fcm.html">文章</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> SQL数据管理活动<br /> </td> 
   <td> <p>添加了新的数据管理工作流活动。 的 <strong>SQL数据管理</strong> 活动允许您编写或复制粘贴您自己的SQL脚本，以创建和填充工作表（仅限FDA）。 </p> <p>有关详细信息，请参阅<a href="../../workflow/using/sql-data-management.md">有详细说明的文档</a>。</p></td> 
  </tr> 
  <tr> 
   <td> 工作流监测<br /> </td> 
   <td> <p>借助新的Adobe Campaign Workflow HeatMap，平台管理员能够快速以图形形式表示所有并发工作流，从而监控实例的负载并相应地规划工作流。</p> <p>有关详细信息，请参阅<a href="../../workflow/using/heatmap.md">有详细说明的文档</a>。</p> <p>对于8977之前的版本（从8700开始），也可以根据需要使用Workflow HeatMap包。 有关请求和安装它的更多信息，请参阅 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">本页</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 修复了可能导致服务器端请求伪造(SSRF)攻击和拒绝服务(DoS)攻击漏洞的安全问题。 (NEO-11453)
* 内容（跟踪重定向、镜像页面、调查等） 现在，Campaign将使用X-Robots-Tag提供：无缓存标头。 这会阻止通过Internet搜索引擎索引此内容。 (NEO-11101)
* 修复了订阅API(nms)中的XTK注入问题:subscription:取消订阅和nms:subscription:订阅)。
* 修复了退订Web应用程序中的XTK注入问题。
* 删除了某些短信日志中不安全显示的密码。

**改进**

* Campaign Classic API 现在可在[专用页面](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)中使用。如果您使用的是 jsapi.chm 文件，您现在应该参阅新的在线版本。
* 现在支持PostgreSQL 10、Debian 9和Teradata16.20。 请参阅[兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)。
* 现在，在创建SFTP连接时，您可以使用代理身份验证。 有关更多信息，请参阅 [详细文档](../../installation/using/file-res-management.md) (NEO-9868)
* 的 **日期计算公式** 现在，使用直邮投放模板创建单个投放时，投放属性中的选项可用。 (NEO-9792)
* 对Cookie跟踪和Web应用程序的域名管理进行了改进。 有关更多信息，请参阅下面的“技术演变”部分。
* 在安全性和性能方面，已改进Adobe Marketing Cloud在投放或登陆页面中共享资产的导入。
* 移动渠道外部帐户中新增了一个复选框，用于在日志文件中启用详细的SMPP跟踪，以便从Adobe Campaign界面直接访问此输出。
* 在广播日志中，每小时的最大连接数和最大消息数之间存在区别。 当达到限制时，就可以知道为什么吞吐量有限。 以前，同一消息（“满足配额”）适用于这两种情况。
* 现在，您可以指定在从池获取连接时要执行的SQL脚本。 此脚本可用于设置默认架构。 此脚本将在查询分段后应用。 (NEO-11256)
* Campaign SDK不再存储用户ID以遵守PII法规。 数据现在以哈希形式存储。
* 现在，在导入资源包导出XML文件时，即使在文件中明确声明了编码，Campaign仍支持文件中存在物料清单。

**技术演进**

客户端和服务器升级

>[!CAUTION]
>
>如果您的服务器已更新为18.10，则必须使用18.10客户端才能访问您的服务器。 18.10客户端将能够连接到旧版服务器。

域名管理

对Cookie跟踪和Web应用程序的域名管理进行了改进。

现在，默认支持所有双字母二级域名（例如.aa.com）。 对于更复杂的域名（例如，三个字母的二级域，如.com.au），您需要将它们添加到 **cookieDomains** 选项serverConf（位于重定向标记下）。 示例如下：

```
<redirection cookiedomain="http://toureiffel.paris">
```

索引增强功能

NmsRecipient上的索引已重新工作。 这应会提高使用此表的查询的性能。 如果已扩展了NmsRecipient，则可能需要验证是否没有与新索引重复的索引（以最大限度地减少数据库服务器上的空间使用）。 (NEO-8228)

在使用UTF-8归类时，在PostgreSql上，现在可以创建索引，以优化“LIKE &#39;string%&#39;”（或“开头为”）操作。 如果对同一列执行其他操作（例如按顺序或联接），则需要另一个标准索引。 在架构端，将通过在索引定义中添加indexOption=&quot;searchFromStart&quot;来完成此操作（它将创建varchar_pattern_ops索引，而不是标准树索引）。 例如（在NmsRecipient上）：

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

新索引已添加到NmsRtEvent和NmsEventHisto（在“已计划”列上），这应会缩短相应表单的显示时间(NEO-11738)。

这些索引更改可能会增加执行升级后所需的时间。

**补丁程序**

* 修复了阻止 **Web下载** 工作流活动。 (NEO-11105)
* 修复了有时会在 **发送指标和营销活动属性** 工作流处于失败状态(NEO-10820)。
* 修复了删除在工作流中运行列表更新活动后创建的收件人列表的问题。 (NEO-11696)
* 修复了在促销活动日历（日语实例）中提前一个月错误地显示促销活动的问题。 (NEO-11445)
* 修复了导致Analytics配置无法在投放属性的Web分析选项卡中显示的问题。 (NEO-11619)
* 修复了在尝试编辑和保存nms:delivery输入表单时显示的错误。 (NEO-10973)
* 修复了运行包含文件传输活动的工作流时发生的外部帐户配置问题。 (NEO-11012)
* 修复了使用zcat函数加载数据加载活动中的文件时返回空行的问题。 (NEO-11273)
* 修复了在分析投放期间生成重复的广泛日志的问题。 (NEO-11360)
* 修复了在工作流中执行扩充活动后，由于缺少外联键而导致投放失败的问题。 (NEO-11537)
* 修复了安装路径包含特定的GB18030中文字符时，无法正确卸载或修复Adobe Campaign的问题。
* 修复了将某些跟踪日志链接到错误投放的问题。 (NEO-11412)
* 修复了可能导致投放日志的某些部分保持挂起状态的时间超过预期时间的问题。 (NEO-11336)
* 修复了在编辑查询以向投放添加优惠券时发生的错误。 (NEO-11037)
* 修复了报表中的问题，即无论选择哪个聚合运算符，图表都会始终计算值的总和。 (NEO-10913)
* 由于“request.scheme”函数已被弃用，因此已从JSAPI文档中删除该函数。 (NEO-10828)
* 修复了某些具有特定时区配置的用户无法登录Adobe Campaign的问题。 (NEO-10712)
* 修复了使用扩展通用SMPP连接器设置移动渠道外部帐户时发生的问题：如果您为接收机指定了不同的参数，则发射机将错误地使用这些参数而不是自己的参数。
* 修复了在为压力规则设置频率时导致计划投放失败的问题，因为在首次仲裁后会不断重新计算投放。 (NEO-10016)
* 修复了在应用程序池回收过程（在nlsrvmod.dll库中）期间导致IIS Web服务器崩溃的问题。 (NEO-10862)
* 修复了可能阻止在 **配置文件和Target** 屏幕。 (NEO-8228)
* 修复了在记录数较多的情况下访问事件历史记录文件夹时可能导致超时错误的问题。 (NEO-11738)
* 修复了可能导致LINE投放收件人错误地返回为“不可到达”的问题。 (NEO-10833)
* 修复了在执行工作流查询时对Oracle添加附加列的问题。 (NEO-11615)
* 已进行增强，以确保连接池中不会保留已关闭的连接太长。 (NEO-11392)
* 修复了使用定向工作流活动(查询、数据加载(RDBMS)等)时的问题 通过FDA连接到包含UTF8字符（在表名、字段名称等中）的外部Oracle表 还包含具有系统生成的缺省约束名称的主键约束。 (NEO-10714)
* 修复了可能阻止删除投放HTML内容的问题。 (NEO-11327)
* 修复了运行营销活动后在直邮中预览XML和CSV文件时出现的问题。 (NEO-11290)
* 修复了扩充工作流活动中对数据进行排序时的问题。 (NEO-11394)
* 修复了在自定义报表中对数据进行排序时的问题。 (NEO-10896)
* 修复了在将useVault设置与Teradata结合使用时导致错误的问题。 (NEO-11399)
* 修复了在删除多个查询行时导致Adobe Campaign客户端控制台崩溃的问题。 (NEO-10744)
* 修复了在发送直邮时在某些情况下无法应用压力规则的问题。 (NEO-9004)
* 修复了使用数据加载活动导入数据类型为“time”的列时出现的问题：时间分隔符即使在删除后也会重置。 (NEO-10743)
* 修复了在编辑定期投放时，投放文件夹无法从投放属性的执行文件夹列表中显示的问题。 (NEO-11094)
* 修复了导致“查看填充”窗口无法将200条以上的记录显示为工作流中查询活动的结果目标的问题。 (NEO-11195)
* 修复了Oracle中阻止在选择超过1000个元素的情况下执行DELETE查询的问题。 (NEO-11171)
* 修复了导致在Android推送通知投放的其他参数中将URL编码为跟踪URL的问题。 (NEO-11468)
* 修复了将参数设置为“间隔一天”和“打开次数”时，用户活动报表中发生的脚本错误。 (NEO-11655)
* 修复了通过经过身份验证的Web代理连接到中间源服务器或消息中心时发生的问题。 (NEO-11309)
* 修复了在选择特定架构的元素后保存新投放组合时发生的Oracle错误 **基于SQL视图**. (NEO-11682)
* 修复了在使用解压缩选项通过加载文件活动处理包含.csv的zip文件时，导致生成包含误报的拒绝文件的问题。
* xtkjoblog现已被清除。
