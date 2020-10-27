---
title: Gold Standard兼容性矩阵
description: Gold Standard版本的Campaign Classic兼容性矩阵
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7p
translation-type: tm+mt
source-git-commit: e615b2420d126cd42ed52257491282b36975f9ff
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 13%

---


# Gold Standard兼容性矩阵{#compatibility-matrix-gs}

此文档列表了支持Adobe Campaign ClassicGold Standard **19.1构建的所** 有系统和组件。 不属于本列表的产品和版本与Adobe Campaign不兼容。

## 重要说明{#important-notes-gs}

除非另有说明，否则支持所有次要版本。

Adobe Campaign Classic与本页中列出的所有系统和工具兼容。 由于这些第三方系统和工具的特定版本与各自的创建者达到生命周期终止(EOL),Adobe Campaign将不再与这些版本兼容，并且它们将在后续产品版本中从我们的兼容性矩阵中删除。 请确保您使用兼容性矩阵中列出的任何系统的受支持版本，以避免出现任何问题。

## Operating Systems{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x（64位）</p>
<p>7.x（64位）</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9（64位）</p>
<p>8（64位）</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x（64位）</p>
<p><strong>重要：</strong> 如果您使用RHEL，您必须愿意禁用SELinux，或让架构师编写自定义SELinux规则来检查启用的SELinux是否未导致活动操作问题。</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012年R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

## Web Servers{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2016上的10.0</p>
<p>8.5 on Windows Server 2012 R2</p>
<p>Windows Server 2012上的8.0 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4适用于RHEL7 - CentOS 7、Debian 8/9、Windows（64位）</p>
<p>2.2适用于RHEL6 —— 仅限CentOS 6（64位）</p>
</td>
</tr>
</tbody>
</table>

## 工具{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java开发工具包(JDK)</td>
<td>
<p>8</p>
<p>该应用程序已被批准用于Oracle开发的Java开发工具包(JDK)以及OpenJDK。</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6（如果嵌入到系统中，则为先前版本）</p>
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

## RDBMS服务器{#RDBMSservers-gs}

>[!NOTE]
>
>RDBMS驱动程序必须与RDBMS服务器版本匹配。

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
<p>注意：您还可以将AmazonRDS for PostgreSQL与上述指定的版本一起使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2018</p>
<p>2018 R2</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1和SP2</p>
<p>警告：当活动服务器在Linux上运行时，不支持将Microsoft SQL Server作为主数据库。 <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">了解详情</a>。</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>警告：新安装不允许使用DB2 UDB。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL是托管环境的默认数据库服务器。

## CRM connectors{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce连接器API</td>
<td>
<p>API版本37</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API版本21</p>
<p>API版本15</p>
</td>
</tr>
<tr><td>Oracle On Demand API</td>
<td>
<p>Web服务v1.0 API</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>Soap API —— 内部部署：2007、2015、2016</p>
<p>Soap API —— 在线：2015年， 2016年</p>
<p>Web API —— 内部部署和在线：365、2016、2016更新1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
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
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1和SP2</p>
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
<td>内泰扎</td>
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
<p>版本1 SP12或更高版本</p>
</td>
</tr>
<tr><td>通过HiveSQL的Hadoop</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4(HDP 2.4)、3.5(HDP 2.5)、3.6(HDP 2.6)</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## 客户端控制台操作系统{#ClientConsoleoperatingsystems-gs}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>七</p>
<p>8</p>
<p>10（对于日语实例，建议使用）</p>
</td>
</tr>
</tbody>
</table>

## 移动SDK{#MobileSDK-gs}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x、8.x、9.0</p>
<p>与移动SDK内部版本1.0.27。</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 12</p>
<p>与移动SDK内部版本1.0.25兼容，并兼容32和64位版本。</p>
</td>
</tr>
</tbody>
</table>

## 浏览器{#Browsers-gs}

对于以下浏览器，支持最新版本：Microsoft Edge、Mozilla Firefox、Google Chrome、Safari。

支持Internet Explorer 11。

## 更像这样{#Morelikethis-gs}

* [Campaign Classic发行说明](../../rn/using/latest-release.md)
* [安装指南](../../installation/using/general-architecture.md)
* [已弃用的功能和系统](../../rn/using/deprecated-features.md)
* [构建升级过程](https://helpx.adobe.com/cn/campaign/kb/acc-build-upgrade.html)
