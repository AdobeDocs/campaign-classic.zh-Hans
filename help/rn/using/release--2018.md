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

2019年7月12日

**改进**

* 现在，允许在导入工作流期间删除在Microsoft Dynamics中创建的虚拟记录。
* 修复了文件收集器工作流活动的问题，该问题在拒绝访问文件时可能会循环记录错误。 (NEO-12085)
* 修复了导致用户活动与打开投放指示器的跟踪报表之间存在报表差异的问题。 (NEO-11742)
* 改进了在使用内部帐户时执行安全区域包的权限。
* 修复了可能导致匹配字段日志中出现错误的问题。 (NEO-8978)

### 18.10.5 版 - 内部版本 8984{#release-18-10-5-build-8984}

2019年4月23日

**改进**

* 修复了SQL死锁的问题，该问题在同时分析/发送（同时分析两个投放）的情况下导致投放分析失败。 (NEO-13026)
* 删除了工作流热图中的10,000条记录限制，以修复缺失的数据问题。 (NEO-12329)
* 修复了在扩充工作流活动中使用“从主集中保留所有其他数据”选项时的问题。 (NEO-13291)

### 18.10.4 版 - 内部版本 8983{#release-18-10-4-build-8983}

2019年4月15日

**改进**

* 修复了事务型消息的跟踪指标的计算过程中存在的问题。 (NEO-12529、NEO-12581)
* 修复了HTTPRequest API未等待所有回调完成的问题。 (NEO-12628)
* 在优惠券临时表中添加了索引，以优化投放发送。 (NEO-12437)
* 修复了分析日语(.JP)域的目标收件人的消息时的问题。 (NEO-12246)
* 在Analytics集成中，现在允许检索包含%字符的AAM区段数据。 (NEO-12025)
* 修复了使用HTTP2发送推送通知时的Tomcat崩溃问题。 (NEO-12701)

### 18.10.3 版 - 内部版本 8981{#release-18-10-3-build-8981}

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

### 18.10.2 版 - 内部版本 8978{#release-18-10-2-build-8978}

2018年12月6日

>[!CAUTION]
>
>这栋建筑已被召回。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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


### 18.10.1 版 - 内部版本 8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>这栋建筑已被召回。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
    </ul> <p>作为遭Google弃用的GCM的一部分，Android V2连接器现在只能连接到FCM服务器。</p><p>有关更多信息，请参阅<a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">详细文档</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> SQL数据管理活动<br /> </td> 
   <td> <p>添加了新的数据管理工作流活动。 的 <strong>SQL数据管理</strong> 活动允许您编写或复制粘贴您自己的SQL脚本，以创建和填充工作表（仅限FDA）。 </p> <p>有关更多信息，请参阅<a href="../../workflow/using/sql-data-management.md">详细文档</a>。</p></td> 
  </tr> 
  <tr> 
   <td> 工作流监测<br /> </td> 
   <td> <p>借助新的Adobe Campaign Workflow HeatMap，平台管理员能够快速以图形形式表示所有并发工作流，从而监控实例的负载并相应地规划工作流。</p> <p>有关更多信息，请参阅<a href="../../workflow/using/heatmap.md">详细文档</a>。</p> <p>对于8977之前的版本（从8700开始），也可以根据需要使用Workflow HeatMap包。 有关请求和安装它的更多信息，请参阅 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">本页</a>.</p> </td> 
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

* Campaign Classic API 现在可在[专用页面](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans)中使用。如果您使用的是 jsapi.chm 文件，您现在应该参阅新的在线版本。
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

**修补程序**

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

## 18.6 版

### 18.6.2 版 - 内部版本 8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>这栋建筑已被召回。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> <p>当多个Campaign用户连接到同一FDATeradata外部帐户时，您现在可以传递特定于每个用户的查询频带（键/值对）。 每次Campaign用户对Teradata数据库执行查询时，Adobe Campaign现在都能够发送与用户关联的元数据。 这些Teradata（包含在键和值列表中）随后可由数据管理员用于审核目的或管理访问权限，例如。</p><p>有关更多信息，请参阅<a href="../../installation/using/external-accounts.md">详细文档</a>。</p> </td>
  </tr> 
 </tbody> 
</table>

**改进**

