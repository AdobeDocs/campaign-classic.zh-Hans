---
product: campaign
title: Campaign Classic 2018 版
description: 详细了解 Campaign Classic 2018 版
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: true
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 8%

---

# 2018 版{#release-2018}



## 18.10 版

### 18.10.6 版 - 内部版本 8985{#release-18-10-6-build-8985}

2019年7月12

**改进**

* 现在，我们允许在导入工作流期间删除在Microsoft Dynamics中创建的虚设记录。
* 修复了文件收集器工作流活动的问题，当对文件的访问被拒绝时，该问题可能会记录循环中的错误。 (NEO-12085)
* 修复了导致未结投放指标的用户活动和跟踪报表之间报告差异的问题。 (NEO-11742)
* 改进了使用内部帐户时执行安全区域包的权限。
* 修复了可能导致匹配日志中出现错误的问题。 (NEO-8978)

### 18.10.5 版 - 内部版本 8984{#release-18-10-5-build-8984}

2019年4月23日

**改进**

* 修复了在同时分析/发送的情况下（同时分析两个投放时），SQL死锁导致投放分析失败的问题。 (NEO-13026)
* 删除了工作流热图中10,000条记录限制以修复缺少数据的问题。 (NEO-12329)
* 修复了在扩充工作流活动中使用“保留主集中的所有附加数据”选项时的问题。 (NEO-13291)

### 18.10.4 版 - 内部版本 8983{#release-18-10-4-build-8983}

2019年4月15日

**改进**

* 修复了事务性消息跟踪指标的计算过程存在的问题。 (NEO-12529、NEO-12581)
* 修复了HTTPRequest API未等待所有回调完成的问题。 (NEO-12628)
* 在优惠券临时表中添加了索引以优化投放发送。 (NEO-12437)
* 修复了在分析面向日语(.JP)域的收件人的邮件时的问题。 (NEO-12246)
* 在Analytics集成中，现在允许检索具有%字符的AAM区段数据。 (NEO-12025)
* 修复了使用HTTP2发送推送通知时的Tomcat崩溃问题。 (NEO-12701)

### 18.10.3 版 - 内部版本 8981{#release-18-10-3-build-8981}

2019年1月29

>[!CAUTION]
>
>此内部版本已撤消。 请 [升级到最新内部版本](../../production/using/build-upgrade.md)  或联系人 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**改进**

* 修复了s3文件传输工作流活动的问题。 (NEO-12473)
* 修复了跟踪工作流中可能失败的问题。 (NEO-12520)
* 修复了IMS登录问题。
* 修复了使用大型选件ID时，事务型消息传递中的预览和内容审批问题。
* 修复了中间源（投放计数器）工作流的问题。
* 修复了数据库结构更新在NmsRecipient上删除新索引的问题。
* 修复了在为投放的主目标使用“在外部文件中定义”选项时可能发生的控制台崩溃问题。 (NEO-12349)
* 修复了多次InMail崩溃问题。
* 修复了使用更新数据工作流活动删除存储在FDATeradata数据库中的记录时的问题。
* 修复了密钥管理中的不一致问题。
* 修复了以下字段输入时的扩充活动问题：xml=true和calculated=true
* 修复了在移动应用程序上发送推送通知时的字符转义问题。
* 修复了阻止在中间源外部帐户中从FDA切换到SOAP同步方法的问题。

### 18.10.2 版 - 内部版本 8978{#release-18-10-2-build-8978}

2018年12月6

>[!CAUTION]
>
>此内部版本已撤消。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系人 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**改进**

* 修复了在FDA上使用MySQL运行工作流时出现的各种问题。 (NEO-11652)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了在投放中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了在使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了通过1：N链接使用值分布时的显示问题。 (NEO-11820)
* 修复了工作流热图中的Oracle错误。
* 修复了在扩充活动中添加优惠建议时的权限问题。
* 修复了SQL数据管理连接问题。
* 修复了在ID为负时生成临时工作流表名称的问题。
* 修复了在Workflow HeatMap中计算工作流持续时间时出现的问题。


