---
product: campaign
title: '"[!DNL Gold Standard] 版本"'
description: Campaign Classic  [!DNL Gold Standard] 的发行说明和兼容性矩阵
feature: Overview
role: User
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: 7f24c8be599d6dece41de848d64feb8079b10ff3
workflow-type: ht
source-wordcount: '1670'
ht-degree: 100%

---

# [!DNL Gold Standard] 版本{#gold-standard}

![](../../assets/v7-only.svg)

您可以在此页面中找到 [!DNL Gold Standard] 版本的发行说明和兼容性矩阵。

## [!DNL Gold Standard] 发行说明


### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] 12 版{#gs-12}

_2021 年 9 月 7 日_

版本 9032@554dbcd 包含以下修复：

* 修复了在启用跟踪的 Line 投放中打开指向 Web 应用程序的链接时导致出现 500 错误的问题。

_2021 年 8 月 27 日_

版本 9032@99a3894 包含以下修复：

* 跟踪签名功能已得到改进，以防止与第三方工具（电子邮件客户端、互联网浏览器等）链接的方式出现错误处理特殊字符。URL 参数现已经过编码。
* 修复了日期选取器的问题，该问题可能导致控制台显示阻止程序错误消息。(NEO-36345)

### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] 11 版{#gs-11}

_2021 年 4 月 14 日_

内部版本 9032@d030c36 包含以下修复：

* 修复了导致 IMS 连接屏幕上出现持续错误消息的客户端控制台回退问题。 (NEO-34821)
* 需要安装此控制台版本来保持 [IMS 访问](../../technotes/using/ims-updates.md)。

**必须执行仅控制台升级。无需升级服务器。**