* 电子邮件存档日志已得到增强，这使得检查哪些电子邮件已成功发送或通过密送存档失败变得更加容易和清晰。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而不是客户IP的问题。 (NEO-11295)
* 修复了导致投放属性被错误覆盖的随机问题。 (NEO-11015)
* 修复了对扩充活动结果进行排序时出现的语法错误。 (NEO-11394)
* 修复了在 **[!UICONTROL Survey answers]** 工作流活动。 (NEO-11382)
* Tomcat已更新，以防止漏洞利用。 (NEO-11503)
* 修复了使用FDA连接到PostgreSQL数据库时LATIN1编码错误。 (NEO-11299)
* 修复了在使用 **[!UICONTROL Prepare the personalization data with a workflow]** 投放选项。 (NEO-11047)
* 修复了在使用扩展连接器时无法发送短信的升级后问题。
* 改进了包导入/导出（界面中添加了日志和区域）。
* 修复了在升级后日志中显示无用错误的问题 **[!UICONTROL Survey answers]** 工作流活动未完全配置。

**技术演进**

查询分段

特定键（PROXYUSER或PROXYROLE）用于将Teradata用户或角色与Campaign用户关联。 添加了使用此代理用户/角色的新权限。 您需要将GRANTCONNECTTHROUGH访问权限添加到Teradata库帐户（在数据外部帐户中定义）。

在Teradata外部帐户中添加了新选项卡。 的 **[!UICONTROL Query banding]** 选项卡包含以下选项：

* **[!UICONTROL Active]**:选中此框可激活该功能。
* **[!UICONTROL Default]**:输入默认查询分段，在用户没有关联的查询分段时使用该分段。 如果没有定义默认查询分段，则没有关联查询分段的用户将无法使用Teradata。
* **[!UICONTROL Users]**:为每个用户指定查询分段。 您可以根据需要添加任意数量的键/值对。 例如：&#39;priority=1;workload=high;&#39;

有关查询分段的详细信息，请参阅以下文章：

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### 18.6.1 版 - 内部版本 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>这栋建筑已被召回。 请 [升级到最新内部版本](../../production/using/build-upgrade.md) 或联系 [技术支持](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> 向Campaign Classic添加了一系列安全改进功能。 下面列出了改进和修复。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支持Windows Server 2016<br /> </td> 
   <td> Adobe Campaign 现在与 Windows Server 2016 兼容。请参阅 <a href="https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html">Campaign Classic兼容性矩阵</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

decryptString

的 **decryptString** 函数被弃用。 请参阅 [已弃用和已删除的功能](deprecated-features.md) 文章。

对于新客户，此函数现在仅用于解密登陆页面中收件人的加密ID。 要解密存储在外部帐户中的密码，请使用新 **decryptPassword** 函数。

对于现有客户，此函数的行为不会发生更改，但我们建议您使用 **decryptPassword** 而不是 **decryptString**. 的 **XtkSecurity_Unsafe_DecryptString** 兼容性选项由后端升级添加，默认情况下处于激活状态，允许您继续使用函数。 如果要停用 **decryptString**，取消激活选项。

decryptPassword

的 **decryptPassword** 函数。 它允许您解密存储在外部帐户中的密码。 请参阅 [JSAPI](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html) 文档以了解更多信息。

文件API

对于新安装，通过文件API访问文件夹的权限仅限于 **var**, **sftp** 和Adobe Campaign的临时文件夹。

对于现有客户，文件API无法再访问 **conf** 文件夹Adobe Campaign。 的 **XtkSecurity_Disable_JSFileSandboxing** 兼容性选项由后端升级添加，默认情况下会激活，以便您继续访问其他文件夹。 如果要限制对 **var**, **sftp** 和Adobe Campaign的临时文件夹，取消激活选项。

**修补程序**

* 修复了可能影响短信事务型消息性能的问题。 (NEO-9812)

## 18.4 版

### 18.4.5 版 - 内部版本 8937{#release-18-4-5-build-8937}

2018年11月21日

**改进**

