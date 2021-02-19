---
solution: Campaign Classic
product: campaign
title: 兼容性矩阵
description: Campaign Classic 兼容性矩阵
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 100%

---


# 兼容性矩阵{#compatibility-matrix}

本文档列出针对[最新内部版本](../../rn/using/latest-release.md)的 **Adobe Campaign Classic** 支持的所有系统和组件。此列表中未包含的产品和版本与 Adobe Campaign 不兼容。

如果您是 Gold Standard 用户，请参阅 [Gold Standard 兼容性矩阵](../../rn/using/compatibility-matrix-gs.md)。

## 重要说明{#important-notes}

除非另有说明，否则支持所有次要版本。

在其[最新内部版本](../../rn/using/latest-release.md)中，Adobe Campaign Classic 与本页中列出的所有系统和工具都兼容。随着这些第三方系统和工具的特定版本到达其各自创建者的终止生命周期 (EOL)，Adobe Campaign 将不再与这些版本兼容，并将在后续产品发布中从兼容性矩阵中移除。请确保您使用兼容性矩阵中列出的任何系统的受支持版本，以避免出现任何问题。

要了解有关已弃用项目的更多信息，请访问[此页面](../../rn/using/deprecated-features.md)。

>[!CAUTION]
>
>此矩阵通过添加新的受支持项目并移除已弃用项目定期更新。

## 操作系统{#OperatingSystems}

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
<p>10（64 位）</p>
<p>9（64 位）</p>
<p>8（64 位）</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.X（64 位）</p>
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

## Web 服务器{#WebServers}

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
</td>
</tr>
</tbody>
</table>

## 工具{#Tools}

<table>
<tbody>
<tr>
<td>Java 开发工具包 (JDK)</td>
<td>
<p>11</p>
<p>9</p>
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

## RDBMS 服务器{#RDBMSservers}

>[!NOTE]
>
>RDBMS 驱动程序必须与 RDBMS 服务器版本匹配。

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
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
<p>警告：当 Campaign 服务器在 Linux 上运行时，不支持将 Microsoft SQL Server 作为主数据库。<a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">了解详情</a>。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL 是托管环境的默认数据库服务器。

## CRM 连接器{#CRMconnectors}

<table>
<tbody>
<tr>
<td>Salesforce 连接器 API</td>
<td>
<p>API V37</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics 连接器</td>
<td>
<p>Web API：Dynamics 365 本地版和联机版</p>
</td>
</tr>
</tbody>
</table>

## 联合数据访问 (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
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
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
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
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
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
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10（建议用于日语实例）</p>
</td>
</tr>
</tbody>
</table>

## 移动 SDK{#MobileSDK}

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

## 浏览器{#Browsers}

对于以下浏览器，支持最新版本：Microsoft Edge、Mozilla Firefox、Google Chrome、Safari。

支持 Internet Explorer 11。

## 诸如此类{#Morelikethis}

* [Campaign Classic 发行说明](../../rn/using/latest-release.md)
* [安装指南](../../installation/using/general-architecture.md)
* [已弃用的功能和系统](../../rn/using/deprecated-features.md)
* [内部版本升级过程](../../production/using/build-upgrade.md)
