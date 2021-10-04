---
product: campaign
title: Campaign Classic 已弃用和已移除的功能
description: 本页列出了 Adobe Campaign Classic 中已弃用并移除的功能
feature: Overview
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 98%

---

# 已弃用和已移除的功能 {#deprecated-and-removed-features}

![](../../assets/v7-only.svg)

Adobe 不断评估产品功能，以确定应用更现代的功能替换的旧功能，从而提高客户获得的整体价值，并且我们始终不断仔细考量向后兼容性。由于 Adobe Campaign Classic 可与第三方工具配合使用，所以会定期更新产品兼容性，以仅实施所支持的版本。下面和[兼容性矩阵](../../rn/using/compatibility-matrix.md)中列出了不再与 Adobe Campaign Classic 兼容的版本。

要传达即将移除/替换的 Campaign Classic 功能，请应用以下规则：

* 首先宣布弃用。尽管已弃用的功能仍然可用并且支持现有用户，但是它们不会得到进一步增强或记录。
* 至少将在以下版本中移除已弃用的功能。本页会宣布实际的目标移除日期。

此过程为客户提供了至少一个版本周期，以在实际移除之前，使其实施适应已弃用功能的新版本或后继版本。

>[!NOTE]
>Adobe Campaign 版本和新功能列在[发行说明中](../../rn/using/latest-release.md)。

## 已弃用的功能 {#deprecated-features}

本部分列出最新 Campaign Classic 版本中标记为已弃用的特性和功能。

通常，计划在将来版本中移除的功能会首先设置为已弃用。这些特性和功能不再向新 Campaign Classic 客户提供，也不应用于任何新实施。它们也会从产品文档中移除。

建议客户检查他们是否在当前部署中利用了这些特性/功能，并制定计划来更改其实施。请参阅目标移除日期，以相应地规划环境和项目更新。

<table> 
 <tbody> 
   <tr>
   <td><strong>功能</strong></td>
   <td><strong>替换</strong></td>
  </tr>
    <tr>
  <td>Adobe Analytics Data Connector<br></td>
   <td><p>从 Campaign 21.1.3 版本开始，弃用 Adobe Analytics Data Connector。</p>
   <p>如果您使用的是此连接器，则需要相应地调整实施。<a href="../../platform/using/adobe-analytics-connector.md">了解详情</a></p>
  <p><em>目标移除日期：2022 年 3 月 1 日</em></p>
  </td>
 </tr>
    <tr>
  <td>技术可投放性监视报告<br></td>
   <td><p>从 Campaign 21.1 版本开始，弃用了“技术可投放性监视报告”功能。</p>
   <p>如果需要，您仍可以每天通过电子邮件接收此报告，直到功能被移除的那天。如需申请，请打开一个具体的<a href="https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">支持案例</a>，并指明实例的名称和用于接收报告的电子邮件地址。</p> 
   <p>Adobe 建议您与投放评估团队合作，以确定用于监测实例投放性能的理想工具。</p>
  <p><em>目标移除日期：2021 年底</em></p>
  </td>
 </tr>
  <tr>
  <td>Oauth 身份验证（OAuth 和 JWT）<br></td>
  <td><p> 从 Campaign 20.3 版本开始，最初基于 oAUTH 身份验证设置来访问管道的 Triggers 集成身份验证现已更改并移至 Adobe I/O。 <p>
  <p>如果您使用的是 Triggers 集成，则需要相应地调整实施。<a href="../../integrations/using/configuring-adobe-io.md">了解详情</a></p> 
  <p>有关 Oauth 身份验证折旧的详细信息，请参阅此<a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">页面</a></p> 
  <p><em>目标删除日期：2021 年 11 月</em></p>
  </td>
  </tr>
 </tbody> 
</table>

## 移除的功能 {#removed-features}

本部分列出从 Campaign Classic 中移除的特性和功能。