* 修复了在FDA上使用MySQL运行工作流时的各种问题。 (NEO-11652)
* 修复了在特定情况下导致部分投放群体保持待定状态的问题。 (NEO-11336)
* 修复了短信自动响应的间歇性问题。 (NEO-11811)
* 修复了在投放中使用种子地址时的ID耗尽问题。 (NEO-11842)
* 修复了在扩充工作流活动中执行排序时的语法错误。 (NEO-11394)
* 修复了重新启动IIS时可能导致Web服务器崩溃的问题。 (NEO-10862)
* 修复了在升级内部版本(FDA - SQL)后可能导致跟踪工作流失败的问题。 (NEO-11635)
* 修复了可能导致工作流列表数据丢失的问题。 (NEO-11696)
* 修复了发送推送通知时的性能问题。 (NEO-11787)
* 修复了Web跟踪无法用于“com.au”域(NEO-4385)的问题。
* 修复了在使用复杂工作流时可能发生的客户端冻结问题。 (NEO-11847)
* 修复了在选择特定架构的元素后保存新投放时的Oracle错误(NEO-11682)。
* 修复了查询包含带重音符的字段(FDA/Teradata)时的问题。 现在，外部帐户允许您更改用于与Teradata驱动程序通信的编码。 (NEO-11818).
* 修复了在推送通知中以其他变量传递URL时可能导致移动设备应用程序收到格式错误或数据不正确的跟踪问题。 (NEO-11468、NEO-11960)
* 修复了在将值分布与1:N链接结合使用时导致显示问题的问题。 (NEO-11820)
* 修复了批量加载无法在Teradata16上工作的问题。
* 增加了Teradata上时间戳的缓冲大小，以避免15.10驱动程序出现绑定问题。
* 改进了对可能导致升级后问题的长名称索引的管理。
* 改进了子代死机处理(MTA)期间的共享内存可用时间。
* 修复了Apache（跟踪）中的潜在死锁。


### 18.4.4 版 - 内部版本 8936{#release-18-4-4-build-8936}

2018年8月1日

**改进**

* 电子邮件存档日志已得到增强，这使得检查哪些电子邮件已成功发送或通过密送存档失败变得更加容易和清晰。 (NEO-10675)
* 修复了导致在跟踪广播中显示负载平衡器IP而不是客户IP的问题。 (NEO-11295)
* 修复了使用FDA连接到PostgreSQL数据库时LATIN1编码错误。 (NEO-11299)
* 修复了在使用 **[!UICONTROL Prepare the personalization data with a workflow]** 投放选项。 (NEO-11047、NEO-11301)
* 修复了导致投放属性被错误覆盖的随机问题。 (NEO-11015)
* 修复了在 **[!UICONTROL Survey answers]** 工作流活动。 (NEO-11382)
* 修复了在 **[!UICONTROL Survey answers]** 工作流活动。 (NEO-10816)
* 修复了在版本8935中执行服务器升级时的问题。
* 修复了在升级后日志中显示无用错误的问题 **[!UICONTROL Survey answers]** 工作流活动未完全配置。
* FDATeradata:修复了SQL表中自动递增的字段和索引的问题。

### 18.4.3 版 - 内部版本 8935{#release-18-4-3-build-8935}

2018年6月22日

**改进**

* 修复了Microsoft Edge和Internet Explorer的跟踪编码问题。 (NEO-11257)
* 修复了LINE投放中图像链接个性化的问题。 (NEO-11077)
* 修复了ID序列生成机制无法正常工作的问题。 (NEO-11115)
* 修复了在使用具有整数类型协调键值的自定义命名空间时隐私(GDPR)请求无法工作的问题。 (NEO-11123)
* 修复了在使用 **[!UICONTROL Distribution of values]** 选项 **[!UICONTROL Query]** 工作流活动。 (NEO-10958)
* 修复了将选件空间从营销实例同步到交互实例时的问题。 (NEO-11162)
* 改进了升级后期间长名称索引的管理

### 18.4.2 版 - 内部版本 8932{#release-18-4-2-build-8932}

2018年5月22日

**改进**

