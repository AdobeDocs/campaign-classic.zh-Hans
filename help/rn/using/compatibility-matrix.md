---
product: campaign
title: Campaign Classic 的兼容性矩阵
description: Campaign Classic 兼容性矩阵
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 3e771d9a18c083bee8239b95d1d68d63928217c2
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 100%

---

# 兼容性矩阵{#compatibility-matrix}



本文档列出了针对[最新内部版本](../../rn/using/latest-release.md)的 **Adobe Campaign Classic v7** 支持的所有系统和组件。此列表中未包含的产品和版本与 Adobe Campaign 不兼容。

如果您是 [!DNL Gold Standard] 用户，请参阅 [[!DNL Gold Standard]  兼容性矩阵](../../rn/using/gold-standard.md#compatibility-matrix-gs)。

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
<p>7.x</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11（从 Campaign v7.3 开始）</p>
<p>10</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x</p>
<p>7.x</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2019（从 Campaign v7.2 开始）</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>如果使用的是 RHEL，则必须愿意禁用 SELinux，或者让架构师编写自定义 SELinux 规则来检查已启用的 SELinux 是否不会导致 Campaign 操作问题。

## Web 服务器{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 on Windows Server 2016 和 2019</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7、Debian 8/9、Windows</p>
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
<p>Campaign 支持由 Oracle 开发的 Java 开发工具包 (JDK) 和 OpenJDK。</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7（和先前版本，如果嵌入在系统中）</p>
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

## 关系数据库管理系统 (RDBMS){#RDBMSservers}

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
<p>14.x（从 Campaign v7.3.2 起）</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p><strong>注意：</strong>您还可以将 Amazon RDS for PostgreSQL 与以上指定的版本配合使用。</p>
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
<p><strong>重要提示：</strong>当 Campaign 服务器在 Linux 上运行时，不支持将 Microsoft SQL Server 作为主数据库。<a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/installing-campaign-in-linux/prerequisites-of-campaign-installation-in-linux.html?lang=zh-Hans#database-access-layers">了解详情</a>。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS 驱动程序必须与 RDBMS 服务器版本匹配。
>
>* PostgreSQL 是用于托管环境的 RDBMS。

## CRM 连接器{#CRMconnectors}

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
<td><strong>Campaign 版本</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>最低版本为 7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>最低为 7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>最低版本为 7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>最低为 7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>最低版本为 7.0 19.1.4</td>
</tr>
</tbody>
</table>

此外，**混合**&#x200B;和&#x200B;**内部部署**&#x200B;环境也支持将 Campaign 与以下外部数据库系统连接。这些系统与 Campaign **Managed Services**（托管）环境&#x200B;**不兼容**。

<table>
<tbody>
<td><strong>数据库系统</strong></td>
<td><strong>数据库版本</strong></td>
<td><strong>Campaign 版本</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td>最低版本为 7.0 19.1.4</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>最低版本为 7.3</p>
<p>最低版本为 7.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>最低版本为 7.0</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>最低版本为 7.0</p>
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
<td>最低版本为 7.0</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 和 SP2</p>
</td>
<td>最低版本为 7.0</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>最低版本为 7.0</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x（最新版本）</p>
</td>
<td>最低版本为 7.0</td>
</tr>
<tr><td>Hadoop（通过 HiveSQL）</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>最低版本为 7.0</td>
</tr>
</tbody>
</table>



## 客户端控制台 {#ClientConsoleoperatingsystems}

**必须**&#x200B;配备以下操作系统和浏览器，才能使用 [Campaign 客户端控制台](../../installation/using/installing-the-client-console.md)。

### 操作系统

<table>
<tbody>
<td><strong>系统</strong></td>
<td><strong>操作系统版本</strong></td>
<td><strong>Campaign 版本</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>最低版本为 7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>最低版本为 7.2.1</p>
<p></p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 运行时

Microsoft Edge WebView2 运行时最新版本是 Campaign 客户端控制台的必需版本。

从 [Microsoft 开发人员网站](https://www.adobe.com/go/acc-ms-webview2-runtime-download)下载 Microsoft Edge WebView2。


## 移动 SDK{#MobileSDK}

您可以在下列操作系统上使用 Campaign [发送推送通知](../../delivery/using/about-mobile-app-channel.md)，通过利用关联的 [Mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。

您还可以通过在“数据收集 UI”中配置 Adobe Campaign 扩展来使用 Adobe Experience Platform Mobile SDK。

<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>12（从 Campaign v7.3 开始）、9.0、8.x、7.x</p>
<p>带有移动 SDK 内部版本 1.1.1</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 15</p>
<p>带有移动 SDK 内部版本 1.0.26，与 32 位和 64 位版本兼容。从 Campaign v7.3 开始支持 iOS 15</p>
</td>
</tr>
</tbody>
</table>

## 浏览器{#Browsers}

以下浏览器在其最新版本中与 Campaign [Web 访问](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-)兼容。

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



## 更多此类内容{#Morelikethis}

* [Campaign Classic 发行说明](../../rn/using/latest-release.md)
* [Campaign 一般架构](../../installation/using/general-architecture.md)
* [硬件大小调整建议](../../technotes/using/hardware-sizing.md)
* [已弃用的功能和系统](../../rn/using/deprecated-features.md)
* [内部版本升级过程](../../production/using/build-upgrade.md)