### 18.10.1 版 - 内部版本 8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>此内部版本已撤消。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系人 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> 在Adobe Campaign中为推送通知实施了许多增强功能：<br /> 
    <ul> 
     <li> <p>在iOS中跟踪静默通知 </p> </li> 
     <li> <p>在iOS中实施注册调用的反馈</p> </li> 
     <li> <p>提高iOS投放准备速度</p> </li> 
    </ul> <p>作为Google弃用GCM的一部分，Android V2连接器现在仅允许连接到FCM服务器。</p><p>有关更多信息，请参阅<a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">详细文档</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> SQL数据管理活动<br /> </td> 
   <td> <p>添加了新的数据管理工作流活动。 此 <strong>sql数据管理</strong> 通过活动，您可以编写或复制粘贴自己的SQL脚本，以创建和填充工作表（仅限FDA）。 </p> <p>有关更多信息，请参阅<a href="../../workflow/using/sql-data-management.md">详细文档</a>。</p></td> 
  </tr> 
  <tr> 
   <td> 工作流监测<br /> </td> 
   <td> <p>借助新的Adobe Campaign Workflow HeatMap，平台管理员可以快速以图形方式表示所有并发工作流，从而监控实例的负载并相应地规划工作流。</p> <p>有关更多信息，请参阅<a href="../../workflow/using/heatmap.md">详细文档</a>。</p> <p>8977之前的版本（从版本8700开始）也按需提供工作流热图包。 有关请求和安装该软件的更多信息，请参阅 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">此页面</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 修复了可能导致服务器端请求伪造(SSRF)攻击和拒绝服务(DoS)攻击漏洞的安全问题。 (NEO-11453)
* 内容（跟踪重定向、镜像页面、调查等） 现在将由Campaign提供，带有X-Robots-Tag： nocache标头。 这可以防止互联网搜索引擎索引此内容。 (NEO-11101)
* 修复了订阅API (nms)中的XTK注入问题:subscription:取消订阅和nms:subscription:订阅)。
* 修复了退订Web应用程序中的XTK注入问题。
* 移除了某些短信日志中显示的不安全密码。

**改进**

* Campaign Classic API 现在可在[专用页面](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans)中使用。如果您使用的是 jsapi.chm 文件，您现在应该参阅新的在线版本。
* 现在支持PostgreSQL 10、Debian 9和Teradata16.20。 请参阅[兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)。
* 创建SFTP连接时，您现在可以使用代理身份验证。 欲了解更多信息，请参见 [详细文档](../../installation/using/file-res-management.md) (NEO-9868)
* 此 **日期计算公式** 现在，使用直邮投放模板创建单个投放时，投放属性中提供了选项。 (NEO-9792)
* Cookie跟踪和Web应用程序的域名管理已得到改进。 有关更多信息，请参阅下面的“技术演变”部分。
* 在投放或登陆页面中导入Adobe Marketing Cloud共享资源在安全性和性能方面得到了改进。
* Mobile渠道外部帐户中新增了一个复选框，用于在日志文件中启用详细的SMPP跟踪，从而可直接从Adobe Campaign界面访问此输出。
* 在broadlog中，最大连接数和每小时最大消息数之间现在有一个区别。 当达到这些限制时，就可以知道吞吐量为何受限。 以前，同一消息（“达到配额”）同时适用于这两种情况。
* 现在，您可以指定在从池获取连接时要执行的SQL脚本。 此脚本可用于设置默认架构。 此脚本将在查询分段后应用。 (NEO-11256)
* 为遵守PII法规，Campaign SDK不再存储用户ID。 数据现在存储为哈希。
* 现在，在导入资源包导出XML文件时，Campaign支持文件中存在BOM，即使在该文件中明确声明了编码也是如此。

**技术演进**

客户端和服务器升级

>[!CAUTION]
>
>如果您的服务器已更新到18.10，则必须使用18.10版客户端才能访问您的服务器。 18.10客户端将能够连接到较旧的服务器版本。

域名管理

Cookie跟踪和Web应用程序的域名管理已得到改进。

现在，默认情况下支持所有两个字母的第二级域名(例如.aa.com)。 对于更复杂的域名（例如，由3个字母组成的二级域名，如.com.au），您需要将它们添加到 **cookieDomains** serverConf的选项（在重定向标记下）。 示例如下：