* 修复了Windows Server更新无法正常工作的问题。
* 修复了 **[!UICONTROL Survey Result]** 活动。 报表显示不正确。 (NEO-10816)
* 修复了使用退回邮件服务器时inMail进程可能发生的性能问题。 (NEO-10641)
* 修复了在升级1000个以上架构时可能发生的数据库升级问题。

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
   <td> 欧盟《通用数据保护条例》(GDPR)<br /> </td> 
   <td> <p>GDPR是欧盟(EU)的新隐私法，旨在协调数据保护要求并使之现代化，于2018年5月25日正式生效。 GDPR 适用于所持有数据的数据主体位于欧盟的 Adobe Campaign 客户。</p> <p>除了Adobe Campaign中已有的可用隐私功能（包括同意管理、数据保留设置和用户角色）之外，我们还将利用我们作为数据处理者的角色提供的这一机会，加入其他功能，以帮助您作为数据控制者为某些GDPR请求做好准备：</p> 
    <ul> 
     <li> <p>访问权：允许数据主体接收其由数据控制者捕获的个人数据的副本，可能包括存储在Adobe Campaign中的数据。</p> </li> 
     <li> <p>删除权：授权数据主体擦除“数据控制者”捕获的个人数据，这可能包括存储在Adobe Campaign中的数据。</p> </li> 
    </ul> 有关更多信息，请参阅<a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">详细文档</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的用户档案<br /> </td> 
   <td> <p>Adobe Campaign现在提供活动用户档案的列表，通过专用工作流每月更新。</p> <p>有关更多信息，请参阅<a href="../../platform/using/about-profiles.md#active-profiles">详细文档</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> Android推送连接器增强功能<br /> </td> 
   <td> <p>Android连接器已得到增强，可支持更高的吞吐量。 </p> <p>有关更多信息，请参阅<a href="../../delivery/using/configuring-the-mobile-application.md">详细文档</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 现在禁用了外部实体的扩展，以防止未经身份验证的用户发生潜在攻击。 (NEO-10173)
* 强化了权限，以防止标准用户更改实例配置参数，如应用程序访问URL、LDAP设置等。 (NEO-10171)
* 修复了可能通过堆栈跟踪显示敏感信息的问题。 错误详细信息现在记录在后端到外部网络无法访问的位置。 (NEO-10176)
* 强化了权限，以防止标准用户查看管理员上传的文档和/或导出的包。 (NEO-10170)

**改进**

* **LINE渠道 — 架构增强**:与Adobe Campaign中的所有其他渠道一样，现在所有部署类型都支持LINE渠道：托管、混合和内部部署。
* **序列自动生成**:ID生成机制已得到增强，可增加具有大量对象的Campaign实例的有效期。

**其他变更**

