---
title: 兼容性矩阵
description: 兼容性矩阵
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e8598fd445f6e2ebd891af1e15c07eb836cd647
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 6%

---


# 兼容性矩阵{#compatibility-matrix}

此文档列表最新版本的 **Adobe Campaign经典（v6.11和v7）支持的所有系统和组件**。 不属于本列表的产品和版本与Adobe Campaign不兼容。

## 重要说明{#important-notes}

此矩阵会定期更新，新增受支持项目正在添加，已弃用项目正在删除。

除非另有说明，否则支持所有次要版本。

Adobe Campaign经典与本页中列出的所有系统和工具兼容。 由于这些第三方系统和工具的特定版本与其各自的创建者达到生命周期终止(EOL),Adobe Campaign将不再与这些版本兼容，并且它们将在后续产品版本中从我们的兼容性矩阵中删除。 请确保您使用兼容性矩阵中列出的任何系统的受支持版本，以避免出现任何问题。

要了解有关已弃用项目的更多信息，请 [访问此页](../../rn/using/deprecated-features.md)。

## 操作系统{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x（64位）</p>
</td>
</tr>
<tr>
<td>德比安</td>
<td>
<p>8（64位）</p>
<p>9（64位）</p>
<p>10（64位）</p>
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
<p>2012</p>
<p>2012年R2</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

## Web服务器{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2012上的8.0 - Windows 8</p>
<p>8.5 on Windows Server 2012 R2</p>
<p>Windows Server 2016上的10.0</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4适用于RHEL7 - CentOS 7、Debian 8/9、Windows（64位）</p>
</td>
</tr>
</tbody>
</table>

## 工具{#Tools}

<table>
<tbody>
<tr>
<td>Java开发工具包(JDK)</td>
<td>
<p>8</p>
<p>9</p>
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

## RDBMS驱动程序{#RDBMSdrivers}

支持以下RDBMS驱动程序：

* Oracle SQL*Net 11

* Oracle SQL*Net 12

* PostgreSQL(libpq)

* SQLServer

* DB2（ODBC驱动程序）


>[!NOTE]
>
>RDBMS驱动程序必须与RDBMS服务器版本匹配。

## RDBMS服务器{#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>11g R2</p>
<p>12c</p>
<p>18c</p>
<p>19c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
<p>注意： 您还可以将Amazon RDS for PostgreSQL与上述指定的版本一起使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2012 - SP1和SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
<p>警告： 当活动服务器在Linux上运行时，不支持将Microsoft SQL Server作为主数据库。 请参阅安 <a href="https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html#Microsoft_SQL_Server">装指南</a>。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL是托管环境的默认数据库服务器。

## CRM连接器{#CRMconnectors}

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
<p>API版本15</p>
<p>API版本21</p>
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
<p>Soap API —— 内部部署： 2007、2015、2016</p>
<p>Soap API —— 在线： 2015年， 2016年</p>
<p>Web API —— 内部部署和在线： 365、2016、2016更新1</p>
</td>
</tr>
</tbody>
</table>

## 联合数据访问(联合数据访问){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>微软Azure突触Analytics</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>11g</p>
<p>12c</p>
<p>18c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2012 SP1和SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
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
<p>15.0</p>
<p>15.10</p>
<p>16</p>
<p>16.20</p>
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
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>雪花</td>
<td> </td>
</tr>
</tbody>
</table>

## 客户端控制台操作系统{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2016</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10（对于日语实例，建议使用）</p>
</td>
</tr>
</tbody>
</table>

## 移动SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x</p>
<p>8.x</p>
<p>9.0</p>
<p>与移动SDK内部版本1.0.27。</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9</p>
<p>iOS 10</p>
<p>iOS 11</p>
<p>iOS 12</p>
<p>iOS 13</p>
<p>与移动SDK内部版本1.0.26兼容，并兼容32和64位版本。</p>
</td>
</tr>
</tbody>
</table>

## 浏览器{#Browsers}

支持Internet Explorer版本11。

对于以下浏览器，支持最新版本：

* Microsoft Edge

* Firefox

* 铬黄

* Safari

## Experience Cloud 集成{#ExperienceCloudintegrations}

有关与Adobe解决方案集成的信息，请参阅本 [节](https://docs.adobe.com/content/help/en/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations)。

## 更像这样{#Morelikethis}

* [Campaign Classic发行说明](https://docs.adobe.com/content/help/zh-Hans/campaign-classic/using/release-notes/latest-release.html)
* [安装指南](https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [已弃用的功能和系统](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)
* [构建升级过程](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html)
* [Campaign Classic19.0版本的兼容性矩阵](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html)
* [Campaign Classic19.1版本的兼容性矩阵](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-1.html)