```
<redirection cookiedomain="http://toureiffel.paris">
```

索引增强功能

已重新处理NmsRecipient上的索引。 这应该可以提高使用此表的查询的性能。 如果已对NmsRecipient进行了扩展，则可能需要验证是否没有复制新索引的索引（以最大限度地减少数据库服务器上的空间使用）。 (NEO-8228)

在使用UTF-8归类的PostgreSql上，现在可以创建将优化“LIKE &#39;string%&#39;”（或“starts with”）操作的索引。 如果对同一列执行其他操作（例如，排序依据或联接），则需要另一个标准索引。 在架构方面，将通过在索引定义上添加indexOption=&quot;searchFromStart&quot;来完成此操作（它将创建varchar_pattern_ops索引而不是标准btree索引）。 例如（在NmsRecipient上）：

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

已向NmsRtEvent和NmsEventHisto（“已计划”列上）添加了新索引，这应会缩短相应表单的显示时间(NEO-11738)。

这些索引更改可能会导致执行升级后所需的时间增加。

**修补程序**

* 修复了阻止文件从 **Web下载** 工作流活动。 (NEO-11105)
* 修复了偶尔会导致 **发送指标和营销活动属性** 工作流处于失败状态(NEO-10820)。
* 修复了删除在工作流中运行列表更新活动后创建的收件人列表的问题。 (NEO-11696)
* 修复了在营销活动日历（在日本实例上）中提前一个月错误地显示营销活动的问题。 (NEO-11445)
* 修复了导致Analytics配置无法在投放属性的Web Analytics选项卡中显示的问题。 (NEO-11619)
* 修复了尝试编辑和保存nms：delivery输入表单时显示的错误。 (NEO-10973)
* 修复了运行包含文件传输活动的工作流时发生的外部帐户配置问题。 (NEO-11012)
* 修复了在数据加载活动中使用zcat函数加载文件时返回空白行的问题。 (NEO-11273)
* 修复了在分析投放期间生成重复的广泛日志的问题。 (NEO-11360)
* 修复了在工作流中执行扩充活动后，由于缺少外链接键而导致投放失败的问题。 (NEO-11537)
* 修复了当安装路径包含特定GB18030中文字符时，阻止正确卸载或修复Adobe Campaign的问题。
* 修复了将某些跟踪日志链接到错误投放的问题。 (NEO-11412)
* 修复了可能导致投放日志的某些部分在挂起状态下保留的时间长于预期的问题。 (NEO-11336)
* 修复了在编辑查询以向投放添加优惠券时发生的错误。 (NEO-11037)
* 修复了报表中的问题，该问题使得图表始终计算值的总和，而不管选择了哪个聚合运算符。 (NEO-10913)
* 由于“request.scheme”函数已被弃用，因此已从JSAPI文档中删除该函数。 (NEO-10828)
* 修复了导致某些具有特定时区配置的用户无法登录Adobe Campaign的问题。 (NEO-10712)
* 修复了在使用扩展通用SMPP连接器设置移动渠道外部帐户时发生的问题：如果您为接收器使用不同的参数指定，则发送器将错误地使用这些参数而不是其自己的参数。
* 修复了在为压力规则设置频率时导致计划投放失败的问题，因为在首次仲裁后会不断重新计算投放。 (NEO-10016)
* 修复了在应用程序池回收过程（在nlsrvmod.dll库中）中导致IIS Web服务器崩溃的问题。 (NEO-10862)
* 修复了可能阻止在 **配置文件和目标** 屏幕。 (NEO-8228)
* 修复了在记录数量较多的情况下访问Event History文件夹时可能导致超时错误的问题。 (NEO-11738)
* 修复了可能导致LINE投放收件人错误返回为“不可访问”的问题。 (NEO-10833)
* 修复了在工作流中执行带有附加列的Oracle查询时的问题。 (NEO-11615)
* 已进行增强以确保已关闭的连接不会在连接池中保留太长时间。 (NEO-11392)
* 修复了使用定位工作流活动(查询、数据加载(RDBMS)等)时的问题 通过FDA连接到包含UTF8字符（表名称、字段名称等）的外部Oracle表 并且还包含一个主键约束，该约束具有系统生成的默认约束名称。 (NEO-10714)
* 修复了可能阻止删除投放的HTML内容的问题。 (NEO-11327)
* 修复了在运行营销活动后直邮中预览XML和CSV文件的问题。 (NEO-11290)
* 修复了在扩充工作流活动中排序数据时的问题。 (NEO-11394)
* 修复了对自定义报表中的数据排序的问题。 (NEO-10896)
* 修复了将useVault设置与Teradata结合使用时导致出现错误的问题。 (NEO-11399)
* 修复了在删除多个查询行时导致Adobe Campaign客户端控制台崩溃的问题。 (NEO-10744)
* 修复了在投放直邮时，阻止在某些情况下应用压力规则的问题。 (NEO-9004)
* 修复了在使用数据加载活动导入数据类型为“time”的列时发生的问题：即使在删除后时间分隔符也会重置。 (NEO-10743)
* 修复了在编辑循环投放时，阻止从投放属性的执行文件夹列表中显示投放文件夹的问题。 (NEO-11094)
* 修复了导致“查看群体”窗口无法显示200多条记录作为工作流中“查询”活动结果目标的问题。 (NEO-11195)
* 修复了Oracle中的一个问题，该问题阻止在选择1000多个元素的情况下执行DELETE查询。 (NEO-11171)
* 修复了导致在Android推送通知投放的其他参数中将URL编码为跟踪URL的问题。 (NEO-11468)
* 修复了将参数设置为“一天间隔”和“打开”时，用户活动报表中发生的脚本错误。 (NEO-11655)
* 修复了在通过经过身份验证的Web代理连接到中间源服务器或消息中心时发生的问题。 (NEO-11309)
* 修复了在选择特定架构的元素后保存新投放组合时发生的Oracle错误 **基于SQL视图**. (NEO-11682)
* 修复了在使用解压缩选项通过加载文件活动处理包含.csv的zip文件时导致生成包含误报的拒绝文件的问题。
* xtkjoblog现在由清理清除。

