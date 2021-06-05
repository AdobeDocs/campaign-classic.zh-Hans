---
product: campaign
title: 最新版本
description: 最新 Campaign Classic 发行说明
feature: 概述
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 28083eb0271c8c148955fa33978479dc3683eaed
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 52%

---

# 最新版本{#latest-release}

此页面列出了&#x200B;**最新 Campaign Classic 发行候选版本**&#x200B;随附的新功能、改进和修复。

>[!NOTE]
>
>Campaign **正式发布 (GA) 内部版本**&#x200B;为：[[!DNL Gold Standard]  11 版](../../rn/using/gold-standard.md#gs-11)和 [Campaign 20.2.5 版](../../rn/using/release--20-2.md)。

## ![](assets/do-not-localize/blue_2.png) 21.1.3 版 - 内部版本 9330 {#release-21-1-3-build-9330}

_2021年6月5日_

**新增功能**

<table>
<thead>
<tr>
<th><strong>与Adobe集成Journey Orchestration</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Journey Orchestration与Adobe Campaign Classic之间的集成现已正式启用。 它允许Journey Orchestration使用Adobe Campaign Classic事务型消息传送功能发送电子邮件、推送通知和短信。</p>
<p>Journey Orchestration实例和Campaign Classic实例之间的连接是在预配时通过Adobe来设置的。</p>
<p>有关更多信息，请参阅<a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html">Journey Orchestration文档</a>。 此<a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html">部分</a>中提供了分步使用案例</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>LINE渠道增强功能</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>已向LINE渠道添加以下改进：
</p>
<ul> 
<li><p>支持LINE视频消息类型</p></li>
<li><p>支持LINE合作伙伴注册API</p></li>
<li><p>支持在出现LINE服务器端错误或网络超时时重试发送消息</p></li>
</ul>
<p>有关更多信息，请参阅<a href="../../delivery/using/line-channel.md">详细文档</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA连接器</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>您现在可以将Adobe Campaign Classic实例连接到Vertica外部数据库。 此连接通过新的外部帐户管理。</p>
<p>有关更多信息，请参阅<a href="../../installation/using/configure-fda-vertica.md">详细文档</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google Big Query FDA连接器</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>您现在可以将Adobe Campaign Classic实例连接到Google Big Query外部数据库。 此连接通过新的外部帐户管理。
</p>
<p>有关更多信息，请参阅<a href="../../installation/using/configure-fda-google-big-query.md">详细文档</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

**安全性增强**

* 现在，对&#x200B;**xtk:session#GetCnxInfo**&#x200B;返回完整数据库连接详细信息的API方法的访问权限仅限于管理员用户。 (NEO-27779)
* 已弃用的decryptString函数在与CRM相关的JavaScript文件中替换为decryptPassword函数。
* 跟踪签名功能已得到改进，以在第三方工具（电子邮件客户端、Internet浏览器、安全链接安全工具）修改跟踪链接时降低跟踪重定向错误的风险。
* 修复了在包含大写字符时，可能会阻止跟踪的URL正常工作的问题。 跟踪的URL签名机制现在区分大小写。 (NEO-28414)

**兼容性更新**

Campaign 现在支持以下系统：
* Google Big Query FDA连接器
* Vertica FDA连接器
* PostgreSQL 13

在 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md)中了解详情。

**已弃用的功能**

* 从Campaign 21.1版本开始，弃用Adobe Analytics Data Connector。 如果您使用的是此连接器，则需要使用新连接器Adobe Analytics连接器相应地调整实施。
有关更多信息，请参阅[详细文档](../../platform/using/adobe-analytics-connector.md)。
* 现已弃用对Debian 8的支持。
* 在20.3中弃用OracleCRM后，已从界面中删除相关的外部帐户。

在[已弃用和已删除的功能页面](../../rn/using/deprecated-features.md)中了解详情。

**改进**

