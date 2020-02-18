---
title: 版本18.10
seo-title: 版本18.10
description: 版本18.10
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a8c4face331ab6d646480322c0f53a7147251aa6

---


# 版本18.10{#release-18-10}

## 版本18.10.6 —— 内部版本8985{#release-18-10-6-build-8985}

2019年7月12日

**改进**

* 现在，我们允许在导入工作流程期间删除在Microsoft Dynamics中创建的伪记录。
* 修复了文件收集器工作流活动的一个问题，该问题可能导致在拒绝访问文件时在循环中记录错误。 (NEO-12085)
* 修复了导致用户活动与打开的交付指示器的跟踪报告不一致的问题。 (NEO-11742)
* 改进了在使用内部帐户时执行安全区包的权限。
* 修复了可能导致匹配字段日志错误的问题。 (NEO-8978)

## 版本18.10.5 —— 内部版本8984{#release-18-10-5-build-8984}

2019年4月23日

**改进**

* 修复了在同时分析／发送（同时分析两个交付时）时导致交付分析失败的SQL死锁问题。 (NEO-13026)
* 删除了“工作流热图”中的10,000记录限制以修复缺少的数据问题。 (NEO-12329)
* 修复了在丰富化工作流活动中使用“保留主集的所有其他数据”选项时的问题。 (NEO-13291)

## 版本18.10.4 —— 内部版本8983{#release-18-10-4-build-8983}

2019年4月15日

**改进**

* 修复了事务消息的跟踪指示符的计算过程的问题。 (NEO-12529, NEO-12581)
* 修复了HTTPRequest API的一个问题，该问题未等待所有回调完成。 (NEO-12628)
* 在优惠券临时表中添加了索引以优化交付发送。 (NEO-12437)
* 修复了分析日文(.JP)域的目标收件人的消息时的问题。 (NEO-12246)
* 在Analytics集成中，现在允许检索字符为%的AAM区段数据。 (NEO-12025)
* 修复了使用HTTP2发送推送通知时的Tomcat崩溃问题。 (NEO-12701)

## 版本18.10.3 —— 内部版本8981{#release-18-10-3-build-8981}

2019年1月29日