## 18.6 版

### 18.6.2 版 - 内部版本 8949{#release-18-6-3-build-8949}

2018年8月22

>[!CAUTION]
>
>此内部版本已撤消。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系人 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> 查询分段<br /> </td> 
   <td> <p>当多个Campaign用户连接到同一个FDATeradata外部帐户时，您现在可以传递特定于每个用户的查询范围（键/值对）。 每当Campaign用户在Teradata数据库上执行查询时，Adobe Campaign现在能够发送与该用户关联的元数据。 例如，Teradata管理员可以使用这些数据（包含在一组键和值中）进行审核或管理访问权限。</p><p>有关更多信息，请参阅<a href="../../installation/using/external-accounts.md">详细文档</a>。</p> </td>
  </tr> 
 </tbody> 
</table>

**改进**

* 电子邮件存档日志已得到增强，这使得检查哪些电子邮件已成功投放或未能通过密件抄送存档变得更容易和更清晰。 (NEO-10675)
* 修复了导致在跟踪broadlog中显示负载平衡器IP而不是客户IP的问题。 (NEO-11295)
* 修复了导致投放属性被错误覆盖的随机问题。 (NEO-11015)
* 修复了对扩充活动结果进行排序时的语法错误。 (NEO-11394)
* 修复了在中使用计算字段时的问题 **[!UICONTROL Survey answers]** 工作流活动。 (NEO-11382)
* Tomcat已更新，以防止漏洞攻击。 (NEO-11503)
* 修复了使用指向PostgreSQL数据库的FDA连接时的LATIN1编码错误。 (NEO-11299)
* 修复了使用时出现的问题 **[!UICONTROL Prepare the personalization data with a workflow]** 投放选项。 (NEO-11047)
* 修复了在使用扩展连接器时阻止发送短信的升级后问题。
* 改进了包的导入/导出（在界面中添加了日志和区域）。
* 修复了在升级后日志中显示无用错误的问题 **[!UICONTROL Survey answers]** 未完全配置工作流活动。

**技术演进**

查询分段

使用特定键（PROXYUSER或PROXYROLE）将Teradata用户或角色与Campaign用户相关联。 已添加使用此代理用户/角色的新权限。 您需要将GRANTCONNECTTHROUGH访问权限添加到数据库帐户(在Teradata外部帐户中定义的帐户)。

