---
product: campaign
title: 服务器配置文件
description: 服务器配置文件
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '7969'
ht-degree: 5%

---

# 服务器配置文件{#the-server-configuration-file}

![](../../assets/v7-only.svg)

Adobe Campaign的整体配置在安装目录的&#x200B;**conf**&#x200B;目录的&#x200B;**serverConf.xml**&#x200B;文件中定义。 本部分列出&#x200B;**serverConf.xml**&#x200B;文件的所有不同节点和参数。

>[!NOTE]
>
>只能通过Adobe对由Adobe托管的部署执行服务器端配置。 要了解有关不同部署的更多信息，请参阅[托管模型](../../installation/using/hosting-models.md)部分或[此页面](../../installation/using/capability-matrix.md)。 此[部分](../../installation/using/hosting-models.md)介绍了托管和混合型号的安装和配置步骤。

第一个参数位于&#x200B;**shared**&#x200B;节点内。 这些值与实例相关。 所有nlserver命令（nlserver web、nlserver wfserver等）都可能使用它们。 其他部分与特定nlserver子命令相关。

**共享参数**

* [身份验证](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [执行](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [模块](#module)
* [监测](#monitoring)
* [乌孔夫](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**其他参数**

* [存档](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [流水线](#pipelined)
* [修复](#repair)
* [securityZone](#securityzone)
* [短信](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [跟踪](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## 身份验证 {#authentication}

以下是&#x200B;**authentication**&#x200B;节点的不同参数：

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> 启用IP地址检查。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> 默认标识模式。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “nl”<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> 以秒为单位的长会话超时。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> 安全令牌超时（以秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> 缓存持续时间：以秒为单位缓存会话信息。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> 会话超时（以秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

以下是&#x200B;**authentication > XTK**&#x200B;节点的不同参数：

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> 内部帐户的密码。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> 内部帐户安全区：内部帐户的授权区域。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

以下是&#x200B;**dataStore**&#x200B;节点的不同参数。 这是定义服务器数据源的位置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> 导出目录：导出数据的目标目录的路径。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/” <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> 附加沙盒目录：要添加到沙盒中的其他路径（逗号分隔）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “/home/customers/,/sftp/” <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> 表单缓存过期延迟：超时时间（以秒为单位），在此时间后，缓存条目将失效。 O表示缓存条目仅在发布时刷新。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> DNS掩码：此实例提供的DNS掩码列表(以逗号分隔，可使用*和？ )。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> 交互JSSP缓存过期延迟：超时时间（以秒为单位），在此时间后，缓存条目将失效。 负值表示缓存始终无效。 “0”、空值或无效值被视为60。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> 实例语言（枚举）。 可能的值包括“fr_FR”(Français)、“en_GB”(英语(UK))、“en_US”(英语（美国）)、“de_DE”(Deutsch)和“ja_JP”（日语）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> 上传文件夹：上载数据的目标目录的路径。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/” <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> 将要下载的授权文件以“，”分隔。 该字符串必须是有效的正则表达式。 请参阅<a href="file-res-management.md" target="_blank">限制可上载的文件</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> 将密钥存储在保管库中：使用Hashicorp Vault。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Vault<br />中的密钥路径 </td> 
   <td> 字符串<br /> </td> 
   <td> “/v1/secret/campaign/”<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> 包含保管库令牌的文件的本地路径。 $(HOME)可以在此路径中使用（但不能用到其他env变量）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “$(HOME)/.vaulttoken”<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp Vault URL <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 视图缓存的有效期：超时时间（以秒为单位），在此时间后，缓存条目将失效。 负值表示缓存始终无效。 “0”、空值或无效值被视为60。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> 工作目录的XPath。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> workingDirectory :工作目录的XPath。 默认：“$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/”<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

以下是&#x200B;**dataStore > proxyAdjust**&#x200B;节点的不同参数。 根据urlBase中定义的URL，将重新生成与正则表达式匹配的URL。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> 在生成外部URL时使用的基本URL。 例如：https://server.domain.com<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 用于匹配URL的正则表达式。 例如：http://server\.lan\.net.*<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

以下是&#x200B;**dataStore > dataSource**&#x200B;节点的不同参数。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 数据源名称<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> default<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**dataStore > dataSource > dbcnx**&#x200B;节点中，配置连接设置：

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Unicode存储<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> 工作区<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 已加密<br /> </td> 
   <td> 加密密码<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 登录<br /> </td> 
   <td> 帐户<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 密码<br /> </td> 
   <td> 密码<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> 类型（枚举）。 可能的值包括：“Oracle”、“MSSQL”(Microsoft SQL Server)、“PostgreSQL”(PostgreSQL)、“Teradata”、“DB2”、“MySQL”、“Netezza”、“AsterData”、“SAPHANA”(SAP HANA)、“RedShift”(Amazon Redshift)、“ODBC”(SybaseASE，Sybase IQ)、“中继”(HTTP/&lt;a)。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> 服务器<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> 时区：请参阅<a href="../../installation/using/time-zone-management.md" target="_blank">时区管理</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> 数据库<br />中的Unicode数据 </td> 
   <td> 布尔值<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> 带时区的日期字段：请参阅<a href="../../installation/using/time-zone-management.md" target="_blank">时区管理</a>。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**dataStore > dataSource > sqlParams**&#x200B;节点中，配置SQL参数：

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> 函数前缀<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**dataStore > dataSource > pool**&#x200B;节点中，配置关联连接池的参数：

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aliveTestDelaySec<br /> </td> 
   <td> 连接有效性检查之间的延迟。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> 池中保留的空闲连接数。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> 拒绝新连接前允许的最大连接数。 请参阅此<a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">技术说明</a>。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> 连接的最大空闲时间。 0表示默认值。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

以下是&#x200B;**dataStore > virtualDir**&#x200B;节点的不同参数。 这是虚拟目录到实际目录映射的配置。

有关其他信息，请参阅[管理公共资源](file-res-management.md)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 虚拟目录的名称<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 路径<br /> </td> 
   <td> 实际目录的完整路径<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是默认配置：

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### precossCommand {#preprocesscommand}

以下是&#x200B;**dataStore > precossCommand**&#x200B;节点的不同参数。 这些是用于预处理“加载文件”工作流活动的授权命令。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 命令<br /> </td> 
   <td> 命令行<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> 命令行标签<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 命令行名称<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是默认配置：

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

以下是&#x200B;**dnsConfig**（DNS配置）节点的不同参数。

有关其他信息，请参阅此[部分](../../installation/using/configuring-campaign-server.md)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> 域名：默认域名。 由SMTP HELO命令使用。 默认情况下，使用在Windows中声明的第一个网络接口的网络参数；或在Linux（域或搜索条目）下解析file/etc/resolv.conf。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS服务器：域名服务器(DNS)列表（以逗号分隔）。 请参阅下面的注释。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 重试<br /> </td> 
   <td> DNS查询的重试次数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> DNS查询的超时时间（以毫秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>**nameSevers**上的注意事项：默认情况下，使用网络
>在Windows中声明的第一个网络接口的参数
>未在UNIX中定义。 定义域名服务器(DNS)
>MTA用来获取为
>域。
>
>如果未定义此值，MTA将在主机网络配置中搜索此信息。 如果可以使用多个DNS，则不同的DNS地址必须用逗号分隔(例如：212.155.207.1,212.155.207.2)。 如果您的投放服务器具有多个网络接口，则MTA使用的DNS列表是第一个。 在这种情况下，我们建议指定&#x200B;**nameServer**&#x200B;参数以避免任何歧义。

>[!CAUTION]
>
>如果网络主机配置使用DHCP，则MTA将找不到DHCP提供的DNS列表。 在这种情况下，我们建议在Windows控制面板的网络参数中指定DNS列表。

## 执行 {#exec}

以下是&#x200B;**exec**（命令执行）节点的不同参数。

有关其他信息，请参见[限制授权的外部命令](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> 包含要添加到的命令的文件的路允许列表径。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户<br /> </td> 
   <td> 作为其他用户执行命令。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

以下是&#x200B;**htmlToPdf**&#x200B;节点的不同参数。 这是将网页转换为PDF文档的服务的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 命令<br /> </td> 
   <td> 用于运行转换的命令行（在“其他”模式下）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max。 一台计算机上一次允许的转换进程数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> 用于转换的工具。 可能的值包括：phantomjs， wkhtmltopdf，其他，已禁用<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “phantomjs”<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 转化超时：最大转化时间（以秒为单位）。 超出此阈值后，转换过程将停止，并引发错误。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> 详细<br /> </td> 
   <td> 详细模式：以详细模式启动以诊断可能的错误。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> 等待进程时的延迟：延迟（以秒为单位）。 如果超出此延迟，则停止转换并引发错误。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Phantomjs的示例：

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

以下是&#x200B;**ims**&#x200B;节点的不同参数。 这是使用[IMS](../../integrations/using/about-adobe-id.md)连接到其他服务的Campaign的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> authIMSClientId<br /> </td> 
   <td> 客户端ID<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> 密钥（在AES中加密）<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> 授权代码（在AES中加密）<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> IMS服务器URL<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> 技术帐户客户端ID<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> 技术帐户密钥（在AES中加密）<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> 技术帐户ID<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> 技术帐户私钥（在AES中加密）<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

以下是&#x200B;**javaScript**&#x200B;节点的不同参数。 这是JavaScript解释器的配置。

有关其他信息，请参阅[报表文档](../../reporting/using/actions-on-reports.md#memory-allocation)和此[技术说明](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> 运行垃圾收集器前的最大大小(MB)。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> 每个堆栈块的大小（以千位八位字节为单位）。 这是一个内存管理调整参数，大多数用户都不应该调整此参数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

以下是&#x200B;**mailExchanger**&#x200B;节点的不同参数。 这是SMTP服务器的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> SMTP服务器：用于电子邮件传输的SMTP服务器的IP地址。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> 用于电子邮件传输的SMTP服务器的TCP端口。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模块 {#module}

以下是&#x200B;**module**&#x200B;节点的不同参数。 这是命名空间限制模块xtk的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> 创建新实体时使用的默认命名空间。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “cus”<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 监测 {#monitoring}

以下是&#x200B;**monitoring**&#x200B;节点的不同参数。 这是监视服务配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> 最大准备时间：持续时间（以秒为单位），在此之后，投放操作应该不再进行准备。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> 由监控服务运行的Unix脚本。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> 要由监视服务执行的Windows脚本。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 乌孔夫 {#ooconv}

以下是&#x200B;**ooconv**&#x200B;节点的不同参数。 这是文档转换服务器的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> 允许OpenOffice服务器执行的最大转化数。 除此数字外，还重新启动服务器。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> OpenOffice服务器在强制关闭前的最长空闲时间。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> OpenOffice服务器监听的端口间隔。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 文档转换服务器的URL。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

以下是&#x200B;**proxyConfig**&#x200B;节点的不同参数。 这是代理参数的配置。

有关其他信息，请参见[代理连接配置](file-res-management.md)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabled<br /> </td> 
   <td> 使用代理服务器。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> 例外：应忽略代理参数的地址列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “localhost*” <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 唯一代理服务器：对所有类型的代理使用相同的配置。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP代理/安全代理 {#http-proxy---secure-proxy-}

在&#x200B;**proxyConfig > HTTP代理/安全代理**&#x200B;节点中，配置以下参数。

有关其他信息，请参见[代理连接配置](file-res-management.md)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 地址<br /> </td> 
   <td> 代理服务器的地址<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 登录<br /> </td> 
   <td> 登录到代理服务器<br />的连接 </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 密码<br /> </td> 
   <td> 与代理服务器<br />的连接的密码 </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 代理服务器端口<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

以下是&#x200B;**threadPool**&#x200B;节点的不同参数。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> 池中的最大线程数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

以下是&#x200B;**urlPermission**&#x200B;节点的不同参数。 这是Javascript代码可访问的URL列表。

域和正则表达式列表，用于指定在Javascript代码中遇到的URL是否可以由Adobe Campaign服务器使用。

如果找不到URL，则会根据指定的默认模式执行默认操作。

有关其他信息，请参见[传出连接保护](../../installation/using/configuring-campaign-server.md#url-permissions)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 操作<br /> </td> 
   <td> 如果URL不在授权列表（枚举）中，则执行默认操作。 可能的值包括“忽略”（授权时没有警告消息，这要求禁用保护）、“警告”（授权并发出警告消息）和“拒绝”（禁止访问URL）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> deny<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> 调试URL选择机制的跟踪：在URL验证过程中发出其他消息。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

对于每个URL，添加一个&#x200B;**url**&#x200B;节点，并使用以下参数：

有关其他信息，请参见[传出连接保护](../../installation/using/configuring-campaign-server.md#url-permissions)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> 域名或域父项，与URL相关：要验证的URL域的全部或部分，以加速验证。 仅当URL的域包含dsnSuffix时，才会针对正则表达式验证该URL。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 用于优化验证属于此域的URL的正则表达式：URL必须验证的正则表达式（如果与dnsSuffix对应）。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

如果记录满足&#x200B;**dnsSuffix**&#x200B;但不满足&#x200B;**urlRegEx**，则会检查以下记录。

例如，要授权访问域business.com的所有URL，我们可以定义两条记录：

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.*”

和

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.*”

以下是默认配置：

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

以下是&#x200B;**xtkJobs**&#x200B;节点的不同参数。 这是服务器作业的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 服务器处理的内存状态刷新周期（毫秒）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 存档 {#archiving}

以下是&#x200B;**archiving**&#x200B;节点的不同参数。 这是后台执行的存档操作的配置。

有关其他信息，请参阅[激活电子邮件存档（内部部署）](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquireLimit<br /> </td> 
   <td> 要同时处理的EML数<br /> </td> 
   <td> 长<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> 已发送消息的存档策略（枚举）。 可能的值为“0”（无存档）和“1”（将已发送邮件的存档传输到SMTP服务器）。<br /> </td> 
   <td> 字节<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> 压缩存档的大小：压缩存档中的最大文件数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> 在存档（枚举）过程中使用的压缩格式。 可能的值为“0”（无压缩）和“1”（使用zip格式压缩已发送的消息）。<br /> </td> 
   <td> 字节<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> 未处理电子邮件自动存档之前的延迟：未处理电子邮件存档前的天数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> 每个更新事件之间的延迟（以秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 删除未处理的电子邮件前的天数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> 存档目标目标<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> 激活SMTPS支持：在远程服务器支持时，以安全模式(STARTTLS/SMTPS)激活电子邮件的发送。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> 与归档SMTP服务器的连接数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> 要使用的SMTP中继的DNS名称或IP地址列表（以逗号分隔）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> SMTP服务器的IP端口。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

以下是&#x200B;**inMail**&#x200B;节点的不同参数。 这是入站电子邮件管理模块的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> 验证实例名称：如果为true，则消息ID标头中包含的Adobe Campaign实例名称必须与当前实例相同。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> 转发地址：规则未处理默认电子邮件传送地址。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> 错误地址：用于传输无效电子邮件的默认地址（MIME编码错误）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> 忽略消息大小：用于忽略POP3服务器返回的消息的大小。 在这种情况下，模块需要“。” 消息的结尾。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 消息读取期：消息队列轮询频率。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> 要更新的日志数上限：定义在更新数据库之前要保留在内存中的日志消息的最大数量。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> 在POP3会话期间要读取的消息数上限。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 会话持续时间：消息处理会话的最大持续时间。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3轮询期<br /> </td> 
   <td> 长<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> 读取消息的队列大小<br /> </td> 
   <td> 长<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> 与POP3服务器的通信超时。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> 要轮询的帐户的数据库重新加载频率。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

在&#x200B;**inMail > msgDump**&#x200B;节点中，配置以下参数。 这是已处理消息的转储配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dump<br /> </td> 
   <td> 以文本格式保存所有入站消息。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> 消息转储路径。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “/tmp/inMail”<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

以下是&#x200B;**interactiond**&#x200B;节点的不同参数。 这是入站交互事件的写入守护程序的配置。

有关其他信息，请参阅[Interaction - Data buffer](../../installation/using/interaction---data-buffer.md)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max。 共享内存中存储的呼叫数据字符数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max。 共享内存中存储的事件数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> 符合条件的选件数的最大值，在命题之后排序，要存储以进行统计。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 响应时间统计信息的聚合持续时间（以秒为单位）。 0表示取消激活统计存储。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max。 存储在共享内存中用于识别个人的字符数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

以下是&#x200B;**mta**&#x200B;节点的不同参数。 这是投放代理的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> 保存已发送电子邮件的路径：如果不为空，则保存已发送电子邮件的所有源文件的路径。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> 转储目录：如果不为空，则复制此目录中已发送邮件的MIME信封。 用于故障排除。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS查询日志延迟：显示日志的时间（以毫秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> 错误统计频率：在数据库中生成统计信息和存储之间的时间。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> 生成错误统计信息并将其存储在数据库中。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> 日志消息的显示级别。 写入数据库的日志的严重性级别。 由MTA生成的日志消息并非总是写入数据库中。 通过此参数，您可以定义在数据库中必须写入消息的级别。 如果定义级别2，则也会写入级别1和0的消息，而如果定义级别1，则只会写入级别1和0的消息。 可能的值包括：0（错误）、1（警告）、2（信息）<br /> </td> 
   <td> 长<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> mta进程可使用的最大内存大小(MB)。 超出此限制后，将重新启动该进程，以便将其使用的内存释放到系统。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 要考虑的连接阈值。 如果errorPeriodSec指定时段的连接总数严格低于阈值，则不会为给定路径生成错误统计信息。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> 要考虑的错误阈值：如果errorPeriodSec指定时段的错误总数严格低于阈值，则不会为给定路径生成错误统计信息。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> 需考虑的消息阈值。 如果在errorPeriodSec指定的时段内发送的消息总数严格低于阈值，则不会为给定路径生成错误统计信息。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知中继：HostName：用于中继通知的端口。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> 删除已存档电子邮件之前的延迟：清除dataLogPath中指定目录中已存档电子邮件的间隔天数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> 重试丢失的消息：如果子进程无效，将重试部分投放。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> 启用签名机制。 这可提高电子邮件中跟踪链接的安全性。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> 投放统计服务器的地址，给定为 
    &lt;dns或ip&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>。 请参阅 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">统计服务器的坐标</a>。 
      <br /> 
     </td> 
   <td> 字符串<br /> </td> 
   <td> 如果未定义，则默认端口为7777。<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSupport<br /> </td> 
   <td> 按域启用TLS:启用可由MX配置的TLS（需要最新的统计信息服务器）。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> 使用的协议版本：通信协议版本（v5.11和6.0.2服务器为1,v6.1服务器为2）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 如果未定义，则使用最新版本。<br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> 如果设置为“true”，则您的实例将使用<a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Enhanced MTA</a>.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> 验证模式：激活验证模式(不进行报文的物理传输；用于模拟和测试)。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> 工作目录：MTA用于与其子进程通信的临时文件的位置。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/” <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer字段：SMTP邮件标头中字段“X-Mailer”的值。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'nlserver， Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

在&#x200B;**cache**&#x200B;节点中，配置以下参数。 这是本地文件缓存配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> 在以下情况下回收：句点，以秒为单位，此后文件自动从缓存中删除以回收存储。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> 最大缓存大小(Mb)。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> 清除频率：执行缓存清除机制之间的句点（以秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中继 {#relay}

在&#x200B;**mta > relay**&#x200B;节点中，配置以下参数。 这是邮件投放的邮件服务器配置。

该列表的处理方式与MX DNS查询返回的MX列表相同，通常只要第一个MX可用，就使用下一个MX，依此类推。

有关其他信息，请参见[SMTP中继](../../installation/using/configuring-campaign-server.md#smtp-relay)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 地址<br /> </td> 
   <td> 要使用的SMTP中继的DNS名称或IP地址列表（以逗号分隔）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> SMTP服务器的IP端口。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 主控 {#master}

在&#x200B;**mta > 主控**&#x200B;节点中，配置以下参数。 这是主服务器的配置。

有关其他信息，请参阅此[部分](../../installation/using/configuring-campaign-server.md#mta-child-processes)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 要提交的作业的数据库轮询频率。 此值指示数据库轮询频率（以秒为单位）。 为获取等待交付的作业列表，MTA会定期轮询数据库。 当没有等待的作业时，轮询周期由此值定义。 否则，如果作业已被转移到子服务器，则该轮询持续时间被自动缩短为一秒，以便能够尽快地再次处理新作业，即当子服务器再次可用时。 这并不意味着在子服务器再次可用之前，将每秒执行一次数据库查询。 事实上，只有在至少一个子服务器可用时，才能完成数据库访问。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> 数据库连接失败后的等待时间。 数据库连接失败通常由数据库服务器本身引起。 例如，也可出于维护目的而停止服务器。 DataBaseRetryDelay参数定义在数据库连接失败时两次连接尝试之间的持续时间。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 私钥(DomainKeys)缓存的有效期。 用于在DomainKeys推荐(http://antispam.yahoo.com/domainkeys)之后对电子邮件进行签名的私钥作为选项存储在数据库中。 domainKeysReloadPeriodSec参数定义MTA可将这些键保留在缓存中的秒数。 在此延迟后，必须从数据库重新加载所有密钥。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> 子服务器的最大数量。 表示运行的服务器的最大数量。 建议在与服务器内存资源兼容的最佳位置限制此数量。 可以在投放期间检查此项。 使用的内存不应超过物理内存的三分之一，否则将使用交换。 请参阅<a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA子进程</a>。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> 子服务器的最小数量。 MTA会尝试至少保持此数量的服务器运行。 如果数量较少，则每秒会重新启动一次新服务器，直到达到此值。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 启动时的子服务器数量。 动态监控子服务器的数量；当MTA启动时，它会创建该值所指示的任意数量的子服务器。 通常，为了节省主机资源，子服务器的启动速度不能快于每秒一个服务器。 但是，当MTA启动时，此限制将被覆盖，以便尽快提供子服务器。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 孩子 {#child}

在&#x200B;**mta > child**&#x200B;节点中，配置以下参数。 这是子服务器的配置。

有关其他信息，请参阅[电子邮件发送优化](../../installation/using/email-deliverability.md#email-sending-optimization)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> 可选命令行参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 超时，直到停止空闲的子服务器。 如果子服务器的空闲时间大于此参数，则它将自动停机以释放主机资源。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> 最大邮件保留时间。 如果由于限制或无法连接到目标MTA而无法发送准备的消息，则该消息将被放弃，并将在下次重试时进行处理。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> 每个子服务器启动的对FCM的并行Http请求的最大值。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> 每个子服务器的消息数上限。 每个MTA子项都会处理此数量的消息和死亡。 必须指定一个数字，以便MTA中的内存或资源泄漏是无害的（通常只有几千个）。 即使MTA代码中没有已知的内存泄漏，嵌入的JavaScript和XSL引擎也不完全可靠。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 待处理消息：内存中待发送消息的最大数量。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 子进程可使用的最大内存大小(MB)。 超出此限制后，进程将停止，以便它使用的内存将释放到系统。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 超时（以秒为单位），在此之后将放弃投放连接器的SOAP连接。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> 始终以最高优先级MX开头。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> 恢复后连续尝试的最大次数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**mta >子> smtp**&#x200B;节点中，配置以下参数。 这是SMTP会话的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> 在远程服务器支持时，以安全模式(STARTTLS/SMTPS)激活电子邮件的发送。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> 空闲会话超时。 仅当会话被重用来向给定域发送多条消息时，才使用此参数。 当MTA完成消息传输时，它使用的SMTP会话不会系统关闭。 如果消息已准备好为同一域发送，则同一SMTP会话将被重用，这就是会话不自动关闭的原因。 参数IdleSessionTimeout参数允许您定义SMTP会话在何种时间内可保持活动状态以等待另一条消息。 持续时间过后，会话将自动关闭。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> 重试连接之前的初始延迟。 每次连接失败时，此延迟都会加倍。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 子服务器的SMTP会话数上限。 要发送消息，MTA会初始化与收件人MTA的SMTP连接。 给定子服务器的并发和活动SMTP会话的最大数量受此值限制。 如果将此值乘以maxSpareServers，则得到给定子服务器可同时处理的消息数上限。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**mta >子项> smtp > IPAffinity**&#x200B;节点中，配置以下参数。 这是使用IP地址管理用于优化传出SMTP流量的喜好的配置。

有关更多信息，请参阅[要使用](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)和[管理具有相关性的出站SMTP流量的IP地址列表](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> 域名：链接到IP地址的本地域名。 发出SMTP HELO命令时使用。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 逻辑名称：用户链接到亲和度的名称。 名称使用分号分隔；<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**mta >子> smtp > IP**&#x200B;节点中，配置以下参数。

有关其他信息，请参阅[要使用的IP地址列表](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 地址<br /> </td> 
   <td> 关联的物理地址。 例如：“192.168.0.1”<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> 关联的公共地址ID。 用作统计信息服务器的键。 必须是数字。 请参阅此<a href="../../installation/using/email-deliverability.md#managing-ip-addresses">部分</a>。<br /> </td> 
   <td> 长<br /> </td> 
  </tr> 
  <tr> 
   <td> 权重<br /> </td> 
   <td> 指定此IP相对于其他IP的使用频率（权重越大，频率越高）。<br /> </td> 
   <td> 长<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> 要包含的域掩码列表（以逗号分隔）。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> 要排除的域掩码列表（以逗号分隔）。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> 链接到IP地址的计算机名称。 发出SMTP HELO命令时使用。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

以下是&#x200B;**nmac**&#x200B;节点的不同参数。 这是推送通知投放的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> 使用在shared/proxyHTTP中定义的HTTP代理。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中继 {#relay-1}

以下是&#x200B;**nmac > relay**&#x200B;节点的不同参数。 这会配置对消息传递的中继的使用(ios http2 connector)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 地址<br /> </td> 
   <td> 要使用的中继的DNS地址或名称。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 中继端口<br /> </td> 
   <td> 长<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> 证书链（PEM文件）。 在使用模拟服务器时很有用。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 流水线 {#pipelined}

以下是&#x200B;**pipelined**&#x200B;节点的不同参数。 这是Pipeline Services的事件处理模块的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> 保存公钥时在开发人员连接中生成的应用程序的名称。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> 用于获取网关令牌的URL。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 用于获取令牌的私钥（在AES中使用XtkKey选项进行加密）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> 禁用身份验证：在未进行身份验证的情况下连接到Pipeline Services。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 用于发现管道服务URL的URL。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> 状态保存期：进程内部信息保存在文件中的频率。 如果为0. <br />，则不活动 </td> 
   <td> 长<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 监听URL:强制管道服务的监听URL。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> 状态服务器端口：用于查询进程状态的HTTP服务器端口。 如果为0.<br />，则为非活动 </td> 
   <td> 长<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> 每次处理此数量的消息时，指针都将存储在数据库中。<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> 存储指针之前的延迟：在此期间，指针将至少存储一次在数据库中（在活动低时很有用）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> 使用个性化JavaScript连接器进行事件处理的线程数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> 用于事件处理的线程数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> 出现故障时，处理之间的延迟。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 在此时段后放弃：如果处理在此时段后仍然失败，请放弃事件。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 修复 {#repair}

以下是&#x200B;**repair**&#x200B;节点的不同参数。 这是数据库修复模块的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> repairActionDelayMin<br /> </td> 
   <td> 交货操作修复模块：延迟（以分钟为单位），修复模块可在延迟后处理投放操作。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

以下是&#x200B;**securityZone**&#x200B;节点的不同参数。

有关其他信息，请参阅[定义安全区](../../installation/using/security-zones.md)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> 授权Web应用程序的调试模式。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 授权用户在无密码的情况下使用应用程序。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> 授权使用HTTP进行操作员登录。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLIncompent<br /> </td> 
   <td> 授权在表达式中使用SQLDATA。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> 授权用户/密码会话令牌。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 标签<br /> </td> 
   <td> 标签<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 内部名称<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> NewName()<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> 请勿使用安全令牌。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> 显示错误详细信息<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是默认配置：

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

以下是&#x200B;**securityZone > subNetwork**&#x200B;节点的不同参数。

有关其他信息，请参阅[定义安全区](../../installation/using/security-zones.md)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 标签<br /> </td> 
   <td> 标签<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> 掩码<br /> </td> 
   <td> 掩码或地址<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 内部名称<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> NewName()<br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> 此子网络用于访问实例的代理的掩码或地址（反向）。 在这种情况下，将测试“X-Forwarded-For”标头，而不是此代理。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 短信 {#sms}

以下是&#x200B;**sms**&#x200B;节点的不同参数。 这是入站短信管理模块的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> SMPP连接器保留的文件工作文件的最大天数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> SMPP工作文件的最大大小(MB)。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 会话连续性框架的重复：max 两帧之间用于通知接收会话仍处于启用状态的时段（秒）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> 搜索频率：SMS帐户轮询期。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> 帐户重新加载频率：要轮询的帐户的数据库重新加载频率。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> SR处理延迟的秒数：只有恢复日期早于当前时间的SR减去srReadDelay给定的持续时间（以秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 与短信网关的通信超时。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

以下是&#x200B;**sms > netsize**&#x200B;节点的不同参数。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> 与Netsize建立连接时的超时时间（以秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

以下是&#x200B;**stat**&#x200B;节点的不同参数。 这是MTA统计模块的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 服务器侦听端口。 请参阅此<a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">部分</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

以下是&#x200B;**syslogd**&#x200B;节点的不同参数。 这是日志管理模块的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> 日志文件的最大大小(Mb)。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> 要保留的logins.log文件数上限。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟踪 {#tracking}

以下是&#x200B;**tracking**&#x200B;节点的不同参数。 这是跟踪服务器的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> 禁用从以前的内部版本生成的格式错误的URL。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> 合并期<br /> </td> 
   <td> 长<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> 删除重复的开口：删除重复的打开跟踪日志，以限制Outlook等邮件阅读器中邮件预览的效果。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> 最多忽略X%的错误：只要尚未考虑的日记帐比率未达到此值，就不要更新跟踪指标。<br /> </td> 
   <td> 字节<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> 更新错误指示器：重新计算错误指示器前的最大持续时间。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> 在以下期间计算指标：在投放有效日期之后的持续时间，在此之后将不再计算合并指标。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程<br />时要执行的JavaScript ID </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 调用远程跟踪服务器请求的日志数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Phishbowl服务端点集成的API密钥。 这可保护从旧版本生成的格式错误的URL的重定向。<br /> </td> 
   <td> 长<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Phishbowl服务端点集成的端点。 这可保护从旧版本生成的格式错误的URL的重定向。<br /> </td> 
   <td> 长<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> 最多忽略X%的跟踪：只要尚未考虑的日记帐比率未达到此值，请不要更新跟踪指标。<br /> </td> 
   <td> 字节<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> 更新跟踪指标：重新计算跟踪指示器之前的最大持续时间。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> 浏览器标识符缓存的大小。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

以下是&#x200B;**trackinglogd**&#x200B;节点的不同参数。 这是跟踪日志写入守护程序的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程<br />时要执行的JavaScript ID </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 最大写入重试数：在日志文件中写入失败时可以创建的最大文件数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 最大日志大小：磁盘上日志使用的最大空间(MB)。 不能小于100 MB。 <br /> </td> 
   <td> 长<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 最大日志计数：共享内存中存储的最大日志数。 不能小于10000。 <br /> </td> 
   <td> 长<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 清除前的日志数：开始清除日志文件之前插入的日志数。 不得低于50000。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> 共享内存中为额外Web跟踪参数保存的最大字符数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

以下是&#x200B;**web**&#x200B;节点的不同参数。 这是Web模块的配置。

有关其他信息，请参阅此[部分](configuring-campaign-server.md#default-port-for-tomcat)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> 作为字符串传递的JVM的选项。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> 最大线程数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> 最小线程数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat监听控制端口：请参阅<a href="configure-tomcat.md" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP侦听端口：请参阅<a href="configure-tomcat.md" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SubmitDelivery调用的队列大小：可排入队列的SubmitDelivery SOAP调用的最大数量。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：关于给定进程消耗的RAM量（以Mb为单位）的警告<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知中继：HostName：启用通知中继的端口。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> 以模块模式启动SOAP路由器。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

以下是&#x200B;**web > jsp**&#x200B;节点的不同参数。 这是JSP使用的参数的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debug<br /> </td> 
   <td> 是否在调试模式下执行JSP。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> 下载文件夹：客户端控制台安装程序的下载路径。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp”<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> .fo文件的路径。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> SOAP路由器的URL(http://myserver/xxx、http://jni或mailto:xxx)。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

**web > jsp > classpath**&#x200B;节点包含启动JVM时要使用的所有类路径的列表。 以下是默认配置：

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

以下是&#x200B;**web > jssp**&#x200B;节点的不同参数。 这是JSSP使用的参数的配置。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> 在每个查询后启用JavaScript上下文的垃圾回收器。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> JavaScript上下文提供的最大页面数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

**web > jsp > classpath**&#x200B;节点包含启动JVM时要使用的所有类路径的列表。

### 中继 {#relay-2}

以下是&#x200B;**web > relay**&#x200B;节点的不同参数。 这是两个区域之间HTTP请求的中继配置。

有关其他信息，请参阅此[部分](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> 在调试模式下启动Web服务器中的HTTP中继模块。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> 禁止字符（域）：URI的“authority”部分中禁止字符的列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '.#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> 禁止字符（路径）：URI的“路径”部分中的禁止字符列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> “mod_dir”模块选项的值：文件夹查询时要使用的文件列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “index.md”<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> 启动HTTP中继模块。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> 在Web服务器中启动HTTP中继模块。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 在删除禁止的url之前等待时间。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “60”<br /> </td> 
  </tr> 
 </tbody> 
</table>

使用以下参数为每个要中继的URL添加&#x200B;**web > relay > url**&#x200B;节点（插入顺序定义优先级）。

有关其他信息，请参阅[动态页面安全和中继](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays)和[部分](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> 授权IP:允许此掩码使用中继的源IP地址列表（以逗号分隔）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> deny<br /> </td> 
   <td> 拒绝访问这些URL（返回HTTP 403错误）<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> 要中继的DNS别名：要中继的DNS别名掩码列表（以逗号分隔）(例如：'*.adobe.com')。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> 无论安全区域（如webApps）如何，都会授权HTTP访问。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> 添加原始主机：中继时使用原始请求的HTTP“Host”标头。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> 添加初始URL路径：附加要中继到目标页面URL的完整路径。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> 公共资源的同步状态（枚举）。 可能的值为“normal”（正常执行）、“blacklist”（在出现错误404时添加到的URL）和“spare”（如果存在，则在备用服务器上传文件）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> 目标页面的URL:请参阅<a href="configure-tomcat.md" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 正在中继的请求的最大执行时间（以秒为单位）。<br /> </td> 
   <td> 长<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> 要中继的URL掩码(例如：'/nl*', '*.jsp')。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是默认配置：

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

为每个HTTP标头添加一个&#x200B;**web > relay > responseHeader**&#x200B;节点，以添加转发到中继的回复。

有关其他信息，请参阅[管理HTTP标头](../../installation/using/configuring-campaign-server.md#managing-http-headers)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 标头名称<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> 标头值<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是默认配置：

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### 重定向 {#redirection}

以下是&#x200B;**web >重定向**&#x200B;节点的不同参数。 这是重定向模块的配置。

有关其他信息，请参阅此[部分](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Identity Management系统(IMS)组织标识符：Adobe Experience Cloud中的唯一组织标识符，特别用于VisitorID服务和IMS SSO。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> 描述用于永久性Cookie的策略的值（与P3P Compact Policy格式兼容）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “CAO DSP COR CUR A DEVa TAIa我们的总线IND UNI COM NAV”<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> 要配置以明确指示要设置Cookie的域的逗号分隔域列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> 与跟踪实例关联的数据库标识符。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> 按调用记录计数：在调用方法GetTrackingLogs时默认返回的日志数。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> 过期重定向的页面：重定向服务器在投放操作的重定向过期时默认使用的网页URL。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> 最大作业计数：缓存中投放操作的最大数量。 不能低于50。 <br /> </td> 
   <td> 长<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> 启动重定向服务。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> 在模块模式下启动重定向服务。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Web跟踪：为未知用户访问的页面创建日志。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> 重定向服务器使用的密码。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是&#x200B;**web > redirection > spareServer**&#x200B;节点的不同参数。

有关其他信息，请参阅[冗余跟踪](../../installation/using/configuring-campaign-server.md#redundant-tracking)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> 在以下情况下，请考虑：如果表达式返回true，则会考虑跟踪服务器。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> 名称<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 额外的重定向服务器URL<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

以下是&#x200B;**web > spamCheck**&#x200B;节点的不同参数。 这是电子邮件防垃圾邮件评分评估参数的配置。

有关其他信息，请参阅[配置SpamAssassin](../../installation/using/configuring-spamassassin.md)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 命令<br /> </td> 
   <td> 用于评估电子邮件的防垃圾邮件得分的命令(例如'perl spamcheck.pl')。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

以下是&#x200B;**wfserver**&#x200B;节点的不同参数。 这是工作流进程配置。

有关其他信息，请参阅[高可用性工作流和相关性](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

<table> 
 <thead> 
  <tr> 
   <th> 参数 </th> 
   <th> 说明 </th> 
   <th> 类型 </th> 
   <th> 默认值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> affinity<br /> </td> 
   <td> 亲和度<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动启动<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 句点<br /> </td> 
   <td> 长<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的JavaScript ID。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以Mb为单位）的警告。<br /> </td> 
   <td> 长<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知中继：HostName：启用通知中继的端口。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间。 请参阅<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “06:00:00” <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 开始时的优先级。 低优先级模块首次启动和最后停止。 因此，syslogd模块的优先级必须为0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