>[!CAUTION]
>
>这栋建筑已被召回。 请升 [级到最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或联系技 [术支持](https://support.neolane.net/)。

**改进**

* 修复了s3文件传输工作流活动的问题。 (NEO-12473)
* 修复了跟踪工作流可能失败的问题。 (NEO-12520)
* 修复了IMS登录的问题。
* 修复了在使用大型选件ID时，事务性消息传递中的预览和内容审批问题。
* 修复了中间采购（交付计数器）工作流的问题。
* 修复了数据库结构更新的问题，该问题导致NmsRecipient上丢失新索引。
* 修复了在外部文件选项中为分发的主要目标使用“已定义”时可能发生的控制台崩溃问题。 (NEO-12349)
* 修复了多个InMail崩溃问题。
* 修复了使用“更新”数据工作流活动删除FDA Teradata数据库中存储的记录时的问题。
* 修复了密钥管理中的不一致问题。
* 修复了在将字段键入为时富集活动的问题：xml=true且calculated=true
* 修复了在移动应用程序上发送推送通知时的字符转义问题。
* 修复了在中间采购外部帐户中无法从FDA切换到SOAP同步方法的问题。

## 版本18.10.2 —— 内部版本8978{#release-18-10-2-build-8978}

2018年12月6日

>[!CAUTION]
>
>这栋建筑已被召回。 请升 [级到最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或联系技 [术支持](https://support.neolane.net/)。

**改进**

* 修复了在FDA上使用MySQL运行工作流时的各种问题。 (NEO-11652)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了在传送中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了在1:N链接中使用值分布时的显示问题。 (NEO-11820)
* 修复了Worflow Heatmap中的Oracle错误。
* 修复了在丰富化活动中添加选件建议时的正确问题。
* 修复了SQL数据管理连接问题。
* 修复了负ID情况下生成临时工作流表名称的问题。
* 修复了在Workflow HeatMap中计算工作流持续时间的问题。


## 版本18.10 —— 内部版本8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>这栋建筑已被召回。 请升 [级到最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或联系技 [术支持](https://support.neolane.net/)。

**有什么新增功能？**

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
   <td> 在Adobe Campaign中，已对推送通知实施了许多增强功能：<br /> 
    <ul> 
     <li> <p>在iOS中跟踪静默通知 </p> </li> 
     <li> <p>在iOS中实施注册调用反馈</p> </li> 
     <li> <p>提高iOS交付准备速度</p> </li> 
    </ul> <p>作为Google GCM折旧的一部分，Android V2连接器现在仅允许与FCM服务器连接。</p><p>有关详细信息，请参阅详 <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">细文档</a>。 本文详细介绍了人工对FCM的 <a href="https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html">升级</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td> SQL数据管理活动<br /> </td> 
   <td> <p>新的数据管理工作流活动已添加。 通过 <strong>SQL数据管理</strong> ，您可以编写或复制粘贴自己的SQL脚本，以创建和填充工作表（仅限FDA）。 </p> <p>有关详细信息，请参阅详 <a href="../../workflow/using/sql-data-management.md">细文档</a>。</p></td> 
  </tr> 
  <tr> 
   <td> 工作流监控<br /> </td> 
   <td> <p>借助新的Adobe Campaign Workflow HeatMap，平台管理员可以快速以图形形式呈现所有并发工作流，从而监控实例负载和计划工作流。</p> <p>有关详细信息，请参阅详 <a href="../../workflow/using/heatmap.md">细文档</a>。</p> <p>Workflow HeatMap包也可在8977之前（从8700开始）对构建进行需求。 有关请求和安装它的详细信息，请参 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">阅本页</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全增强**

* 修复了一个安全问题，该问题可能导致服务器端请求伪造(SSRF)攻击和拒绝服务(DoS)攻击的漏洞。 (NEO-11453)
* 内容（跟踪重定向、镜像页面、调查等）将由Campaign使用X-Robots-Tag提供：无缓存头。 这可防止Internet搜索引擎对此内容进行索引。 (NEO-11101)
* 修复了订阅API（nms:subscription:Unsubscribe和nms:subscription:Subscribe）中的XTK注入问题。
* 修复了取消订阅Web应用程序中的XTK注入问题。
* 删除了某些SMS日志中不安全显示的密码。

**改进**

* Campaign Classic API现在可在专用页 [面中使用](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。 如果您使用jsapi.chm文件，您现在应该参阅新的在线版本。
* 现在支持PostgreSQL 10、Debian 9和Teradata 16.20。 请参阅兼 [容性矩阵](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。
* 创建SFTP连接时，您现在可以使用代理身份验证。 有关详细信息，请参 [阅详细文档](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration) (NEO-9868)
* 使用 **直邮递送模板创建单次递送时** ,“日期计算公式”选项现在在递送属性中可用。 (NEO-9792)
* 对cookie跟踪和Web应用程序的域名管理进行了改进。 有关更多信息，请参阅下面的“技术演化”部分。
* 在安全性和性能方面，Adobe Marketing cloud共享资产在交付或登录页面的导入已得到改进。
* 移动渠道外部帐户中有一个新的复选框，用于在日志文件中启用详细的SMPP跟踪，这使该输出可从Adobe Campaign界面直接访问。
* 在广播中，现在可以区分每小时最大连接数和最大消息数。 当达到这些限制时，可以知道为什么吞吐量有限。 以前，两种情况都使用相同的消息（“配额满足”）。
* 您现在可以指定在从池中获取连接时执行的SQL脚本。 此脚本可用于设置默认架构。 此脚本将在查询条带化后应用。 (NEO-11256)
* Campaign SDK不再存储用户ID以符合PII规定。 数据现在以哈希存储。
* 导入包导出XML文件时，Campaign现在支持文件中存在BOM，即使在文件中明确声明了编码也是如此。

**技术演进**

客户端和服务器升级

>[!CAUTION]
>
>如果您的服务器已更新为18.10，则必须使用18.10客户端才能访问您的服务器。 18.10客户端将能够连接到旧版服务器。

域名管理

对cookie跟踪和Web应用程序的域名管理进行了改进。

现在，默认支持所有双字母二级域名（例如。aa.com）。 对于更复杂的域名（例如，三个字母的二级域，如。com.au），您需要将它们添加到serverConf的 **cookieDomains** 选项（在重定向标记下）中。 以下是一个示例：

```
<redirection cookiedomain="http://toureiffel.paris">
```

索引增强功能

NmsRecipient上的索引已重新处理。 这应改进使用此表的查询的性能。 如果已对NmsRecipient进行了扩展，则可能需要验证是否没有复制新索引的索引（以最大限度地减少数据库服务器上的空间使用）。 (NEO-8228)

在PostgreSql上，当使用UTF-8归类时，现在可以创建索引，以优化“LIKE &#39;string%&#39;”（或“starts with”）操作。 如果对同一列执行其他操作（例如，按顺序或连接），则需要另一个标准索引。 在架构方面，将通过在索引定义上添加indexOption=&quot;searchFromStart&quot;来完成此操作（它将创建varchar_pattern_ops索引，而不是标准btree索引）。 例如（在NmsRecipient上）:

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

新索引已添加到NmsRtEvent和NmsEventHisto（在“计划”列上），这应该可以缩短相应表单上的显示时间(NEO-11738)。

这些索引更改可能导致执行升级后所需时间增加。

**修补程序**

* 修复了阻止下载 **Web下载工作流程活动中** 的文件的错误。 (NEO-11105)
* 修复了偶尔将“发送指示器 **”和“营销活动属性”工作流保留为“失败** ”状态(NEO-10820)的错误。
* 修复了在工作流中运行列表更新活动后创建的收件人列表被删除的问题。 (NEO-11696)
* 修复了在营销活动日历（日语实例）中提前一个月错误地显示营销活动的问题。 (NEO-11445)
* 修复了导致Analytics配置无法显示在交付属性的“Web分析”选项卡中的问题。 (NEO-11619)
* 修复了尝试编辑和保存nms:delivery输入表单时显示的错误。 (NEO-10973)
* 修复了在运行包含文件传输活动的工作流时发生的外部帐户配置问题。 (NEO-11012)
* 修复了使用zcat函数在数据加载活动中加载文件时返回空行的问题。 (NEO-11273)
* 修复了在分析交付时生成重复的宽日志的问题。 (NEO-11360)
* 修复了在工作流中执行丰富化活动后，由于缺少外联链接密钥而导致交付失败的问题。 (NEO-11537)
* 修复了安装路径包含特定的GB18030中文字符时，无法正确卸载或修复Adobe Campaign的问题。
* 修复了将某些跟踪日志链接到错误交付的问题。 (NEO-11412)
* 修复了可能导致某些部分的交付日志保留的挂起状态比预期更长的问题。 (NEO-11336)
* 修复了编辑查询以将优惠券添加到分发时发生的错误。 (NEO-11037)
* 修复了报告中的一个问题，该问题使图表始终计算值的和，而无论选择的是哪个聚合运算符。 (NEO-10913)
* 由于“request.scheme”函数已弃用，因此已从JSAPI文档中删除它。 (NEO-10828)
* 修复了导致某些具有特定时区配置的用户无法登录Adobe Campaign的问题。 (NEO-10712)
* 修复了使用扩展通用SMPP连接器设置移动渠道外部帐户时出现的问题：如果您为接收机指定了不同的参数，则发射机将错误地使用这些参数而不是自己的参数。
* 修复了在为压力规则设置频率时导致计划交付失败的问题，因为在第一次仲裁之后，交付会不断地重新计算。 (NEO-10016)
* 修复了在应用程序池循环过程中（在nlsrvmod.dll库中）导致IIS web服务器崩溃的问题。 (NEO-10862)
* 修复了在“配置文件”和“目标”屏幕中搜索收件人 **的问题** 。 (NEO-8228)
* 修复了在记录数量较多的情况下访问“活动历史记录”文件夹时可能导致超时错误的问题。 (NEO-11738)
* 修复了可能导致LINE交付收件人错误地返回为“无法访问”的问题。 (NEO-10833)
* 修复了在Oracle上执行具有附加列的工作流查询时的问题。 (NEO-11615)
* 已进行增强，以确保关闭的连接不会在连接池中保存太长时间。 (NEO-11392)
* 修复了使用定位工作流活动(查询、数据加载(RDBMS)等)时的问题通过FDA连接到包含UTF8字符的外部Oracle表（在表名、字段名称等中）并且还包含一个主键约束，该约束具有系统生成的默认约束名称。 (NEO-10714)
* 修复了无法删除分发的HTML内容的问题。 (NEO-11327)
* 修复了在营销活动运行后，直接邮件中XML和CSV文件预览的问题。 (NEO-11290)
* 修复了在丰富化工作流活动中对数据进行排序时的问题。 (NEO-11394)
* 修复了在自定义报告中对数据进行排序时的问题。 (NEO-10896)
* 修复了在将useVault设置与Teradata结合使用时导致错误的问题。 (NEO-11399)
* 修复了在删除多个查询行时导致Adobe Campaign客户端控制台崩溃的问题。 (NEO-10744)
* 修复了在传送直接邮件时在某些情况下无法应用压力规则的问题。 (NEO-9004)
* 修复了使用数据加载活动导入数据类型为“time”的列时发生的问题：即使在删除时间分隔符后，也会重置时间分隔符。 (NEO-10743)
* 修复了在编辑重复传送时，“传送”属性中的“执行”文件夹列表中无法显示“传送”文件夹的问题。 (NEO-11094)
* 修复了“查看填充”窗口无法将超过200条记录显示为工作流中查询活动的最终目标的问题。 (NEO-11195)
* 修复了Oracle中阻止在选择1000个以上元素的情况下执行DELETE查询的问题。 (NEO-11171)
* 修复了导致在Android推送通知交付的其他参数中将URL编码为跟踪URL的问题。 (NEO-11468)
* 修复了将参数设置为“一天间隔”和“打开”时“用户活动”报告中出现的脚本错误。 (NEO-11655)
* 修复了通过经过身份验证的Web代理连接到中间采购服务器或消息中心时出现的问题。 (NEO-11309)
* 修复了在基于SQL视图选择特定架构的元素后保存新的交付合成时 **发生的Oracle错误**。 (NEO-11682)
* 修复了使用解压缩选项通过加载文件活动处理包含。csv的zip文件时，导致生成的包含误报的拒绝文件的问题。
* xtkjoblog现在由清除清除。