* 新模式可用于使用命令行导入包，允许循环依赖项（对于大型包，不建议使用）。 有关更多信息，请参阅“技术演变”部分。 (NEO-8979)
* 改进了Teradata中大量数据加载的性能，并修复了阻止显示日志中处理数据的正确值的问题。 (NEO-10429)
* 现在，从Audience Manager导入受众可以处理拆分文件。 以前，只有区段的最后一个文件是由importSharedAudience技术工作流导入的。 (NEO-10156)
* 在Windows上，Campaign服务器默认安装路径已更改。 启动64位版本设置时，默认安装路径现在为： **C:\Program Files\Adobe\Adobe Campaign Classic v7** 而不是 **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 默认MX规则已得到增强，可包含更多域并优化吞吐量。
* 对部署向导SOAP调用(xtk:serverOptions#SaveOptions)强制实施访问限制。
* 已删除weka.jar过时库，并更新OpenSSL库以进行安全优化。
* 改进了计费技术工作流以保护实例性能。
* 恢复了管理员设置或重置任何操作员密码的功能。 要执行此操作，请右键单击运算符，选择 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 并设置操作员的新密码。 我们建议操作员在首次重新连接时更改其密码。 有关更多信息，请参阅[详细文档](../../production/using/lost-password.md)。
* 为了支持Adobe Target中新增的多租户功能，现在在配置与Target集成的选项和外部帐户时，可以向URL中添加新的“at_property”参数。 可在Adobe Target中找到用于此参数的值，该值将在调用Target时由Campaign使用。 有关更多信息，请参阅[详细文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 现在，您可以指定在单击Adobe Target提供的图像时要打开的默认登录页面。 以前，单击该图像会导致在创建电子邮件时设置默认图像。 有关更多信息，请参阅[详细文档](../../integrations/using/inserting-a-dynamic-image.md)。
* 添加了 **启用SMPP跟踪** 复选框以强制跟踪输出。 有关更多信息，请参阅[详细文档](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)。

**技术演进**

queryDef

已针对“orderBy”子句修改queryDef。 在更改之前，查询表的主键将隐式添加到“orderBy”子句中。 在某些数据库引擎（至少是postgresql）上，它会阻止使用索引（orderBy子句的所有字段都必须由同一索引覆盖）。 如果您依赖于此行为，则必须在“orderBy”子句中显式添加主键。

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

在18.4号变更之前，它将被隐式地递交为：

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

对于非ASCII字符，“urlEncode” JavaScript函数无法正常工作。 已更正该字符，现在应该可以处理所有Unicode字符（包括日语字符）。 如果您依赖非ASCII字符的“urlEncode”行为，则必须调整您的代码。

包导入新模式

新模式可用于使用命令行导入包，允许循环依赖项（对于大型包，不建议使用）。 现有功能会保留。 对于具有循环依赖关系的此类包，将添加一个新标记 **-usejs** 已添加到命令行包导入中。 执行时，将像从界面执行包导入时一样使用JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修补程序**

* 修复了从Adobe Campaign Standard复制投放和跟踪日志到Adobe Campaign Classic时的同步问题。 (NEO-10023)
* 修复了在快速加载操作失败后恢复ETL工作流时，处理Teradata中的错误和日志表时出现的问题。 现在，每次工作流继续时，错误和日志表都会被正确删除。 (NEO-10672)
* 修复了在安装FDA包时自动安装Hive包(Hadoop需要)的升级后问题。 (NEO-10592)
* 修复了将无效域视为 **未定义** 错误。 (NEO-10248)
* 修复了发送Android推送投放时，deliveryLogStats表中的日志重复的问题。 (NEO-10234)
* 修复了可能导致条形码扫描仪无法读取某些条形码格式的问题。 (NEO-10125)
* 修复了使用非ASCII字符时“urlEncode” JavaScript函数的问题。 有关更多信息，请参阅“技术演变”部分。 (NEO-10123)
* 修复了在Teradata库上执行包含sha256函数的查询时的问题。 (NEO-10119)
* 修复了在使用非常大的SalesForce表时，SalesForce活动中可能发生的工作流内存错误。 (NEO-9900)
* 修复了 **生成补码** 选项来定位工作流活动。 (NEO-9878)
* 修复了可能导致 **已处理** 和 **成功** 使用中间源时，量度不会在营销实例上更新。 (NEO-9454)
* 修复了在平台中总选件超过10k时的交互非重命题规则(NEO-9352)
* 修复了在使用XML外部文件时可能无法指定投放目标的问题。 (NEO-9312)
* 修复了在选件上运行假设并更新建议状态时可能导致工作流错误的问题。 (NEO-9304)
* 修复了基于Android投放映射的属性使用压力规则时在投放分析期间出现的错误。 (NEO-9202)
* 修复了对收件人列表中的列进行排序时可能导致性能问题的问题。 有关queryDef修改的更多信息，请参阅下面的“技术演变”部分。 (NEO-9042)
* 修复了批准电子邮件中的链接可能指向错误的登录URL的问题，尤其是在使用Federated ID登录类型时。 (NEO-9011)
* 修复了可能导致某些时区的报表日期选取器中显示错误日期的问题。 (NEO-9007)
* 修复了使用FDA SQL数据库时无法查看出站目标的问题。 (NEO-8924)
* 修复了导致MS Dynamics CRM连接器无法提取每月前7天数据的问题。 (NEO-8803)
* 修复了Analytics集成中阻止用户包含国际字符的错误。 (NEO-8719)
* 修复了在没有适当权限的情况下可以启用工作流编辑的问题。 (NEO-8708)
* 修复了在混合架构中使用消息中心时，通过HTTP进行联合数据访问导致连接丢失或连接丢失（超时）的问题。 (NEO-8438)
* 修复了负ID的增量查询活动中发生的工作流错误。 (NEO-8229)
* 修复了可能导致在某些屏幕中显示双滚动条的问题。 (NEO-8208)
* 修复了在运行更新数据库结构向导时导致显示错误消息的问题。 PostUpgrade将执行名称超过30的索引的重命名。 请注意，对于大型表，替换索引将需要时间。 (NEO-7983)
* 修复了跟踪日志无法从消息中心执行实例正确同步以控制实例的问题。 (NEO-7286)
* 修复了选件扩充活动的性能问题。 (NEO-7263)
* 修复了在通过FDA查询Redshift数据库时无法使用DaysAgo函数的问题。 (NEO-7099)
* 修复了数据管理中阻止在扩充类工作流活动上创建索引的回归。
* 修复了在使用标题创建外部资源时可能发生的@id问题
* 修复了在通过FTP服务器上传压缩文件或在文件名中上传带通配符的文件时可能发生的问题。
* 修复了在创建到Campaign Standard的外部自定义资源中较长的基类型枚举的问题。
* 修复了即使与提供商的连接失败也可能导致短信丢失的问题。
* 修复了导致SMTP连接无限期卡住的错误。
* 修复了在使用LINE映射或筛选和定位架构不同时在消息准备期间压力分类规则存在的问题。