>[!CAUTION]
>
> * 如果您要通过 Adobe Identity Management Service (IMS) 使用 Adobe ID 连接到 Campaign，则必须升级 Campaign 服务器和客户端控制台才能在 **2021 年 6 月 30 日**&#x200B;后连接到 Campaign。[了解详情](../../technotes/using/ims-updates.md)
> * 此版本附带[安全修复](https://helpx.adobe.com/cn/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。
> * 如果您是通过 oAuth 身份验证使用 Experience Cloud Triggers 集成，则需要按照[此页面](../../integrations/using/configuring-adobe-io.md)中的说明移至 Adobe I/O。Campaign 的旧版 oAuth 身份验证模式已于 **2021 年 9 月**[停用](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。托管环境的支持时间可延长至 **2022 年 2 月 23 日**。作为内部部署或混合型部署客户，请联系 Adobe 客户关怀团队，将支持延长至 2022 年 2 月。您必须向 Adobe 提供 [OAuth 应用程序的 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)。
>
>在[[!DNL Gold Standard] 本节](../../rn/using/gold-standard.md)中了解详情

_2021 年 3 月 2 日_

内部版本 9032@10c2709 包含以下修复：

* 修复了导致无法使用某些控制台组件（如投放中的日期选择器和图像管理）的回退问题。(NEO-31453, NEO-31454)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。

_2020 年 12 月 22 日_

内部版本 9032@d3b452f 包括以下改进和修复：

* 连接协议已经更新，以遵循新的 IMS 认证机制。

* 最初基于 oAUTH 身份验证设置来访问管道的 Triggers 集成身份验证现已更改并移至 Adobe I/O。[了解详情](../../integrations/using/configuring-adobe-io.md)

* [终止支持 iOS APN 旧版二进制协议](https://developer.apple.com/news/?id=c88acm2b)之后，在升级后期间，所有使用此协议的实例都更新为 HTTP/2 协议。

* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)

* 修复了在运行&#x200B;**扩充**&#x200B;活动时可能导致工作流失败的问题。(NEO-17338)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 10 版{#gs-10}

_2020 年 7 月 7 日_

内部版本 9032@efd8a94 包含以下修复：

修复了在禁用签名功能时跟踪无法正常工作的问题。(NEO-26411)

>[!CAUTION]
>
>我们建议您使用此版本中提供的客户端控制台进行升级。请参见[此页面](../../installation/using/installing-the-client-console.md)。

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 9 版{#gs-9}

_2020 年 6 月 22 日_

内部版本 9032@800be2e 包含以下修复：

* iOS HTTP2 连接器已得到改进（第三方更新和错误管理）。(NEO-25904、NEO-25903、NEO-25799)

以下修复与跟踪链接安全机制相关（在[安全和隐私核对清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html#signature-mechanism)中了解更多信息）：

* 修复了跟踪“通知点击量”无法正常工作的问题（iOS 和 Android 推送通知）。(NEO-25965)
* 修复了在使用某些旧版 Outlook 时可能导致无法打开/单击跟踪 URL 的问题。  (NEO-25688)
* 修复了在使用个性化参数（带井号的锚点标记）中的片段跟踪 URL 时无法正常工作的问题。(NEO-25774)
* 修复了反网络钓鱼服务的问题。(NEO-25283)
* 修复了使用特定自定义跟踪公式时的跟踪问题。(NEO-25277)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 8 版{#gs-8}

_2020 年 4 月 29 日_

内部版本 9032@3a9dc9c 包含以下修复：

* 改进了电子邮件中跟踪链接的安全性。默认情况下，所有客户都启用此功能。另外还提供了增强的安全功能，可通过联系客户服务中心来启用此功能。有关此功能及非托管客户启用此功能的步骤的更多详细信息，请参阅[安全和隐私检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html#signature-mechanism)。

>[!CAUTION]
>
>如果您在使用跟踪链接时遇到推送通知问题，或在使用锚点标记时遇到投放问题，建议您禁用跟踪链接的新签名机制。[此页面中](https://helpx.adobe.com/cn/campaign/kb/acc-security.html#signature-mechanism)对该过程进行了详述

* 修复了可能会导致图像无法在 Line 投放中显示的问题。(NEO-23207)
* 修复了&#x200B;**文件传输**&#x200B;活动的问题，该问题导致基于 SFTP 密钥的身份验证无法在 Debian 9 上工作。(NEO-23183)
* 修复了在以高频率发送时可能影响推送通知的问题。(NEO-20516)
* 修复了优惠响应管理中可能导致 Web 服务器崩溃的问题。(NEO-19482)
* 修复了 LibreOffice 管理中阻止导出报告的错误。(NEO-20982)
* 修复了使用调查活动升级大量工作流时导致错误的问题。
* 改进了 LibreOffice 管理，以避免使用 .odt 文件进行电子邮件预览失败。
* 改进了 Apache 连接的管理，以避免 Web 服务延迟。
* 改进了&#x200B;**关于**&#x200B;菜单中版本标记（7 位数）的显示。
* 修复了列表管理中阻止发布优惠的回归。
* 修复了导致清理工作流崩溃的回归。
* 修复了清理工作流日志中的次要回归。

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 6 版{#gs-6}

_2020 年 3 月 9 日_

内部版本 9032@19f73c5 包含以下修复：

* 修复了外部帐户使用 FTP over SSL 时的问题。(NEO-20498)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 5 版{#gs-5}

_2019 年 12 月 17 日_

内部版本 9032@d6b8062 包含以下修复：

* 修复了以下通信渠道上的跟踪问题：移动（SMS 或 MMS）、推送（iOS 或 Android）和社交网络（Facebook 或 Twitter）。(NEO-19595)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 4 版{#gs-4}

_2019 年 12 月 11 日_

内部版本 9032@bc4a935 包含以下修复：

* 修复了使用 MSSQL 数据库发送消息时的性能问题。(NEO-17558)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 3 版{#gs-3}

_2019 年 11 月 20 日_

内部版本 9032@3468c7b 包含以下修复：

* 修复了通过 IMS 身份验证进行登录的问题。(NEO-17312)
* 修复了在多个投放中显示累积报告时的问题。(NEO-18165)
* 修复了可能出现拦截或导致 Web 服务器崩溃的问题。

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 2 版{#gs-2}

_2019 年 9 月 19 日_

内部版本 9032@cee805c 包含以下修复：

* 修复了使用 CRM Connector for Salesforce 时的问题。(NEO-17712)
* 修复了在发送事务性消息时可能导致性能问题的索引问题。

### ![](assets/do-not-localize/red_2.png) 19.1.4 版 - 内部版本 9032{#release-19-1-4-build-9032}

_2019 年 8 月 13 日_

初始 19.1.4 内部版本包含以下修复：

* 修复了调度程序活动在向导配置期间生成不需要的错误消息的问题。NEO-11662 中的“还原更新”。(NEO-17097)
* 修复了 NEO-12727 引起的回归，该回归可能导致在执行两次测试活动时停止工作流。(NEO-16835)
* 修复了在 API 调用中使用无效或过期的会话令牌时导致返回错误的 HTTP 代码（HTTP 200 OK 而非 HTTP 403 Forbidden）的问题。(NEO-16826)
* 修复了 DKIM 密钥的问题，该密钥不再嵌入到电子邮件中，从而导致投放能力问题。(NEO-16804)
* 修复了工作流调度的各种问题。工作流已调度为每天执行一次，而不考虑调度程序配置。(NEO-16619, NEO-16426)


## [!DNL Gold Standard] 兼容性矩阵{#compatibility-matrix-gs}

本章节列出了 **Adobe Campaign Classic[!DNL Gold Standard]** 19.1 内部版本支持的所有系统和组件。此列表中未包含的产品和版本与此版本的 Adobe Campaign 不兼容。

>[!CAUTION]
>除非另有说明，否则支持所有次要版本。
>
>Adobe Campaign Classic 与本页中列出的所有系统和工具都兼容。随着这些第三方系统和工具的特定版本到达其各自创建者的终止生命周期 (EOL)，Adobe Campaign 将不再与这些版本兼容，并将在后续产品发布中从兼容性矩阵中移除。请确保您使用兼容性矩阵中列出的任何系统的受支持版本，以避免出现任何问题。

### 操作系统{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.X（64 位）</p>
<p>7.X（64 位）</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9（64 位）</p>
<p>8（64 位）</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.X（64 位）</p>
<p><strong>重要说明：</strong>如果您使用的是 RHEL，则必须愿意禁用 SELinux，或者让架构师编写自定义 SELinux 规则来检查已启用的 SELinux 是否不会导致 Campaign 操作问题。</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

### Web 服务器{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 on Windows Server 2016</p>
<p>8.5 on Windows Server 2012 R2</p>
<p>8.0 on Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7、Debian 8/9、Windows（64 位）</p>
<p>2.2 for RHEL6 - 仅限 CentOS 6（64 位）</p>
</td>
</tr>
</tbody>
</table>

### 工具{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java 开发工具包 (JDK)</td>
<td>
<p>8</p>
<p>该应用程序已被批准用于 Oracle 开发的 Java 开发工具包 (JDK) 以及用于 OpenJDK。</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6（和先前版本，如果嵌入在系统中）</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

### RDBMS 服务器{#RDBMSservers-gs}

>[!NOTE]
>
>RDBMS 驱动程序必须与 RDBMS 服务器版本匹配。

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>注意：您还可以将 Amazon RDS for PostgreSQL 与以上指定的版本配合使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 和 SP2</p>
<p>警告：当 Campaign 服务器在 Linux 上运行时，不支持将 Microsoft SQL Server 作为主数据库。</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>警告：新安装不允许使用 DB2 UDB。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL 是托管环境的默认数据库服务器。

### CRM 连接器{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce 连接器 API</td>
<td>
<p>API V37</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API V21</p>
<p>API V15</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap API - 本地：2007、2015、2016</p>
<p>Soap API - 在线：2015、2016</p>
<p>Web API - 本地版和联机版：365、2016、2016 Update 1</p>
</td>
</tr>
</tbody>
</table>

### 联合数据访问 (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 和 SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>V1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop（通过 HiveSQL）</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>

### 客户端控制台 {#ClientConsoleoperatingsystems}

:warning:警告：要使用 Campaign 客户端控制台，必须配备以下操作系统和浏览器。

#### 操作系统

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10（建议用于日语实例）</p>
</td>
</tr>
</tbody>
</table>

#### 浏览器

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### 移动 SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x、8.x、9.0</p>
<p>带有移动 SDK 内部版本 1.0.27。</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>带有移动 SDK 内部版本 1.0.26，与 32 位和 64 位版本兼容。</p>
</td>
</tr>
</tbody>
</table>

### 浏览器{#Browsers}

以下浏览器与 Campaign 兼容，可用于进行 Web 访问。

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
