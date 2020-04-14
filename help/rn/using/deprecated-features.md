---
title: Campaign Classic已弃用和已删除的功能
description: 本页列表已弃用并删除Adobe Campaign经典的功能
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 79f8cc179fcbf9d537a1cc889b268a43202d7369

---


# Deprecated and removed features {#deprecated-and-removed-features}

Adobe不断评估产品功能，以确定应用更现代的替代方案取代的旧功能，以提高整体客户价值，并始终注意向后兼容性。 由于Adobe Campaign经典与第三方工具配合使用，兼容性会定期更新，以便仅实施受支持的版本。 下面列出了与Adobe Campaign经典不再兼容的版本。

要传达即将移除／替换Campaign Classic功能，请遵循以下规则：

* 首先宣布弃用。 虽然已弃用的功能仍可用于现有用户，但不会进一步增强，也不会记录这些功能。
* 在以下版本中，将最早删除已弃用的功能。 此页中会宣布实际的目标删除日期。

此过程为客户提供了至少一个发布周期，以在实际删除之前将其实施调整为已弃用功能的新版本或后继版本。

>[!NOTE]
>Adobe Campaign版本和新功能列在发行说 [明中](../../rn/using/latest-release.md)。


## 已弃用功能 {#deprecated-features}

本节列表了最新Campaign Classic版本中标记为已弃用的特性和功能。

通常，计划在未来版本中删除的功能会首先设置为已弃用，并提供替代功能。 这些特性和功能不再适用于新Campaign Standard客户，也不应用于任何新实施。 它们也会从产品文档中删除。

建议客户检查是否在当前部署中使用了功能／功能，并制定计划更改其实施以使用提供的替代方案。 请参阅目标删除日期以计划环境并相应更新项目。

