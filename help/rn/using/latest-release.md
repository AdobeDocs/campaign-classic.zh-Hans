---
product: campaign
title: 最新版本
description: 最新Campaign Classicv7发行说明
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cbafd70f5b5e964256edad0ce2965f3ed4650500
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 88%

---

# 最新版本{#latest-release}

![](../../assets/v7-only.svg)

本页列出了 **最新Campaign Classicv7版本**. 每个新内部版本都带有一个状态，该状态以颜色实现。 进一步了解Campaign Classicv7在中的构建状态 [本页](rn-overview.md).

## 版本7.1(21.1)

>[!CAUTION]
>Campaign **[!UICONTROL Help > About...]** 菜单允许您检查 [版本号和内部版本号](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). 但请注意，对于本页中列出的9277到9343之间的所有内部版本，版本号显示为7.0，而不是7.1。

### ![](assets/do-not-localize/green_2.png) 21.1.4 版 - 版本 9343 {#release-21-1-4-build-9343}

_2021 年 10 月 8 日_

**补丁程序**

* 改进了内部版本9342中可用的计费工作流修复，该修复要求手动重新启动工作流才能应用该修复。 现在，升级后将自动重新启动工作流。

* 修复了在将 **Interaction** 模块与 [Power Booster](../../installation/using/power-booster-and-power-cluster.md) 选项结合使用时可能导致无法正确管理优惠的问题。(NEO-39263)

* 修复了在多中间源实例上使用多个 IP 关联时，在发送投放时出现的“在中间服务器 xxx 上未找到 IP 关联 xxx”错误。(NEO-37514)

### ![](assets/do-not-localize/orange_2.png) 21.1.4 版 - 版本 9342 {#release-21-1-4-build-9342}

_2021 年 9 月 7 日_

**安全性增强**

* 修复了一个安全问题，以加强针对目录遍历攻击的保护。(NEO-28547)

**改进**

* Flash 生命周期结束后，已从所有相关的 Campaign 功能和组件中删除，并替换为 HTML5。已删除&#x200B;**量规**&#x200B;类型的图表。(NEO-30330) [阅读更多](../../reporting/using/creating-a-chart.md)
* 现在，在 Windows 上安装客户端控制台时，安装程序会检查是否存在父注册表节点，如果缺少该节点，则会创建一个。这可防止在启动控制台时出现潜在问题。(NEO-34854)
* 跟踪签名功能已得到改进，以防止与第三方工具（电子邮件客户端、互联网浏览器等）链接的方式出现错误处理特殊字符。URL 参数现已经过编码。

**其他变更**

* 修复了21.1.3中引入的使用计费工作流新护栏的回归。 在错误实例上执行账单工作流，并尝试发送未生成的账单报表时崩溃。 您需要手动重新启动工作流以应用修复。
* 之前弃用的 Microsoft CRM 连接器（Office 365 和内部部署）已从界面中删除。[阅读更多](../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft)
* 迁移到 Tomcat 8 后，更新了 IIS 设置脚本以修复 IIS 集成问题。(NEO-31019)
* 在工作流过渡的 **View population** 窗口的“data”和“schema”选项卡中，数据源标识已得到改进。
* 以下架构中添加了缺少的数据库索引以防止出现数据库更新问题：xtk:rights、nms:dlvExclusion、nms:seedMember、nms:trackingUrl

**补丁程序**

* 修复了将优惠链接到投放时，导致“热门点击”报表无法工作的问题。(NEO-26295)
* 修复了&#x200B;**子工作流**&#x200B;活动在执行时未生成输出表的问题。(NEO-36242)
* 修复了将&#x200B;**描述性分析**&#x200B;报表导出为 PDF 时出现的各种问题。(NEO-25847)
* 修复了在使用外部邮件投放时可能导致投放失败的问题。(NEO-37435)
* 修复了使用 Web API 连接到 Microsoft CRM 时出现的错误。由于功能未受到影响，因此错误消息已删除。
* 修复了将中间服务器设置为跟踪服务器和营销服务器之间的中继时的跟踪日志重复数据删除问题。(NEO-36285)
* 修复了导致无法将保管库用作特定代码库的回归问题。
* 修复了传入过渡是来自 FDA 数据源时，导致无法在&#x200B;**扩充**&#x200B;工作流活动中使用变量的问题。
* 修复了一个可能导致电子邮件中的 URL 损坏的问题。

### ![](assets/do-not-localize/orange_2.png) 21.1.3 版 - 版本 9330 {#release-21-1-3-build-9330}