<table> 
 <tbody>
  <tr> 
   <td><strong>区域 - 功能</strong></td>
   <td><strong>替换</strong></td> 
  </tr>
  <tr>  
   <td>报告<br></td>
   <td><p>在 Adobe Flash Player 生命周期结束后，量规报告和图表渲染引擎不再可用。<a href="../../reporting/using/creating-a-new-report.md">了解详情</a></p>
  </tr>
  <tr>  
   <td>传真渠道<br></td>
   <td><p>从 Campaign 21.1.3 版本开始，不再使用传真渠道。<a href="../../delivery/using/steps-about-delivery-creation-steps.md">了解详情</a></p>
  </tr>
  <tr>
  <td>Demdex 域<br></td>
  <td><p> 从 Campaign 21.1.3 版本开始，不再使用用于将受众导入和导出到 Adobe Experience Cloud 的 demdex 域。<a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">了解详情</a></p> 
  </td>
  </tr>
   <tr> 
   <td>Windows NT 身份验证<br></td>
   <td><p>从 Campaign 20.3 版本开始，在使用 Microsoft SQL Server 配置新数据库时，已从可用的身份验证方法中删除 Windows NT 身份验证。<a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">了解详情</a></p></td>
  </tr>
   <tr> 
   <td>基于文件的电子邮件存档<br></td>
   <td><p>从 Campaign 20.2 版本开始，基于文件的电子邮件存档不再可用。电子邮件存档现在可通过专用的密送电子邮件地址进行。<a href="../../installation/using/email-archiving.md">了解详情</a></p></td>
  </tr> 
   <tr> 
   <td>商机管理</td>
   <td><p>从 Campaign 20.2 本开始，商机管理包不再可用。类似的功能可以通过其他本机工作流活动和数据模型修改来实现。</p></td>
   </tr>
   <tr>
   <td>Campaign API 文档 - jsapi.chm 文件</td>
   <td>从 Campaign 19.1 版本开始，Campaign Classic API 在专用页面中提供。如果您使用的是旧版 jsapi.chm 文件，您现在应该参考 <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">新的在线版本</a>。</td>
  </tr> 
  <tr> 
   <td>活动编排 - 预测营销</td>
   <td>从 Campaign 18.10 版本开始，将不再提供预测营销功能。</td>
  </tr> 
  <tr> 
   <td>Web 应用程序 - 微型站点</td>
   <td>从 Campaign 18.10 版本开始，不再提供微型站点。您可以通过限制仅访问 Adobe Campaign 配置文件上的专用域来提高安全性，并通过使用 DNS 别名在 Campaign 中使用个性化 URL。</td>
  </tr> 
  <tr> 
   <td>推送通知 - iOS 二进制连接器</td>
   <td>根据 Apple 的建议，从 Campaign 18.10 版本开始，Adobe 将移除旧版 iOS 二进制连接器。功能更强、效率更高的基于 HTTP/2 的连接器现已可用。</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>从 Campaign 18.6 版本开始，出于安全原因，<em>decryptString</em> API 在默认情况下不再可用于新安装。</p> 
   <p>在之后升级到 18.6（及更高版本）的上下文中，此 API 不再激活，并由 <em>decryptPassword</em> 函数替换。<a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">了解详情</a></p></td>
  </tr> 
   <tr> 
   <td>移动渠道 - MMS 和 WAP 推送消息</td>
   <td>从 Campaign 18.4 版本开始，不再提供 MMS 和 Wap Push 渠道。作为替代，您可以利用 <a href="../../delivery/using/sms-channel.md">短信 (SMS) </a>和<a href="../../delivery/using/about-mobile-app-channel.md">推送</a>来发送投放。</td>
  </tr> 
   <tr> 
   <td>移动手机渠道 - LINE v1</td>
   <td>从 Campaign 18.4 版本开始，LINE Connect 包不再可用。Adobe 建议使用新的 LINE 渠道包作为替换。<a href="../../delivery/using/line-channel.md">了解详情</a></td>
  </tr>
 </tbody> 
</table>

## 已弃用的兼容性 {#deprecated-compatibility}

Campaign Classic 不再支持以下操作系统。请参阅[兼容性矩阵](../../rn/using/compatibility-matrix.md)，以在兼容性终止之前升级到新版本或迁移到新系统。

### Adobe Campaign 20.2 版  {#compat-20-2-release}