* 在保存工作流时，已添加额外的检查，以确保活动名称是唯一的，且过渡后始终有活动。
* **账单（帐单）**&#x200B;技术工作流现在包括最初由&#x200B;**活动账单用户档案数**(billingActiveContactCount)工作流执行的任务，该工作流已被删除。 工作流每月发送的电子邮件报表现在将提供有关实例上活动用户档案数的信息。 [阅读更多](../../workflow/using/about-technical-workflows.md)。
* 添加了新的&#x200B;**_keyOnMData**&#x200B;属性，以便能够对Memo数据使用键。

**其他变更**

* 适用于Windows的openssl第三方已更新至版本1.1.1h。
* 在Debian包描述中，nlserver已更改为Adobe Campaign Classic服务器。

**修补程序**

* 修复了在编辑会话超时时的问题，即使用户在设定的时间后仍保持登录状态，也会在特定时间段后注销用户。
* 修复了投放显示为只读，但仍可以在投放属性中进行编辑的问题。
* 修复了在设计Web应用程序时导致编辑工具栏消失的错误。
* 修复了在添加指向电子邮件的链接时显示带有Adobe Campaign Classic标题的电子邮件文本版本的错误。 (NEO-29211
* 使用HTTP上的FDA连接时， **中间源（投放日志）**(defaultMidSourcingLog)工作流在&#x200B;**NmsMidSourcing_LogsPeriodHour**&#x200B;选项设置的时间范围内卡住。 这将阻止记录使用此设置的时间范围后发生的数据进行更新。 (NEO-30833)
* 修复了执行消息中心同步工作流后发生的问题。 每次将投放对象文件夹移动到自定义文件夹时，工作流都会将投放移回通用的&#x200B;**Transactional message history**&#x200B;文件夹。 (NEO-27445)
* 修复了在尝试显示&#x200B;**广播统计信息**、**跟踪指示器**&#x200B;和&#x200B;**共享活动统计信息**&#x200B;报表时显示错误消息的问题。
* **Oracle按需**&#x200B;工作流活动已在弃用OracleCRM连接器后从界面中删除。
* 修复了在每日重新启动工作流服务器(wfserver)模块后停止执行处理工作流的问题。 (NEO-30047)
* 修复了MX管理文档无法更新的问题，该问题可能会对IP声誉造成负面影响。 (NEO-29897)
* 修复了在收到SOAP调用时导致Web进程崩溃的问题。 (NEO-28796)(NEO-29600)
* 修复了导致SAP HANAFDA索引创建失败的问题。 (NEO-29664)
* 修复了在执行包含标头的SOAP调用时，可能会将事务型消息保留为&#x200B;**Waiting**&#x200B;状态的问题。 (NEO-28737)
* 修复了使用TeradataFDA连接器时出现的问题：所有临时表都只在群集的一个节点上创建，这最终会消耗整个短管空间并导致Teradata崩溃。 现在，临时表在许多节点上生成。 (NEO-28230)
* 修复了在使用Web应用程序时导致跟踪标记在&#x200B;**nms:trackingURL**&#x200B;模式中生成不正确的主键的问题。 (NEO-27931)
* 与ODBC 3.x的兼容性已得到增强，可确保错误消息的准确性。
* 修复了在电子邮件投放中使用自定义内容模板时可能导致控制台崩溃的问题。 (NEO-31547)
* 修复了由于连接缓慢或响应大小过大，Tomcat无法发送有效响应的问题。
* 修复了从PostgreSQL数据库读取UUID时可能发生的问题。
* 修复了在搜索与选件关联的建议数据时可能导致性能问题的问题。 (NEO-27554)
* 修复了在激活IMS服务但未响应时导致Web进程未响应的问题。
* 修复了由于投放个性化失败的特定加入机制，阻止您发送包含一组校样的投放的问题。 (NEO-14391)
* 修复了在查询和扩充活动定向投放表时，无法通过警报活动发送警报的问题。 (NEO-25157)

## ![](assets/do-not-localize/red_2.png) 21.1.2 版 - 内部版本 9282 {#release-21-1-2-build-9282}

_2021 年 4 月 15 日_

* 为优化安全性，改进了密码管理。
* 修复了可能导致 MTA 崩溃的问题。

## ![](assets/do-not-localize/red_2.png) 21.1.1 版 - 内部版本 9277 {#release-21-1-1-build-9277}

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
