---
product: campaign
title: Campaign Classic 的兼容性矩阵
description: Campaign Classic 兼容性矩阵
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: b23632d0718d62d61e94e636937b93aa39bbe43f
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---

# 兼容性矩阵 {#compatibility-matrix}

在其[最新内部版本](../../rn/using/latest-release.md)中，Adobe Campaign Classic v7 与本页中列出的所有系统和工具都兼容。随着这些第三方系统和工具的特定版本到达其各自创建者设定的终止生命周期 (EOL)，Adobe Campaign 将不再与这些版本兼容，并将在后续产品发布中从兼容性矩阵中移除。请确保使用兼容性矩阵中列出的任何系统的受支持版本，以免出现任何问题。要了解有关已弃用项目的更多信息，请访问[此页面](../../rn/using/deprecated-features.md)。

除非另有说明，否则支持所有次要版本。

>[!CAUTION]
>
>会定期更新此矩阵，添加新的支持系统和工具，并移除已弃用系统和工具。

## 操作系统 {#OperatingSystems}

作为内部部署/混合部署客户，您必须在以下列出的操作系统之一中安装 Adobe Campaign。在[此页面](../../installation/using/application-server.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

<table> 
<tbody> 
<td><strong>操作系统</strong></td>
<td><strong>操作系统版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>如果使用 RHEL，则必须愿意禁用 [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux)，或者让架构师编写自定义 SELinux 规则检查已启用的 SELinux，确定其不会造成 Campaign 操作问题。

## Web 服务器 {#WebServers}

作为内部部署/混合部署客户，根据您的操作系统，您必须在以下列出的一个 Web 服务器中集成 Campaign。在[此页面](../../installation/using/integration-into-a-web-server-for-windows.md)（适用于Windows）和[此页面](../../installation/using/integration-into-a-web-server-for-linux.md)（适用于Linux）中了解有关 Web 服务器配置步骤的更多信息。

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2016 上的 10.0 版</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4</p>
</td>
</tr>
</tbody>
</table>

## 工具 {#Tools}

作为内部部署/混合部署客户，您必须安装和配置以下列出的工具。[了解详情](../../installation/using/application-server.md)。

<table>
<tbody>
<td><strong>工具</strong></td>
<td><strong>版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td><p>Java 开发工具包 (JDK)</p>
<p>请参阅<a href="../../installation/using/application-server.md#jdk" target="_blank">此页面</a>以了解详情。</p>
</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>自 v7.4.1 起必需</p>
<p>截至 v7.4.1</p>
<p>截至 v7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7（和先前版本，如果嵌入在系统中）</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## 关系数据库管理系统 (RDBMS) {#RDBMSservers}

作为内部部署/混合部署客户，您必须安装和配置以下数据库之一。[了解详情](../../installation/using/creating-and-configuring-the-database.md)。


<table>
<tbody>
<td><strong>数据库系统</strong></td>
<td><strong>数据库版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Microsoft SQL Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS 驱动程序必须与 RDBMS 服务器版本匹配。
>
>* Campaign 服务器在 Linux 上运行时，不支持将 Microsoft SQL Server 作为主数据库。[了解详情](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers)。
>
>* 还可以将 Amazon RDS for PostgreSQL 与以上指定的版本配合使用。
>
>* PostgreSQL 是用于托管/管理云服务环境的 RDBMS。


## CRM 连接器 {#CRMconnectors}

下面列出了与 Adobe Campaign 兼容的客户关系管理 (CRM) 系统。[了解](../../platform/using/crm-connectors.md)有关 Campaign CRM 连接器的更多信息。

<table>
<tbody>
<tr>
<td>Salesforce 连接器 API</td>
<td>
<p>API 版本 49</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics 连接器</td>
<td>
<p>网络 API</p>
</td>
</tr>
</tbody>
</table>

## 联合数据访问 (FDA){#FederatedDataAccessFDA}

下面列出了与 Adobe Campaign [联合数据访问模块](../../installation/using/about-fda.md)兼容的外部数据库。兼容性取决于您的[托管模型](../../installation/using/hosting-models.md)。

**Managed Services**（托管）、 **混合**&#x200B;和&#x200B;**内部部署**&#x200B;环境可以将 Campaign 与以下外部数据库系统连接：

<table>
<tbody>
<td><strong>数据库系统</strong></td>
<td><strong>数据库版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

此外，**混合**&#x200B;和&#x200B;**内部部署**&#x200B;环境也支持将 Campaign 与以下外部数据库系统连接。这些系统与 Campaign **Managed Services**（托管）环境&#x200B;**不兼容**。

<table>
<tbody>
<td><strong>数据库系统</strong></td>
<td><strong>数据库版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>V1 SPS 12</p>
</td>
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022（从 Campaign v7.4 开始）</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 和 SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x（最新版本）</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop（通过 HiveSQL）</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## 客户端控制台 {#ClientOS}

**必须**&#x200B;配备以下操作系统和浏览器，才能使用 [Campaign 客户端控制台](../../installation/using/installing-the-client-console.md)。

### 操作系统

<table>
<tbody>
<td><strong>系统</strong></td>
<td><strong>操作系统版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 运行时 {#webview}

Microsoft Edge WebView2 运行时最新版本是 Campaign 客户端控制台的必需版本。

从 [Microsoft 开发人员网站](https://www.adobe.com/go/acc-ms-webview2-runtime-download)下载 Microsoft Edge WebView2。


## Mobile SDK {#MobileSDK}

可以通过在“数据收集”UI 中配置 Adobe Campaign 扩展，使用 Campaign 通过 Adobe Experience Platform Mobile SDK [发送推送通知](../../delivery/using/about-mobile-app-channel.md)。

从 Campaign v7.4 开始[弃用](deprecated-features.md) Campaign SDK。但仍可在以下列出的操作系统中使用它，以确保将现有实施平稳过渡到 AEP Mobile SDK<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->。


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 - 14</p>
<p>带有移动 SDK 内部版本 1.1.1。</p>
<p>从 Campaign v7.4 开始支持 Android 13 和 14。</p>
<p>从 Campaign v7.3 开始支持 Android 12</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 17</p>
<p>带有移动 SDK 内部版本 1.0.26。</p>
<p>Campaign v7.3 及更高版本支持 Apple iOS 15。 </p>
<p>从 Campaign v7.4 开始支持 Apple iOS 16 和 17。</p>
</td>
</tr>
</tbody>
</table>

## 浏览器 {#Browsers}

以下浏览器在其最新版本中与 Campaign [Web 访问](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-)兼容。

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Campaign Classic 发行说明](../../rn/using/latest-release.md)
>* [Campaign 一般架构](../../installation/using/general-architecture.md)
>* [硬件大小调整建议](../../technotes/using/hardware-sizing.md)
>* [已弃用的功能和系统](../../rn/using/deprecated-features.md)
>* [内部版本升级过程](../../production/using/build-upgrade.md)