已在Teradata外部帐户中添加了一个新选项卡。 此 **[!UICONTROL Query banding]** 选项卡包括以下选项：

* **[!UICONTROL Active]**：选中此框可激活该功能。
* **[!UICONTROL Default]**：输入在用户没有关联的查询分段时要使用的默认查询分段。 如果未定义默认查询分段，则没有关联查询分段的用户将无法使用Teradata。
* **[!UICONTROL Users]**：为每个用户指定查询分段。 您可以根据需要添加任意数量的键/值对。 例如：“priority=1；workload=high；”

有关查询分段的更多信息，请参阅以下文章：

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24千伏吉瓦](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### 18.6.1 版 - 内部版本 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>此内部版本已撤消。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系人 [技术支持](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> 安全性改进<br /> </td> 
   <td> 向Campaign Classic添加了一系列安全改进。 下面列出了改进和修复。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支持Windows Server 2016<br /> </td> 
   <td> Adobe Campaign 现在与 Windows Server 2016 兼容。请参阅 <a href="https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html">Campaign Classic兼容性矩阵</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

decryptString

此 **decryptString** 函数已被弃用。 请参阅 [已弃用和已删除的功能](deprecated-features.md) 文章。

对于新客户，此函数现在仅用于解密登陆页面中收件人的加密ID。 要解密存储在外部帐户中的密码，请使用新的 **decryptPassword** 函数。

对于现有客户，此函数的行为不会发生更改，但建议您使用 **decryptPassword** 而不是 **decryptString**. 此 **XtkSecurity_Unsafe_DecryptString** 兼容性选项由postupgrade添加，默认情况下处于激活状态，允许您继续使用函数。 如果要取消激活 **decryptString**，取消激活选项。

decryptPassword

此 **decryptPassword** 函数已添加。 它允许您解密存储在外部帐户中的密码。 请参阅 [JSAPI](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html) 文档，以了解更多信息。

文件API

对于新安装，通过文件API访问文件夹的权限仅限于 **var**， **sftp** 和Adobe Campaign的临时文件夹。

对于现有客户，文件API无法再访问 **会议** Adobe Campaign的文件夹。 此 **XtkSecurity_Disable_JSFileSandboxing** 兼容性选项由postupgrade添加，默认情况下处于激活状态，允许您继续访问其他文件夹。 如果要限制对 **var**， **sftp** 和Adobe Campaign的临时文件夹，请取消激活选项。

**Patch**

* 修复了可能影响短信事务型消息性能的问题。 (NEO-9812)

## 18.4 版

### 18.4.5 版 - 内部版本 8937{#release-18-4-5-build-8937}

二零一八年十一月二十一日

**改进**

* 修复了在FDA上使用MySQL运行工作流时出现的各种问题。 (NEO-11652)
* 修复了在特定情况下，导致投放群体的一部分保持挂起状态的问题。 (NEO-11336)
* 修复了短信自动响应的间歇性问题。 (NEO-11811)
* 修复了在投放中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了在扩充工作流活动中执行排序时的语法错误。 (NEO-11394)
* 修复了在重新启动IIS时可能导致Web服务器崩溃的问题。 (NEO-10862)
* 修复了可能导致跟踪工作流在内部版本升级(FDA - SQL)后失败的问题。 (NEO-11635)
* 修复了可能导致工作流列表数据丢失的问题。 (NEO-11696)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了Web跟踪无法用于“com.au”域的问题(NEO-4385)。
* 修复了在使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了在选择特定架构的元素后保存新投放时的Oracle错误(NEO-11682)。
* 修复了查询包含重音字符(FDA/Teradata)的字段时的问题。 外部帐户现在允许您更改用于与Teradata驱动程序通信的编码。 (NEO-11818).
* 修复了在推送通知中向其他变量传递URL时的跟踪问题，该问题可能会导致移动应用程序收到的数据格式不正确或不正确。 (NEO-11468、NEO-11960)
* 修复了在通过1：N链接使用值分布时导致显示问题的问题。 (NEO-11820)
* 修复了批量加载无法在Teradata16上工作的问题。
* 增加了Teradata上时间戳的缓冲区大小，以避免与15.10驱动程序发生绑定问题。
* 改进了可能导致升级后问题的长名称索引的管理。
* 改进了子死处理(MTA)期间的共享内存可用时间。
* 修复了Apache中的潜在死锁（跟踪）。


### 18.4.4 版 - 内部版本 8936{#release-18-4-4-build-8936}

2018年8月1日

**改进**

* 电子邮件存档日志已得到增强，这使得检查哪些电子邮件已成功投放或未能通过密件抄送存档变得更容易和更清晰。 (NEO-10675)
* 修复了导致在跟踪broadlog中显示负载平衡器IP而不是客户IP的问题。 (NEO-11295)
* 修复了使用指向PostgreSQL数据库的FDA连接时的LATIN1编码错误。 (NEO-11299)
* 修复了使用时出现的问题 **[!UICONTROL Prepare the personalization data with a workflow]** 投放选项。 (NEO-11047、NEO-11301)
* 修复了导致投放属性被错误覆盖的随机问题。 (NEO-11015)
* 修复了在中使用计算字段时的问题 **[!UICONTROL Survey answers]** 工作流活动。 (NEO-11382)
* 修复了在中使用存储在XML中的数据时的问题 **[!UICONTROL Survey answers]** 工作流活动。 (NEO-10816)
* 修复了使用内部版本8935执行服务器升级时的问题。
* 修复了在升级后日志中显示无用错误的问题 **[!UICONTROL Survey answers]** 未完全配置工作流活动。
* FDATeradata：修复了SQL表中自动递增字段和索引的问题。

### 18.4.3 版 - 内部版本 8935{#release-18-4-3-build-8935}

2018年6月22

**改进**

* 修复了Microsoft Edge和Internet Explorer的跟踪编码问题。 (NEO-11257)
* 修复了LINE投放中的图像链接个性化问题。 (NEO-11077)
* 修复了阻止ID序列生成机制正常工作的问题。 (NEO-11115)
* 修复了在使用具有整数类型对帐密钥的自定义命名空间时，隐私(GDPR)请求无法工作的问题。 (NEO-11123)
* 修复了在使用时可能发生的错误 **[!UICONTROL Distribution of values]** 中的选项 **[!UICONTROL Query]** 工作流活动。 (NEO-10958)
* 修复了将优惠空间从营销实例同步到交互实例时的问题。 (NEO-11162)
* 改进了在升级后期间对长名称索引的管理

### 18.4.2 版 - 内部版本 8932{#release-18-4-2-build-8932}

2018年5月22日

**改进**

* 修复了Windows Server更新无法正常工作的问题。
* 修复了中的一个问题 **[!UICONTROL Survey Result]** 活动。 报告显示不正确。 (NEO-10816)
* 修复了在使用退回邮件服务器时inMail进程可能发生的性能问题。 (NEO-10641)
* 修复了在升级1000多个架构时可能发生的数据库升级问题。

### 18.4.1 版 - 内部版本 8931{#release-18-4-build-8931}

2018年4月24日

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
   <td> 欧盟通用数据保护条例(GDPR)<br /> </td> 
   <td> <p>GDPR是欧盟(EU)的新隐私法，旨在协调数据保护要求并使之现代化，于2018年5月25日生效。 GDPR 适用于所持有数据的数据主体位于欧盟的 Adobe Campaign 客户。</p> <p>除了Adobe Campaign中已有的可用隐私功能（包括同意管理、数据保留设置和用户角色）之外，我们还将以数据处理方的角色利用此机会来包含其他功能，以帮助您作为数据控制方为特定GDPR请求做好准备：</p> 
    <ul> 
     <li> <p>访问权：允许数据主体接收其由数据控制者捕获的个人数据的副本，可能包括存储在Adobe Campaign中的数据。</p> </li> 
     <li> <p>删除权：允许数据主体擦除其由数据控制者捕获的个人数据，可能包括存储在Adobe Campaign中的数据。</p> </li> 
    </ul> 有关更多信息，请参阅<a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">详细文档</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的用户档案<br /> </td> 
   <td> <p>Adobe Campaign现在提供活动用户档案的列表，每月通过专用工作流更新。</p> <p>有关更多信息，请参阅<a href="../../platform/using/about-profiles.md#active-profiles">详细文档</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> Android推送连接器增强<br /> </td> 
   <td> <p>Android连接器已得到增强，以支持更高的吞吐量。 </p> <p>有关更多信息，请参阅<a href="../../delivery/using/configuring-the-mobile-application.md">详细文档</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 现已禁用外部实体的扩展，以防止来自未经身份验证用户的潜在攻击。 (NEO-10173)
* 增强了权限，以防止标准用户更改实例配置参数，如应用程序访问URL、LDAP设置等。 (NEO-10171)
* 修复了可能通过栈栈跟踪泄露敏感信息的问题。 错误详细信息现在记录到无法从外部网络访问的位置的后端。 (NEO-10176)
* 增强的权限，以防止标准用户查看管理员上传的文档和/或导出的资源包。 (NEO-10170)

**改进**

* **LINE渠道 — 体系结构增强**：与Adobe Campaign中的所有其他渠道一样，现在，所有部署类型（托管、混合和内部部署）都支持LINE渠道。
* **序列自动生成**：ID生成机制已得到增强，以提高具有大量对象的Campaign实例的生命周期。

**其他变更**

* 新模式可用于使用命令行导入软件包，允许循环依赖关系（不建议用于大型软件包）。 有关更多信息，请参阅“技术演变”部分。 (NEO-8979)
* 改进了Teradata中大量数据加载的性能，并修复了阻止在日志中显示处理的数据的正确值的问题。 (NEO-10429)
* 现在，从Audience Manager导入受众适用于拆分文件。 以前，importSharedAudience技术工作流只导入区段的最后一个文件。 (NEO-10156)
* 在Windows上，Campaign服务器的默认安装路径已更改。 在启动64位版本安装程序时，默认安装路径现在为： **C:\Program Files\Adobe\AdobeCampaign Classicv7** 而不是 **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 增强了默认MX规则，以包含更多域并优化吞吐量。
* 对部署向导SOAP调用(xtk：serverOptions#SaveOptions)强制执行访问限制。
* 删除了weka.jar过时的库，并更新了OpenSSL库以进行安全优化。
* 改进了计费技术工作流，以保护实例性能。
* 管理员设置或重置任何操作员密码的能力已恢复。 要实现此目的，请右键单击某个运算符，然后选择 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 并设置操作员的新密码。 我们建议操作员在首次重新连接时更改密码。 有关更多信息，请参阅[详细文档](../../production/using/lost-password.md)。
* 为了支持Adobe Target中的新增多租户功能，在配置与Target集成的选项和外部帐户时，现在可以向URL添加新的“at_property”参数。 此参数要使用的值可以在Adobe Target中找到，并供Campaign在执行对Target的调用时使用。 有关更多信息，请参阅[详细文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 现在，您可以指定在单击Adobe Target提供的图像时要打开的默认登录页面。 以前，单击该图像会在创建电子邮件时指向默认图像集。 有关更多信息，请参阅[详细文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 已添加 **启用SMPP跟踪** 用于强制跟踪输出的外部帐户中的复选框。 有关更多信息，请参阅[详细文档](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)。

**技术演进**

queryDef

已修改有关“orderBy”子句的queryDef。 在更改之前，查询表的主键将隐式添加到“orderBy”子句中。 在某些数据库引擎（至少是postgresql）上，它阻止使用索引（orderBy子句的所有字段都必须由同一索引覆盖）。 如果您依赖于此行为，则必须在“orderBy”子句中显式添加主键。

例如，如果您具有以下查询：

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

它会隐式传递为（在18.4版本更改之前）：

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode函数

对于非ASCII字符，“urlEncode”JavaScript函数无法正常工作。 已更正此错误，现在，它应该可以与所有Unicode字符（包括日语字符）一起使用。 如果您依赖非ASCII字符的“urlEncode”行为，则必须调整代码。

包导入新模式

新模式可用于使用命令行导入软件包，允许循环依赖关系（不建议用于大型软件包）。 保留现有功能。 对于具有循环依赖关系的此类包，会添加一个新标记 **-usejs** 已添加到命令行软件包导入。 在执行时，它将使用与从界面执行资源包导入时相同的JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修补程序**

* 修复了将投放和跟踪日志从Adobe Campaign Standard复制到Adobe Campaign Classic时的同步问题。 (NEO-10023)
* 修复了在快速加载操作失败后恢复ETLTeradata时，处理Error和Log表的问题。 现在，每次恢复工作流时，都会正确删除“错误”表和“日志”表。 (NEO-10672)
* 修复了在安装FDA包时自动安装配置单元包(Hadoop所需)的升级后问题。 (NEO-10592)
* 修复了将无效域视为 **未定义** 错误。 (NEO-10248)
* 修复了在发送android推送投放时在deliveryLogStats表中复制日志的问题。 (NEO-10234)
* 修复了可能导致某些条形码格式无法被条形码扫描仪读取的问题。 (NEO-10125)
* 修复了使用非ASCII字符时“urlEncode”JavaScript函数出现的问题。 有关更多信息，请参阅“技术演变”部分。 (NEO-10123)
* 修复了在Teradata数据库上执行包含sha256函数的查询时的问题。 (NEO-10119)
* 修复了在使用非常大的SalesForce表时SalesForce活动中可能发生的工作流内存错误。 (NEO-9900)
* 修复了的问题 **生成补码** 使用FDA时定位工作流活动中的选项。 (NEO-9878)
* 修复了可能导致 **已处理** 和 **成功** 使用中间源时，量度未在营销实例上更新。 (NEO-9454)
* 修复了平台中选件总数超过10,000件时的交互非重新建议规则(NEO-9352)
* 修复了在使用XML外部文件时可能阻止指定投放目标的问题。 (NEO-9312)
* 修复了对优惠运行假设并更新建议状态时可能导致工作流错误的问题。 (NEO-9304)
* 修复了使用基于Android投放映射属性的压力规则时投放分析期间发生的错误。 (NEO-9202)
* 修复了对收件人列表中的列进行排序时可能导致性能问题的问题。 有关queryDef修改的更多信息，请参阅下面的“技术演变”部分。 (NEO-9042)
* 修复了批准电子邮件中的链接可能指向不正确的登录URL的问题，尤其是使用Federated ID登录类型时。 (NEO-9011)
* 修复了可能导致某些时区报表的日期选择器中显示错误日期的问题。 (NEO-9007)
* 修复了在使用FDA SQL数据库时无法查看出站目标的问题。 (NEO-8924)
* 修复了导致MS Dynamics CRM连接器无法提取当月前7天的数据的问题。 (NEO-8803)
* 修复了Analytics集成中阻止用户包含国际字符的错误。 (NEO-8719)
* 修复了在没有适当权限的情况下可能启用工作流编辑的问题。 (NEO-8708)
* 修复了在混合架构中使用消息中心时，导致连接断开或连接丢失（超时）的FDA over HTTPs问题。 (NEO-8438)
* 修复了在负ID的增量查询活动中发生的工作流错误。 (NEO-8229)
* 修复了可能导致在某些屏幕中显示双滚动条的问题。 (NEO-8208)
* 修复了在运行更新数据库结构向导时导致显示错误消息的问题。 PostUpgrade将执行名称大于30的索引的重命名。 请注意，对于大型表，索引替换将需要时间。 (NEO-7983)
* 修复了跟踪日志未正确从消息中心执行实例同步到控制实例的问题。 (NEO-7286)
* 修复了优惠扩充活动的性能问题。 (NEO-7263)
* 修复了在通过FDA查询Redshift数据库时无法使用DaysAgo函数的问题。 (NEO-7099)
* 修复了数据管理中阻止在类似扩充的工作流活动中创建索引的回归。
* 修复了在使用标题@id创建外部资源时可能发生的问题
* 修复了在通过FTP服务器上传压缩文件或在文件名中包含通配符的文件时可能发生的问题。
* 修复了在Campaign Standard中创建的外部自定义资源中的长基类型枚举的问题。
* 修复了可能导致发送短信的问题，即使在与提供商的连接失败导致短信丢失时也是如此。
* 修复了导致SMTP连接无限期停滞的错误。
* 修复了在使用LINE映射或筛选和定位架构不同时在消息准备期间出现的压力类型规则问题。
