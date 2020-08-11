---
title: Campaign Classic已弃用和已删除的功能
description: 本页列表已弃用并删除了Adobe Campaign Classic的功能
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 63f07746d39fff22a98b3cd4ab7f2294da778ab3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 3%

---


# 已弃用和已删除的功能 {#deprecated-and-removed-features}

Adobe不断评估产品功能，以确定应用更现代的替代方案替换的旧功能，以提高整体客户价值，始终在仔细考虑向后兼容性的情况下。 在Adobe Campaign Classic使用第三方工具时，将定期更新兼容性，以便仅实施受支持的版本。 下面和兼容性矩阵中列出了不再与Adobe Campaign Classic兼容 [的版本](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

要传达即将拆除／替换Campaign Classic功能，请应用以下规则：

* 首先宣布弃用。 尽管已弃用的功能仍然可用并且支持现有用户，但是它们不会得到进一步增强或记录。
* 在以下版本中最早将删除已弃用的功能。 本页会宣布实际的删除目标日期。

此过程为客户提供了至少一个发布周期，以在实际删除之前，使其实施适应已弃用功能的新版本或后继版本。

>[!NOTE]
>Adobe Campaign版本和新功能列在发 [行说明中](../../rn/using/latest-release.md)。

## Deprecated features {#deprecated-features}

本节介绍最新列表版本中标记为已弃用的Campaign Classic特性和功能。

通常，计划在将来版本中删除的功能会首先设置为已弃用。 这些特性和功能不再适用于新Campaign Classic客户，也不应用于任何新实施。 它们也会从产品文档中删除。

建议客户检查他们是否在当前部署中利用了功能／功能，并制定计划来更改其实施。 请参阅目标删除日期，以相应地规划环境和项目更新。

<table> 
 <tbody> 
   <tr>
   <td><strong>功能</strong></td>
   <td><strong>替换</strong></td> 
  </tr>
   <tr>
  <td>SMS连接器<br></td>
  <td><p> 从20.2版本开始，已弃用以下SMS连接器。<p>
   <ul>
   <li>NetSize</li>
   <li>通用SMPP（支持二进制模式的SMPP版本3.4）</li>
   <li>Sybase365(SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>如果您使用其中一个连接器，您需要相应地调整实施。 <a href="../../delivery/using/sms-channel.md">了解更多</a></p> 
  <p>阅读此技术说明，了解如何迁移 <a href="https://helpx.adobe.com/campaign/kb/sms-connector.html">传统连接器</a>。</p>
  <p><em>目标删除日期：2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>传真渠道<br></td>
   <td><p>从20.2版本开始，已弃用传真渠道。</p> 
   <p>如果您使用此渠道，则需要相应地调整实施。 <a href="../../delivery/using/steps-about-delivery-creation-steps.md">进一步了解</a> 活动渠道。</p>
   <p><em>目标删除日期：2021</em></p></td>
  </tr>
 </tbody> 
</table>

## 删除的功能 {#removed-features}

本节列表已从Campaign Classic中删除的特性和功能。

<table> 
 <tbody> 
  <tr> 
   <td><strong>区域——功能</strong></td>
   <td><strong>替换</strong></td> 
  </tr> 
   <tr> 
   <td>基于文件的电子邮件存档<br></td>
   <td><p>从活动20.2版本开始，基于文件的电子邮件存档不再可用。 电子邮件存档现在可通过专用的密送电子邮件地址进行。 <a href="../../installation/using/email-archiving.md">了解更多</a></p></td>
  </tr> 
   <tr> 
   <td>潜在客户管理</td>
   <td><p>从活动20.2版本开始，销售线索管理包不再可用。 类似的功能可以通过其他本机工作流活动和数据模型修改来实现。</p></td>
   </tr>
   <tr>
   <td>活动API文档- jsapi.chm文件</td>
   <td>从活动19.1版本开始，Campaign ClassicAPI可在专用页面中使用。 如果您使用的是旧版jsapi.chm文件，您现在应该参 <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">考新的联机版本</a>。</td>
  </tr> 
  <tr> 
   <td>活动编排——预测营销</td>
   <td>从活动18.10版开始，将不再提供预测营销功能。</td>
  </tr> 
  <tr> 
   <td>Web 应用程序-微型站点</td>
   <td>从活动18.10版开始，不再提供微型站点。 您可以通过限制仅访问Adobe Campaign配置文件上的专用域来提高安全性，并通过使用DNS别名在活动中使用个性化URL。 <a href="https://helpx.adobe.com/cn/campaign/kb/domain-name-delegation.html">了解更多</a></td>
  </tr> 
  <tr> 
   <td>推送通知- iOS二进制连接器</td>
   <td>根据Apple的推荐，Adobe已删除旧版iOS二进制连接器，启动活动18.10版本。 功能更强、效率更高的基于HTTP/2的连接器现已可用。</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>从活动18.6版本开始，出于安全原 <em>因，decryptString</em> API在默认情况下不再可用于新安装。</p> 
   <p>在指向18.6（及更高版本）的上下文中，此API不再激活，已由decryptPassword函数 <em>替换</em> 。 <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">了解更多</a></p></td>
  </tr> 
   <tr> 
   <td>移动渠道- MMS和WAP推送消息</td>
   <td>从活动18.4版开始，不再提供MMS和Wap推送渠道。 作为替代，您可以利 <a href="../../delivery/using/sms-channel.md">用SMS</a> 和 <a href="../../delivery/using/about-mobile-app-channel.md">推送</a> 投放。</td>
  </tr> 
   <tr> 
   <td>移动渠道- LINE v1</td>
   <td>从活动18.4版本开始，LINE Connect包不再可用。 Adobe建议使用新的LINE渠道包作为替换。 <a href="../../delivery/using/line-channel.md">了解更多</a></td>
  </tr> 
 </tbody> 
</table>

## 已弃用的兼容性 {#deprecated-compatibility}

以下系统已弃用于Campaign Classic。 请参阅兼容性 [表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) ，以升级到较新版本或在兼容性结束前移至新系统。

### Adobe Campaign20.2版 {#compat-20-2-release}

从20.2版本开始，已弃用以下系统进行Campaign Classic。 兼容性将在20.3版本（2020年9月）中终止。

* 客户端控制台：Windows 7
* 旧版SMS连接器（请参阅下面的已弃用功能部分）

### Adobe Campaign19.2版  {#compat-19-2-release}

从19.2版本开始，Campaign Classic不再支持以下操作系统。 兼容性将于2020年结束。

* Web服务器：Apache 2.2。
* 操作系统：CentOS 6。

请参阅兼容性 [表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) ，以升级到较新版本或迁移到新系统。

## 兼容性终止 {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic与兼容性矩阵中列出的所有系统和工 [具兼容](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。 当这些第三方系统和工具的特定版本与其各自的创建者达到生命周期终止(EOL)时，Adobe Campaign不再与这些版本兼容：它们被宣布为已弃用，然后从后续产品发行版的兼容性矩阵中删除。 请确保您使用兼容性矩阵中列出的任何系统的受支持版本，以避免出现任何问题。

### 客户端控制台 {#client-console-eol}

Adobe Campaign Classic客户端控制台不再能在以下系统上运行，因为其编辑已弃用它们。 在其中某个版本上运行活动客户端控制台的客户需要在目标删除日期之前升级到最新版本。 请参阅兼容性 [表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

* Windows Server 2003、2008、2008 R2
* Windows XP、Vista

>[!NOTE]
>从活动20.1版本开始，Campaign Classic客户端控制台32位不再与活动最新版本兼容。 您需要使用64位客户端控制台。


### 操作系统 {#o-s-eol}

从19.1版本开始，Adobe Campaign不再与以下操作系统兼容。

* 德比7号。 [了解更多](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [了解更多](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008。 [了解更多](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11。 [了解更多](https://www.suse.com/lifecycle)

### Web服务器 {#web-server-eol}

从19.1 Spring Release开始，Adobe Campaign不再与以下Web服务器兼容。

* Microsoft IIS 7。 [了解更多](https://support.microsoft.com/en-us/lifecycle/search/810)

### 工具 {#tools-eol}

从19.1 Spring发行版开始，Adobe Campaign不再与以下工具兼容。

* Java JDK 7. [了解更多](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x，嵌入到其他工具中时除外。 [了解更多](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### 数据库引擎 {#dbe-eol}

Adobe不支持以下数据库引擎，因为其编辑器已弃用它们。 在这些版本中运行的客户需要升级到最新版本或迁移到另一个版本。

请参阅 [Campaign Classic兼容性表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) ，访问兼容版本的列表。

**联合数据访问(联合数据访问)**

从19.1 Spring发行版开始，Adobe Campaign不再与以下联合数据访问服务器兼容。

* PostgreSQL 9.3。了解 [更多](https://www.postgresql.org/support/versioning)
* MySQL 5.5。了 [解更多](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5。了解 [更多](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 - 14.1。了解 [更多](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic与联合数据访问(联合数据访问)下的服务器不兼容。

* DB2 UDB 9.5、9.7。支持更新版本的DB2，通过联合数据访问(联合数据访问)。 [了解更多](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i、10G R2。 支持更新版本的Oracle,联合数据访问(联合数据访问)。 [了解更多](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3、8.4、9.0、9.1、9.2。支持更新版本的PostgreSQL通过联合数据访问(联合数据访问)。 [了解更多](https://www.postgresql.org/support/versioning)
* MSSQL 2000、2005、2008 R2。 支持更新版本的SQL Server，方法是联合数据访问(联合数据访问)。 [了解更多](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1。支持更新版本的MySQL通过联合数据访问(联合数据访问)。 [了解更多](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB已经寿终正寝。 [了解更多](https://www.mysql.com/support)
* Teradata 13、13.1。通过联合数据访问(联合数据访问)支持更新版本的Teradata。 [了解更多](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* 内泰扎6.02,7.0。 [了解更多](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0。 AsterData已经寿终正寝。 [了解更多](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2、15.4、15.5和Sybase ASE 15.0。支持更新版本的Sybase通过联合数据访问(联合数据访问)。 [了解更多](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* 通过HiveSQL的Hadoop:Hadoop 2.7.3、HiveSQL 1.2.1。Adobe Campaign Classic仍将通过联合数据访问(联合数据访问)通过HiveSQL支持列出的Hadoop版本，但这些版本与以下版本合并：HortonWorks(HDP 2.4.X、2.5.x、2.6.x)和HDInsight 3.4(HDP 2.4)、3.5(HDP 2.5)、3.6(HDP 2.6)

**RDBMS服务器**

Adobe Campaign与以下RDBMS服务器不兼容：
* Oracle 10GR2
* PostgreSQL 9.0到9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