_2021 年 6 月 5 日_

**新增功能**


<table>
<thead>
<tr>
<th><strong>全新工作流活动：更改数据源</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>全新的<b>更改数据源</b>工作流活动允许您更改工作流工作表的数据源。这提高了跨不同数据源（FDA 和本地数据库）管理数据的灵活性。</p>
<p>在 Adobe Campaign 工作流中，使用工作（或临时）表管理数据。工作流执行时，工作表会在工作流活动之间共享数据。默认情况下，工作表会在与我们查询的数据源相同的数据库中创建。</p>
<p>有关详细信息，请参阅<a href="../../workflow/using/change-data-source.md">有详细说明的文档</a>。</p>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th><strong>与 Adobe Journey Orchestration 集成</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Journey Orchestration 与 Adobe Campaign Classic 之间的集成现已正式启用。它允许 Journey Orchestration 使用 Adobe Campaign Classic 事务性消息传递功能发送电子邮件、推送通知和短信。</p>
<p>Journey Orchestration 实例和 Campaign Classic 实例之间的连接是在预配置时通过 Adobe 来设置的。</p>
<p>有关更多信息，请参阅 <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=zh-Hans">Journey Orchestration 文档</a>。此<a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=zh-Hans">部分</a>中介绍了分步用例</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>LINE 渠道增强</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>已向 LINE 渠道添加以下改进：
</p>
<ul> 
<li><p>支持 LINE 视频消息类型</p></li>
<li><p>支持 LINE 合作伙伴注册 API</p></li>
<li><p>支持在出现 LINE 服务器端错误或网络超时的情况下重试消息发送</p></li>
</ul>
<p>有关更多信息，请参阅<a href="../../delivery/using/line-channel.md">有详细介绍的文档</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA 连接器</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>您现在可以将 Adobe Campaign Classic 实例连接到 Vertica 外部数据库。此连接通过新的外部帐户管理。</p>
<p>有关更多信息，请参阅<a href="../../installation/using/configure-fda-vertica.md">有详细介绍的文档</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google Big Query FDA 连接器</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>您现在可以将 Adobe Campaign Classic 实例连接到 Google Big Query 外部数据库。此连接通过新的外部帐户管理。
</p>
<p>有关更多信息，请参阅<a href="../../installation/using/configure-fda-google-big-query.md">有详细介绍的文档</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

**安全性增强**

* 现在，仅管理员用户可访问返回完整数据库连接详细信息的 **xtk:session#GetCnxInfo** API 方法。(NEO-27779)
* 在 CRM 相关的 JavaScript 文件中，已弃用的 decryptString 函数已替换为 decryptPassword 函数。
* 跟踪签名功能已得到改进，以降低第三方工具（电子邮件客户端、互联网浏览器、安全链接安全工具）修改跟踪链接时发生跟踪重定向错误的风险。
* 修复了在包含大写字符时，可能会导致跟踪 URL 无法正常工作的问题。跟踪 URL 签名机制现在区分大小写。(NEO-28414)

**兼容性更新**

Campaign 现在支持以下系统：
* Google Big Query FDA 连接器
* Vertica FDA 连接器
* PostgreSQL 13

在 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md)中了解详情。

**已弃用的功能**

* ODBC驱动程序现在直接与Adobe Campaign第三方安装。 安装驱动程序不再需要手动步骤。
* Google Big Query现在可用于托管部署。

[了解更多信息](../../installation/using/configure-fda.md)

**改进**

* 已对Microsoft Dynamics Connector Web API应用了以下关键修复：
   * 修复了在过滤条件包含查找字段时，可能导致从Microsoft CRM导入数据失败或无法工作的问题。
   * 修复了在由工作流触发的导入期间导致字符串类型字段的null值保存为Null而不是空值的问题。
   * 修复了使用Web API调用导致数据导入或导出出现以下错误的问题：&quot;无效的URI:URI方案太长”。
   * 修复了在从Microsoft Dynamics 365导入期间阻止导入查找字段数据的问题。

**其他变更**