### Adobe Campaign18.6版 {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>区域</strong></td>
   <td><strong>功能</strong></td> 
   <td><strong>替换</strong></td> 
  </tr> 
   <tr> 
   <td>Javascript SDK安全性<br></td>
   <td>decryptString<br></td>
   <td><p>出于安全原因， <em>对于新安装，decryptString</em> API在默认情况下不再可用。</p> 
   <p>在指向18.6（及更高版本）的上下文中，此API不再激活，并已由decryptPassword函数 <em>替换</em> 。</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign18.4版 {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>区域</strong></td>
   <td><strong>功能</strong></td> 
   <td><strong>替换</strong></td> 
  </tr> 
   <tr> 
   <td>电子邮件存档<br></td>
   <td>基于文件的存档<br></td>
   <td><p>电子邮件存档现在可通过专用的密送电子邮件地址进行。 <a href="../../installation/using/email-archiving.md">了解更多信息</a>。</p> 
   <p><em>目标删除日期：活动20.2版- 2020年6月</em></p><br> </td>
  </tr> 
   <tr> 
   <td>潜在客户管理<br></td>
   <td>潜在客户<br></td>
   <td><p>Adobe Campaign经典中的潜在客户管理软件包简化了构建和维护整个潜在客户管理生命周期的过程。 类似的功能可以通过其他本机工作流活动和数据模型修改来实现。</p> 
   <p><em>目标删除日期：活动20.2版- 2020年6月</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## 已弃用的兼容性 {#deprecated-compatibility}

### Adobe Campaign20.1版 {#compat-20-1-release}

从2月20.1版开始，已弃用以下系统进行Campaign Classic。 兼容性将在20.2版本中终止- 2020年6月。

<table> 
 <tbody> 
  <tr> 
   <td><strong>区域</strong></td>
   <td><strong>替换</strong></td> 
  </tr> 
   <tr> 
   <td>Campaign Classic客户端控制台32位<br></td>
   <td><p>Campaign Classic客户端控制台64位</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign19.2版 {#compat-19-2-release}

从19.2秋季版本开始，已不再支持以下操作系统进行Campaign Classic。 兼容性将于2020年结束。

* Web服务器：Apache 2.2.了 [解更多](https://wiki.centos.org/About/Product)
* 操作系统：CentOS 6. [了解更多](https://wiki.centos.org/About/Product)

请参阅兼容性 [表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) ，以升级到较新版本或迁移到新系统。

## 删除的功能 {#removed-features}

本节列表了已从Campaign Standard中删除的特性和功能。

<table> 
 <tbody> 
  <tr> 
   <td><strong>区域——功能</strong></td>
   <td><strong>替换</strong></td> 
   <td><strong>版本</strong></td> 
  </tr> 
   <tr> 
   <td>活动API文档- jsapi.chm文件<br></td>
   <td>Campaign ClassicAPI现在可在专用页面中使用。 如果您使用的是jsapi.chm文件，您现在应该参阅 <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">新的联机版本</a>。</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>活动编排——预测营销</td>
   <td>Adobe Campaign经典中预测营销功能的很大一部分是预测模型的消耗。 尽管预测营销工作流活动将在即将推出的版本中删除，但该Adobe Campaign将继续支持通过其他工作流活动从外部来源消费和使用预测模型。</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Web 应用程序-微型站点</td>
   <td>通过限制仅访问Adobe Campaign配置文件上的专用域，提高安全性。 您仍然可以使用DNS别名在活动中使用个性化的URL。 <a href="https://helpx.adobe.com/campaign/kb/domain-name-delegation.html">了解更多信息</a>。</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>推送通知- iOS二进制连接器<br></td>
   <td>根据Apple的建议，Adobe将删除旧版iOS Binary Connector。 功能更强大、效率更高的基于HTTP/2的连接器现已可用。</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>移动渠道- MMS和WAP推送消息</td>
   <td>MMS和Wap推送渠道不再可用。 作为替代产品，您可以利 <a href="../../delivery/using/sms-channel.md">用SMS</a> 和 <a href="../../delivery/using/about-mobile-app-channel.md">推送投放</a> 。</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>移动渠道- LINE v1</td>
   <td>LINE Connect包不再可用于在Adobe Campaign经典中安装。 Adobe建议使用新的LINE渠道包发送LINE消息。 <a href="../../delivery/using/line-channel.md">了解更多信息</a>。</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## 兼容性终止 {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign经典与兼容性矩阵中列出的所有系统和工 [具兼容](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。 当这些第三方系统和工具的特定版本与其各自的创建者达到生命周期结束(EOL)时，Adobe Campaign将不再与这些版本兼容：它们将作为已弃用内容发布，然后从后续产品发行版的兼容性矩阵中删除。 请确保您使用兼容性矩阵中列出的任何系统的受支持版本，以避免任何问题。

### 客户端控制台 {#client-console-eol}

Adobe Campaign经典客户端控制台无法再在以下系统上运行，因为它们的编辑器已弃用它们。 在这些版本之一上运行活动客户端控制台的客户需要在目标删除日期之前升级到最新版本。 请参阅兼 [容性矩阵](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

* Windows Server 2003、2008、2008 R2
* Windows XP、Vista

### 操作系统 {#o-s-eol}

从19.1版本开始，Adobe Campaign不再与以下操作系统兼容。

* 德比7号。 [了解更多信息](https://wiki.debian.org/DebianReleases)。
* RHEL 6.x。了 [解更多信息](https://access.redhat.com/support/policy/updates/errata)。
* Windows Server 2008。 [了解更多信息](https://support.microsoft.com/en-us/lifecycle/search/1163)。
* SLES 11. [了解更多信息](https://www.suse.com/lifecycle)。

### Web服务器 {#web-server-eol}

从19.1 Spring Release开始，Adobe Campaign不再与以下Web服务器兼容。

* Microsoft IIS 7. [了解更多信息](https://support.microsoft.com/en-us/lifecycle/search/810)。

### 工具 {#tools-eol}

从19.1 Spring Release开始，Adobe Campaign不再与以下工具兼容。

* Java JDK 7. [了解更多信息](http://www.oracle.com/technetwork/java/javase/eol-135779.html)。
* Libre Office 3.5 / 4.3 / 5.x，嵌入到其他工具中时除外。 [了解更多信息](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)。

### 数据库引擎 {#dbe-eol}

Adobe不支持以下数据库引擎，因为它们的编辑器已弃用它们。 在这些版本中运行的客户需要升级到最新版本或迁移到另一个版本。

请参阅 [Campaign Classic兼容性列表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) ，以访问兼容版本的。

**联合数据访问(联合数据访问)**

从19.1 Spring Release开始，Adobe Campaign不再与以下联合数据访问服务器兼容。

* Oracle 11G。 [了解更多信息](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)。
* PostgreSQL 9.3。了 [解更多信息](https://www.postgresql.org/support/versioning)。
* MySQL 5.5。 &lt;了[解更多信息](http://www.fromdual.com/support-for-mysql-from-oracle)。
* DB2 9.5.了 [解更多信息](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)。
* Teradata 14 - 14.1。了 [解更多信息](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)。

Campaign Classic与联合数据访问(联合数据访问)中的以下服务器不兼容。

* DB2 UDB 9.5, 9.7。通过联合数据访问(联合数据访问)支持DB2的更新版本。 [了解更多信息](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)。
* Oracle 9i、10G R2。 支持Oracle的更新版本，联合数据访问(联合数据访问)。 [了解更多信息](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)。
* PostgreSQL 8.3、8.4、9.0、9.1、9.2。通过联合数据访问(联合数据访问)支持更新版本的PostgreSQL。 [了解更多信息](https://www.postgresql.org/support/versioning)。
* MSSQL 2000、2005、2008 R2。 通过联合数据访问(联合数据访问)支持更新版本的SQL Server。 [了解更多信息](https://support.microsoft.com/en-us/lifecycle/search/1044)。
* MySQL 5.1。通过联合数据访问(联合数据访问)支持MySQL的更新版本。 [了解更多信息](https://en.wikipedia.org/wiki/InfiniDB)。
* InfiniDB已经寿终正寝。 [了解更多信息](https://www.mysql.com/support)。
* Teradata 13, 13.1.通过联合数据访问(联合数据访问)支持更新版本的Teradata。 [了解更多信息](https://www.info.teradata.com/download.cfm?ItemID=1007255)。
* Netezza 6.02, 7.0内泰扎已经寿终正寝。 [了解更多信息](https://en.wikipedia.org/wiki/Netezza)。
* AsterData 5.0。AsterData即将寿终正寝。 [了解更多信息](https://en.wikipedia.org/wiki/Aster_Data_Systems)。
* Sybase IQ 15.2、15.4、15.5和Sybase ASE 15.0。支持Sybase的更新版本，联合数据访问(联合数据访问)。 [了解更多信息](https://sites.google.com/site/dbatipsandtricks/time-tracker)。
* 通过HiveSQL的Hadoop:Hadoop 2.7.3、HiveSQL 1.2.1。Adobe Campaign经典仍将通过联合数据访问(联合数据访问)通过HiveSQL支持列出的Hadoop版本，但这些版本将与以下内容合并：HortonWorks(HDP 2.4.X、2.5.x、2.6.x)和HDInsight 3.4(HDP 2.4)、3.5(HDP 2.5)、3.6(HDP 2.6)

**RDBMS服务器**

Adobe Campaign与以下RDBMS服务器不兼容：
* Oracle 10GR2、11G
* PostgreSQL 9.0到9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
