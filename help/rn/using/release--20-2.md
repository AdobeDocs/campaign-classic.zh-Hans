---
solution: Campaign Classic
product: campaign
title: 版本 20.2
description: 版本 20.2
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
translation-type: tm+mt
source-git-commit: 571821ce775a7c354d01404d14faee8d2a21c170
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 94%

---


# 版本 20.2{#release-20-2}

![](assets/do-not-localize/cp-icon.png) **新控制面板 10 月版**，其中使用 CNAME 进行域配置并新增数据库监视功能。[了解详情](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/release-notes.html)。

## ![](assets/do-not-localize/green_2.png) 版本 20.2.4 - 版本 9187 {#release-20-2-4-build-9187}

_2020年12月22日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您是通过 Adobe Identity Service (IMS) 连接到 Campaign，则 Campaign 服务器和客户端控制台都必须进行升级，才能在&#x200B;**2021 年 3 月 31 日**&#x200B;之后连接到 Campaign。
> * 此版本附带[安全修复](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。
> * 如果您正通过身份验证使用Experience Cloud触发器集成，则需要按照本页](../../integrations/using/configuring-adobe-io.md)中的[说明移至Adobe I/O。 旧版 oAuth 身份验证模式将于 **2021 年 4 月 30 日**&#x200B;停用。



**改进**

* 连接协议已经更新，以遵循新的 IMS 认证机制。
* 触发最初基于oAUTH身份验证设置的集成身份验证已更改并移至Adobe I/O。[了解更多](../../integrations/using/configuring-adobe-io.md)
* [终止支持 iOS APN 旧版二进制协议](https://developer.apple.com/news/?id=c88acm2b)之后，在升级后期间，所有使用此协议的实例都更新为 HTTP/2 协议。
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)
* 修复了在连接错误后导致SMPP连接器停用的问题，防止发送其他SMS投放并导致性能问题。 (NEO-28609)
* 通过防止在清除表达式分析器时内存损坏，修复了服务器崩溃问题。(NEO-26856)
* 修复了在显示工作流中&#x200B;**拆分**&#x200B;活动的其余目标数据时导致服务器 崩溃的问题。
* 修复了在查询除&#x200B;**收件人** (nms:recipient) 以外的其他模式后尝试预览 SMS 消息时可能显示错误消息的问题。(NEO-27517)
* 修复了在发出具有主机名中明确定义的端口号的HTTPS连接请求时，调用失败并出现证书错误的问题。 (NEO-29146)
* 修复了POSIX线程管理中在营销实例上生成大核心转储文件的问题。 (NEO-28117, NEO-29281)
* 修复了在准备投放或重复投放预览时可能导致Web进程崩溃的问题。 (NEO-27790, NEO-27517)
* 修复了由非管理员操作员触发时导致投放或验证发送失败的问题。 (NEO-28597)

## ![](assets/do-not-localize/red_2.png) 版本 20.2.3 - 版本 9182 {#release-20-2-3-build-9182}

_2020 年 9 月 11 日_

* 修复了由于投放部分的单个错误函数造成内存过载而导致阻止投放准备的回归。(NEO-27346)
* 修复了在重新发布 Web 应用程序之前关闭 Apache 和 Web 服务器的升级后问题。(NEO-27155)
* 修复了由于选项卡的误解而导致跟踪 URL 变为可见的 HTML 模板管理回归。(NEO-25909)
* 修复了由于非托管数据源而导致数据库清理工作流可能失败的问题。(NEO-23160, NEO-23364)
* 清理工作流现在按 100 批而不是逐批清除过期列表。
* 修复了阻止修改外部帐户的内部名称的回归。(NEO-27323)
* 修复了在升级后期导致 nlserver 启动错误的回归（错误日志）。
* 改进了共享内存的更新管理。不再需要 20.2 中必需的其他步骤。

## ![](assets/do-not-localize/red_2.png) 版本 20.2.2 - 版本 9180 {#release-20-2-2-build-9180}

_2020 年 7 月 22 日_

* 修复了在禁用签名功能时跟踪无法正常工作的问题。(NEO-26411)
* 修复了导致在应当允许个性化域中的未签名链接时将其阻止的问题。(NEO-25210)
* 修复了在使用某些旧版 Outlook 时可能导致无法打开/单击跟踪 URL 的问题。  (NEO-25688)
* 修复了导致在电子邮件投放中错误定义镜像页面 URL 的问题（由于 ASCII 字符控制不当）。(NEO-26084)
* 修复了反网络钓鱼服务中的 URL 管理编码问题。(NEO-25283)
* 修复了在使用个性化参数（带井号的锚点标记）中的片段跟踪 URL 时无法正常工作的问题。(NEO-25774)
* 修复了使用特定自定义跟踪公式时的跟踪问题。(NEO-25277)
* 修复了跟踪“通知点击量”无法正常工作的问题（iOS 和 Android 推送通知）。(NEO-25965)
* 修复了由于工作流中的计算字段受影响而导致该工作流失败的回归。(NEO-25194)
* 修复了阻止动态创建 Web 跟踪 URL 正常工作的回归。(NEO-20999)
* 修复了现成投放报告在导出到 PDF 时似乎已截断的回归问题。(NEO-25757)
* 修复了部署向导中的崩溃问题。
* 修复了在升级后可能阻止优惠通知工作流正常工作的问题。
* iOS HTTP2 连接器已得到改进（第三方更新和错误管理）。(NEO-25904, NEO-25903)
* 更新了 catalina.properties 中的 jarToSkip 列表，以删除对不再使用的 jar 文件（iOS 通知）的引用。
* 修复了在升级后阻止投放准备的问题。
* 在切换到[新序列 ID 机制](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)后，所有更新收件人表的 Web 应用程序都会在升级后期间重新发布。
* 修复了投放内容中的潜在 XSS 漏洞。(NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **新的控制面板 6 月版本**，包含活动用户档案监测、子域投放能力审核和 GPG 密钥管理。[了解详情](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html)。

## ![](assets/do-not-localize/red_2.png) 版本 20.2.1 - 版本 9178 {#release-20-2-1-build-9178}

_2020 年 6 月 8 日_

**新增内容？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>支持表情符号</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>在 Campaign 中设计邮件时，您现在可以使用专用按钮在邮件正文中轻松插入表情符号。还可以在电子邮件主题行中添加这些表情符号。您可以自定义界面中可用表情符号的列表。</p>
    <p>有关添加表情符号的详细信息，请参阅 <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">详细文档</a>。在<a href="../../delivery/using/customizing-emoticon-list.md">本部分</a>中了解如何自定义表情符号列表。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA 连接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您现在可以将 Campaign 实例连接到 Azure Synapse 外部数据库。此连接通过新的外部帐户管理。</p>
    <p>Azure Synapse 仅适用于混合和内部部署环境。有关详细信息，请参阅<a href="../../installation/using/configure-fda-synapse.md">详细文档</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>泰国和巴西隐私法</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>泰国的《个人数据保护法》(PDPA) 是一项新的隐私法，旨在协调泰国的数据保护要求并使之现代化。 </p>
   <p>巴西的《通用数据保护法》(LGPD) 将从 2021 年初生效，适用于巴西境内所有收集或处理个人数据的公司。</p>
   <p>这些法规适用于为居住在这些国家/地区的数据主体持有数据的 Adobe Campaign 客户。除了 Campaign 中已有的隐私权功能（包括同意管理、数据保留设置和用户角色），我们还将利用此机会加入其他功能，以帮助您做好 PDPA 和 LGPD 的准备：</p>
   <ul> 
     <li><p>访问权和删除权：我们正在努力利用为 GDPR 和 CCPA 添加的功能。<a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">阅读更多</a></p></li> 
     <li> <p>在使用 Campaign 接口或 API 创建隐私请求时，您现在可以选择<strong>法规</strong>类型：PDPA、LGPD、GDPR、CCPA。<a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">阅读更多</a>。</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 默认情况下，为所有客户启用了跟踪电子邮件中链接的安全性。另外还提供了增强的安全功能，可通过联系客户服务中心来启用此功能。有关此功能及非托管客户启用此功能的步骤的更多详细信息，请参阅[安全和隐私检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。(NEO-24232)

* 为了优化安全性，已通过 sha256 增强了用于生成文件名的 MD5 哈希算法，以用于公共文件上传。(NEO-17044)

* 为了增强针对 XSS 攻击的安全性，在执行镜像页面时禁用客户端脚本。(NEO-17987)

* 修复了阻止&#x200B;**隐私请求清理**&#x200B;技术工作流删除对帐数据的问题。(NEO-25168, NEO-21004)

* 修复了&#x200B;**文件传输**&#x200B;活动的问题，该问题导致基于 SFTP 密钥的身份验证无法在 Debian 9 上工作。(NEO-23183)

**兼容性增强**

Campaign 现在支持以下系统：
* 操作系统：Debian 10
* RDBMS：Oracle 18c 和 Oracle 19c
* FDA：Azure Synapse Analytics

请参阅 [Campaign 兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)了解详情。

**改进**

* 事务性消息已得到改进，可提供更好的用户体验。您现在可以取消发布事务性消息模板，这将从执行实例中删除它。[了解详情](../../message-center/using/template-unpublication.md)。

* 新选项可用于设置发送包含图像或附件的电子邮件时的限制。这些限制可以避免性能问题，这对于事务性消息尤为有用。[阅读更多](../../installation/using/configuring-campaign-options.md#delivery)

* 新的&#x200B;**在数据库中准备投放部分**&#x200B;选项允许直接在数据库中执行投放准备，这可以显著加快分析。此选项仅适用于特定配置。[了解详情](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)。(NEO-23886)

* Microsoft Dynamics 的 [CRM 连接器活动](../../workflow/using/crm-connector.md)的性能已得到改进。(NEO-13303, NEO-12710)

* 已增加共享内存版本。

   >[!WARNING]
   >
   >执行升级后，此改进需要执行额外的步骤。请参阅下面的&#x200B;**技术演变**&#x200B;部分。

* 清理工作流已得到增强。所有已删除工作流的孤立工作表现也由清理工作流自动删除。[了解详情](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances)。

* 使用 iOS HTTP2 连接器的 iOS 移动应用程序的证书现在将在发送推送通知之前经过验证，从而防止投放因证书过期而失败。

* HTTP 代理连接的管理已得到改进。[了解详情](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)。

* **[!UICONTROL Javascript Code]**&#x200B;和&#x200B;**[!UICONTROL Advanced Javascript Code]**&#x200B;工作流活动中新增可在达到限制后停止执行的选项。默认值为 1 小时。[了解详情](../../workflow/using/sql-code-and-javascript-code.md#javascript-code)。

**其他更改**

* 现已弃用传统 SMS 连接器。请参阅[已弃用的功能页](../../rn/using/deprecated-features.md)。

* 您不能再使用自己的 Litmus 帐户来配置和使用 Adobe Campaign 中的收件箱呈现。[了解详情](../../delivery/using/inbox-rendering.md)。

* 为了更好地区分视图和文件夹，视图名称的颜色已从深蓝色更改为深青色。[阅读更多](../../platform/using/access-management.md#about-views)

* Campaign Classic 现在可以连接到托管在英国、印度和加拿大地区的 Microsoft Dynamics CRM 帐户。这适用于 Office 365 和内部部署 (Dynamics 2015) 部署类型。

* Campaign 现在执行 TLS 验证来检查服务器的主机名是否与提供的证书中的主机名匹配。

* 投放和跟踪统计信息表现在为 SMS 渠道的每个投放显示一个条目，而不是每个投放收件人显示一个条目。

* 在日志文件中添加了一条错误消息，用于当下载的文件大于磁盘空间时警告用户。

* Snowflake 连接器现在提供以下功能：MonthsAgo、DaysAgoInt、ToDateTime、YearsAgo

**技术演进**

此新版本更新了共享内存，并需要执行其他步骤来进行升级。作为 Campaign 管理员，您需要删除内存区段。这些步骤是必需的，因为旧区段将阻止 nlserver/nlsrvmod 启动。

在 Windows 上，需要重新启动系统。

在 Debian/CentOs 上，需要删除共享内存。以下是步骤：

在升级之前，您需要执行以下步骤：

1. 如果 apache2（CentOS 上的 http2）服务正在运行，请停止该服务。
1. 如果 nlserver（旧版本为 nlserver6）服务正在运行，请停止该服务。

升级后：

1. 如果版本比当前版本旧，请使用 **ipcrm** 命令删除共享内存。
1. 启动 nlserver 服务（如果它正在运行）。
1. 启动 apache2 服务（如果它正在运行）。

下面是 Debian 的命令行：

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

[本页](../../configuration/using/additional-parameters.md#redirection-server-configuration)提供 Linux 的示例。

**修补程序**

* 修复了清理工作流日志中的次要回归。
* 修复了解析 WSDL 文件时工作流&#x200B;**加载 (SOAP)** 活动中的问题。
* 修复了使用&#x200B;**调查**&#x200B;活动升级多个工作流以高效处理大量工作流时导致错误的问题。
* 修复了处理来自增强型 MTA 的 inMail 邮件时的间歇性连接问题。(NEO-20380)
* 修复了在 HTML 中以 100% 宽度显示图像时，热点单击百分比无法正确显示的问题。(NEO-23203)
* 修复了导致投放的条件内容无法在热点单击报告中完全显示的问题。(NEO-18729)
* 修复了在恢复工作流以发送重复投放时跳过目标批准步骤的问题。(NEO-18166)
* 修复了在工作流中修复错误后，**重新启动邮件准备**&#x200B;按钮无法恢复投放的问题。(NEO-13488)
* 修复了在启动阶段的中间源模式下，目标包含的收件人为日语电子邮件格式时，可能导致投放失败的问题。(NEO-23846)
* 修复了 Snowflake 连接器的时区转换问题 (NEO-20105)
* 修复了外部帐户使用 FTP over SSL 时的问题。(NEO-20498)
* 修复了可能会导致图像无法在 Line 投放中显示的问题。(NEO-23207)
* 修复了在发布优惠时导致错误的问题。(NEO-23312)
* 修复了推送通知的问题，该问题导致即使证书已过期，测试连接也能在移动应用程序中工作。(NEO-22991)
* 修复了在以高频率发送时可能影响推送通知的问题。(NEO-20516)
* 修复了导致跟踪数据包含重复的问题，即使跟踪日志没有。(NEO-20040)
* 修复了在解决跟踪服务器通信失败后导致发送重复事务电子邮件的问题。(NEO-23640)
* 修复了从跟踪 URL 重定向时删除编码参数值的问题（影响日语字符）。(NEO-25637)
* 修复了在比较浮点数时查询无法工作的问题。(NEO-23243)
* 修复了在重新启动工作流后，**修改者**&#x200B;列内容无法显示的问题。(NEO-23035)
* 修复了从第二个容器下载日志时导致跟踪技术工作流失败的问题。(NEO-23159)
* 修复了在运行&#x200B;**扩充**&#x200B;活动时可能导致工作流失败的问题。(NEO-17338)
* 已向&#x200B;**重复数据删除**&#x200B;工作流活动中的&#x200B;**要保持的重复项**&#x200B;添加检查，以防输入空值或负值。
* 已从循环的活动删除&#x200B;**调度程序向导**，以避免提及小时和分钟数。只考虑日期。
* 修复了通过&#x200B;**脚本**&#x200B;工作流活动中的&#x200B;**由脚本计算**&#x200B;选项创建投放时，其他活动字段存在的一个问题。(NEO-20609)
* 修复了导致无法在数据库清理任务中删除幽灵工作流的问题。
* 修复了导致&#x200B;**计费（活动用户档案）**&#x200B;技术工作流失败的问题。(NEO-19777)
* 修复了使用 ACS 连接器功能时阻止连接到 Campaign Standard 实例的回归问题（FOH/FOH2 连接管理不正确）。(NEO-23433)
* 修复了导致无法在 Hadoop 表中多列的主键上创建模式扩展的问题。(NEO-17390)
* 修复了可能导致无法从 URL 加载 WSDL 文件的&#x200B;**加载 (SOAP)**&#x200B;活动中的一个问题。(NEO-16924)
* 修复了在负载平衡多个活动工作流服务器时，导致无法执行&#x200B;**无条件停止**&#x200B;的问题。(NEO-19556)
* 修复了导致清理工作流崩溃的回归。
* 修复了在执行实例上发布模板时可能发生的问题。
* 修复了可能阻止 collectPrivacyRequests 技术工作流运行的问题。(NEO-20513, NEO-25169)
* 修复了在升级到版本 9080 后尝试连接到 Audience Manager 时可能发生的问题。(NEO-20511, NEO-25167)
* 修复了以 PDF 或 XLS 格式导出报表时可能出现的问题。(NEO-20982、NEO-23493、NEO-23348)
* 修复了在发送投放列表后，将投放显示两次的问题。
* 修复了投放准备问题，该问题在将路由配置设置为通过中间源发送投放时可能发生。
* 修复了在单击 Line 邮件中的 Web 应用程序链接时可能显示错误邮件的问题。
* 修复了在运行清理工作流后删除&#x200B;**增量查询**&#x200B;活动历史记录的问题。
* 修复了创建中间源外部帐户时缺少 NmsMidSourcing_LastBroadLog_&lt;InternalName> 选项的问题。
* 修复了数据库连接上的导致 Web 服务器由于数据库编码问题而不断重新启动的回归问题。这可能会造成过度使用。(NEO-23264)