从 20.2 版本开始，弃用旧版 SMS 连接器。请参阅[已弃用的功能](#deprecated-features)部分

## 兼容性终止 {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic 与[兼容性矩阵](../../rn/using/compatibility-matrix.md)中列出的所有系统和工具兼容。当这些第三方系统和工具的特定版本由其各自创建者终止生命周期 (EOL) 时，Adobe Campaign 不再与这些版本兼容：它们将被宣布为已弃用，然后从后续产品发行版的兼容性矩阵中移除。请确保您使用兼容性矩阵中列出的任何系统的受支持版本，以避免出现任何问题。

### 客户端控制台 {#client-console-eol}

Adobe Campaign Classic 客户端控制台无法再在以下系统上运行，因为其编辑者已弃用它们。在其中某个版本上运行 Campaign 客户端控制台的客户需要在目标移除日期之前升级到最新版本。请参阅[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

* Windows Server 2003、2008、2008 R2
* Windows 7、XP、Vista

>[!NOTE]
>从 Campaign 20.1版本开始，Campaign Classic 客户端控制台 32 位不再与 Campaign 最新版本兼容。您需要使用 64 位客户端控制台。

### 操作系统 {#o-s-eol}

从 21.1.3 版本开始，弃用对 Debian 8 的支持。

从 19.1 版本开始，Adobe Campaign 不再与以下操作系统兼容。

* CentOS 6 [了解详情](https://wiki.centos.org/Download)
* Debian 7。[了解详情](https://wiki.debian.org/DebianReleases)
* RHEL 6.x。[了解详情](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008。[了解详情](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11。[了解详情](https://www.suse.com/lifecycle)

### Web 服务器 {#web-server-eol}

从 19.1 Spring Release 开始，Adobe Campaign 不再与以下 Web 服务器兼容。

* Apache 2.2。[了解详情](https://httpd.apache.org/)
* Microsoft IIS 7。[了解详情](https://support.microsoft.com/en-us/lifecycle/search/810)

### 工具 {#tools-eol}

从 19.1 Spring Release 开始，Adobe Campaign 不再与以下工具兼容。

* Java JDK 7。[了解详情](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x，嵌入到其他工具中时除外。[了解详情](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### 数据库引擎 {#dbe-eol}

Adobe 不支持以下数据库引擎，因为其编辑者已弃用它们。运行这些版本的客户需要升级到最新版本或迁移到另一个版本。

请参阅 [Campaign 兼容性矩阵](../../rn/using/compatibility-matrix.md)，访问兼容版本的列表。

**联合数据访问 (FDA)**

从 20.2 版本开始，Adobe Campaign 不再与以下 FDA 服务器兼容：

* DB2 UDB 10.5

从 19.1 Spring 版本开始，Adobe Campaign 不再与以下 FDA 服务器兼容：

* PostgreSQL 9.3。[了解详情](https://www.postgresql.org/support/versioning)
* MySQL 5.5。[了解详情](https://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5。[了解详情](https://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 – 14.1。[了解详情](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic 与以下联合数据访问 (FDA) 服务器不兼容。

* DB2 UDB 9.5、9.7。通过联合数据访问 (FDA) 支持更新版本的 DB2。[了解详情](https://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i、10G R2。通过联合数据访问 (FDA) 支持更新版本的 Oracle。[了解详情](https://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3、8.4、9.0、9.1、9.2。通过联合数据访问 (FDA) 支持更新版本的 PostgreSQL。[了解详情](https://www.postgresql.org/support/versioning)
* MSSQL 2000、2005、2008 R2。通过联合数据访问 (FDA) 支持更新版本的 SQL Server。[了解详情](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1。通过联合数据访问 (FDA) 支持更新版本的 MySQL。[了解详情](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB 的生命周期已终止。[了解详情](https://www.mysql.com/support)
* Teradata 13、13.1。通过联合数据访问 (FDA) 支持更新版本的 Teradata。[了解详情](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02、7.0。Netezza 的生命周期已终止。[了解详情](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0。AsterData 的生命周期已终止。[了解详情](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2、15.4、15.5 和 Sybase ASE 15.0。通过联合数据访问 (FDA) 支持更新版本的 Sybase。[了解详情](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL：Hadoop 2.7.3、HiveSQL 1.2.1。Adobe Campaign Classic 仍通过联合数据访问 (FDA) 支持列出的 Hadoop via HiveSQL 版本，但这些版本与以下版本合并：HortonWorks (HDP 2.4.X、2.5.x、2.6.x）和 HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)

**RDBMS 服务器**

从 19.1 Spring 版本开始，Adobe Campaign 不再与以下 RDBMS 服务器兼容：

* Oracle 10GR2
* PostgreSQL 9.0 至 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

### SMS 连接器 {#sms-eol}

Adobe Campaign 与以下 SMS 连接器不兼容：

* 通用 SMPP（支持二进制模式的 SMPP 版本 3.4）
* Sybase365 (SAP SMS 365)
* CLX 通信
* Tele2
* O2
* iOS

### CRM 连接器 {#crm-connectors}

从 Campaign 21.1 版本开始，Campaign 弃用以下 CRM 连接器：

* Soap API - 本地：2007、2015、2016
* Soap API - 在线：2015、2016
* Web API – Microsoft Dynamics CRM  2016 版
* Web API - Microsoft Dynamics CRM 2016 版更新 1
* Oracle On Demand API