* 添加了护栏，以仅允许[计费技术工作流](../../production/using/monitoring-processes.md#billing-report)在营销实例上运行。
* 适用于 Windows 的第三方 OpenSSL 已更新至 1.1.1h 版本。
* 在 Debian 包描述中，nlserver 已更改为 Adobe Campaign Classic 服务器。

**修补程序**

* 修复了在编辑会话超时以便在特定时间后注销用户时出现的问题，即用户在设定的时间后仍保持登录状态。
* 修复了投放显示为只读，但仍可以在投放属性中进行编辑的问题。
* 修复了在设计 Web 应用程序时导致编辑工具栏消失的错误。
* 修复了向电子邮件添加链接时，显示带有 Adobe Campaign Classic 标题的电子邮件文本版本的错误。(NEO-29211
* 使用 FDA 通过 HTTPs 连接时，**中间源（投放日志）** (defaultMidSourcingLog) 工作流在 **NmsMidSourcing_LogsPeriodHour** 选项设置的时间范围内停滞。这将导致无法使用发生在这个设定的时间范围之后的数据更新记录。(NEO-30833)
* 修复了执行消息中心同步工作流后出现的问题。每次将投放对象文件夹移动到自定义文件夹时，工作流都会将投放移回通用的&#x200B;**事务性消息历史记录**&#x200B;文件夹。(NEO-27445)
* 修复了在尝试显示&#x200B;**广播统计信息**、跟踪指标&#x200B;****&#x200B;和共享活动统计信息&#x200B;****&#x200B;报表时显示错误消息的问题。
* **Oracle On Demand** 工作流活动已在弃用 OracleCRM 连接器后从界面中删除。
* 修复了在每日重新启动工作流服务器 (wfserver) 模块后停止执行处理工作流的问题。(NEO-30047)
* 修复了导致 MX 管理文档无法更新的问题，该问题可能会对 IP 声誉造成负面影响。(NEO-29897)
* 修复了收到 SOAP 调用时导致 Web 进程崩溃的问题。(NEO-28796) (NEO-29600)
* 修复了导致 SAP HANA FDA 索引创建失败的问题。(NEO-29664)
* 修复了在执行包含标头的 SOAP 调用时，可能会使事务性消息处于&#x200B;**等待**&#x200B;状态的问题。(NEO-28737)
* 修复了使用 Teradata FDA 连接器时出现的问题：所有临时表都在集群的一个节点上创建，这最终会消耗整个后台处理空间并导致 Teradata 崩溃。现在，临时表会在许多节点上生成。(NEO-28230)
* 修复了使用 Web 应用程序时导致跟踪标记在 **nms:trackingURL** 架构中生成不正确的主键的问题。(NEO-27931)
* 对 ODBC 3.x 的兼容性已得到增强，以确保错误消息的准确性。
* 修复了在电子邮件投放中使用自定义内容模板时可能导致控制台崩溃的问题。(NEO-31547)
* 修复了由于连接速度缓慢或响应内容过大，Tomcat 无法发送有效响应的问题。
* 修复了从 PostgreSQL 数据库读取 UUID 时可能发生的问题。
* 修复了在搜索与优惠相关的建议数据时可能导致性能不良的问题。(NEO-27554)
* 修复了当 IMS 服务被激活但未响应时导致 Web 进程没有响应的问题。
* 修复了由于特定加入机制导致投放个性化失败，因此导致无法发送包含一组验证的投放的问题。(NEO-14391)
* 修复了在查询和扩充活动以投放表为目标时，无法通过警报活动发送警报的问题。(NEO-25157)

### ![](assets/do-not-localize/red_2.png) 21.1.2 版 - 版本 9282 {#release-21-1-2-build-9282}

_2021 年 4 月 15 日_

* 为优化安全性，改进了密码管理。
* 修复了可能导致 MTA 崩溃的问题。

### ![](assets/do-not-localize/red_2.png) 21.1.1 版 - 版本 9277 {#release-21-1-1-build-9277}

_2021 年 2 月 22 日_

**安全性增强**

* 改进了控制台身份验证机制以优化安全性。 (NEO-26944)
* 修复了一个安全问题，加强了针对服务器端请求伪造 (SSRF) 问题的防护。(NEO-28532)

**兼容性更新**

Campaign 现在支持以下系统：

* 现在，使用 Salesforce CRM 外部帐户时支持 Salesforce API 版本 49。

**已弃用的功能**

**技术性投放能力监控**&#x200B;报告功能现已弃用。

在[已弃用和已删除的功能页面](../../rn/using/deprecated-features.md)中了解详情。

**改进**

**电子邮件反馈服务 (EFS)**&#x200B;是一种可扩展服务，它直接从增强 MTA 获取反馈，从而提高报告准确性。此功能作为专用测试版发布，并将在未来版本中逐步向所有客户提供。

* 现在可捕获所有类别的反馈，以实现完整且精确的报告。
* “已投放”指标的计算现在以来自增强 MTA 的实时反馈为基础，以提高准确性和反应性。
* EFS 通过同步软退信报告的方式解决了延迟问题。

有关更多信息，请参阅[有详细说明的文档](../../delivery/using/sending-with-enhanced-mta.md#efs)。
如果您有兴趣参与此私人测试版的试用，请填写此[表单](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)，我们将回复您。

**其他变更**

* 通过使用压缩方法，提高了大型跟踪日志的传输速度。
* 改进了工作流热图以避免在运行具有多个活动的工作流时发生超时 (NEO-27423)。
* 修复了即使优惠的结束日期已过，仍可能允许显示该优惠信息的问题。Campaign Classic 现在会考虑结束日期的整个时间戳，而不是只考虑日期。(NEO-27590)
* Google+ 链接已从&#x200B;**社交网络分享链接**&#x200B;个性化区块中移除。
* 修复了上个版本中实施错误修复后出现的问题。在使用 SSL/TLS 连接时增加了对主机名的检查，因而导致 SMS 投放失败。已对 POP3、SMS 和带代理的 HTTP 等大多数协议禁用主机名验证，并且 SMS 外部帐户的证书校验已改进为提供三个值 (NEO-29581)。[了解详情](../../delivery/using/sms-protocol.md#skip-tls)

**修补程序**

* 修复了导致 Tab 键、Enter 键和 Esc 键盘快捷键无法在新登录屏幕上使用的问题。
* 修复了导致新创建的工作流的名称在保存后被替换为默认值的刷新问题 (NEO-26106)。
* 修复了运行工作流时，在进行使用&#x200B;**外部文件**&#x200B;目标映射的&#x200B;**投放**&#x200B;活动之前，将新字段添加为&#x200B;**扩充**&#x200B;活动的一部分时发生的问题：不需要的字段被添加至&#x200B;**外部文件**&#x200B;目标映射。(NEO-27687)
* 修复了重新打开之前创建和保存的 Web 应用程序时，会导致源代码中的部分字符发生更改的问题。(NEO-27597)
* 修复了升级到包含用于跟踪链接的新签名机制的内部版本时可能发生的问题（从内部版本 19.1.4 和 Campaign 20.2）：当多个模板与某个事件关联时，升级可能会导致在发送事务性消息时选择错误的模板。(NEO-28326)
* 修复了导致 MTA 无响应并且无法处理投放（除非重新启动）的问题。(NEO-27455)
* 修复了在对日期时间类型列执行批量加载操作时与时间戳管理相关的 MSSQL 数据库问题。
* 修复了使用 Redshift xtk 函数时的工作流查询问题。SubDays、SubSeconds、SubMinutes 和 SubHours 现在接受两种 Redshift 时间戳类型 (NEO-24962)。
* 修复了尝试以匿名访问方式预览报告时会显示脚本错误消息的问题。(NEO-27081)
* 修复了在执行投放分析时，可能会减少服务器内存使用的问题。
* 修复了在尝试运行特定的复杂查询时，可能会阻止实例工作的问题。
* 修复了可能会阻止&#x200B;**同步 Twitter 页面**&#x200B;技术工作流运行的问题。(NEO-28634)
* 修复了尝试使用 **Tweet (twitter)** 投放模板在 Twitter 上发布时，可能会显示与 decryptPassword 函数相关的错误消息的问题。(NEO-28216)
* 修复了在工作流中使用 **Javascript** 活动发出 HTTP 请求时出现的问题。在主机名称中定义端口号后，调用会失败，并出现以下错误 (NEO-29146)：

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* 修复了导致无法发送带有目标数据个性化设置的新投放的问题 (NEO-30323)。
* 修复了营销实例中发生多次崩溃时导致核心文件出现的问题。
* 修复了会导致&#x200B;**跟踪**&#x200B;工作流失败并出现以下错误 (NEO-25206) 的问题：

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* 修复了在营销活动的 **Targeting &amp; Workflow（定位和工作流）**&#x200B;选项卡中创建和保存投放时发生的问题：预览会失败，并出现以下错误 (NEO-29440)：

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* 修复了在营销实例与 Adobe Campaign Standard 实例或 Campaign Classic 中间源实例之间设置外部帐户并使用选项“DisableFOH2=1”时发生的错误。当在外部帐户中使用“DisableFOH2=1”选项时，连接未正确关闭，并会堆积导致以下错误 (NEO-26258)：

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* 修复了服务器和提供商之间发生连接问题时 SMS 出现的错误。之后，MTA 子项将自动禁用连接。只要尚未启动新子项，Adobe Campaign Classic 就不会尝试连接到此失败的连接。
