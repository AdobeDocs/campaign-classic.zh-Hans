---
product: campaign
title: 服务器配置文件
description: 服务器配置文件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '7979'
ht-degree: 39%

---

# 服务器配置文件{#the-server-configuration-file}



Adobe Campaign的整体配置在 **serverConf.xml** 文件，位于 **conf** 安装目录的目录。 本节列出了 **serverConf.xml** 文件。

>[!NOTE]
>
>只能通过Adobe对由Adobe托管的部署执行服务器端配置。 要了解有关不同部署的更多信息，请参阅 [托管模型](../../installation/using/hosting-models.md) 或 [本页](../../installation/using/capability-matrix.md). 下面介绍了托管和混合型号的安装和配置步骤 [部分](../../installation/using/hosting-models.md).

第一个参数位于 **共享** 节点。 这些值与实例相关。 所有nlserver命令（nlserver web、nlserver wfserver等）都可能使用它们。 其他部分与特定nlserver子命令相关。

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

以下是 **身份验证** 节点：

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
   <td> 启用 IP 地址检查.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> 默认识别模式.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “nl”<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> 长会话超时（以秒为单位）.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> 安全令牌超时（以秒为单位）.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> 缓存持续时间：会话信息的缓存时间（以秒为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> 会话超时（以秒为单位）.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

以下是 **authentication > XTK** 节点：

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
   <td> 内部帐号的密码.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> 内部帐户安全区：内部帐户的授权区域。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “lan”<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

以下是 **dataStore** 节点。 这是定义服务器数据源的位置。

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
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 主机<br /> </td> 
   <td> DNS掩码：此实例提供的DNS掩码列表(以逗号分隔，可使用*和？ 模式)。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> 交互JSSP缓存过期延迟：超时时间（以秒为单位），在此时间后，缓存条目将失效。 负值表示缓存始终无效。 “0”、空值或无效值被视为60。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> 朗<br /> </td> 
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
   <td> 要下载的授权文件，用“,”分隔。字符串必须是有效的常规 Java 表达式。请参阅 <a href="file-res-management.md" target="_blank">限制可上载的文件</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> 将密钥存储在保管库中：使用Hashicorp Vault。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> 保险库中的密码路径<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “/v1/secret/campaign/”<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> 包含保险库令牌的文件的本地路径. $(HOME)可以在此路径中使用（但不能用到其他env变量）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “$(HOME)/.vaulttoken”<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp 保险库 URL <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 视图缓存的有效期：超时时间（以秒为单位），在此时间后，缓存条目将失效。 负值表示缓存始终无效。 “0”、空值或无效值被视为60。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> 工作目录的 XPath。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> workingDirectory :工作目录的XPath。 默认：“$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/”<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

以下是 **dataStore > proxyAdjust** 节点。 根据 urlBase 中定义的 URL 重新生成匹配正则表达式的 URL.

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
   <td> 生成外部 URL 时使用的基础。例如：https://server.domain.com<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 用于匹配 URL 的正则表达式。例如：http://server\.lan\.net.*<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

以下是 **dataStore > dataSource** 节点。

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
   <td> 默认<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **dataStore > dataSource > dbcnx** 节点，配置连接设置：

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
   <td> Unicode 存储<br /> </td> 
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
   <td> 加密<br /> </td> 
   <td> 加密的密码<br /> </td> 
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
   <td> 提供程序<br /> </td> 
   <td> 类型（枚举）。 可能的值包括：“Oracle”、“MSSQL”(Microsoft SQL Server)、“PostgreSQL”(PostgreSQL)、“Teradata”、“DB2”、“MySQL”、“Netezza”、“AsterData”、“SAPHANA”(SAP HANA)、“RedShift”(Amazon Redshift)、“ODBC”(SybaseASE，Sybase IQ)、“中继”（HTTP到远程数据库）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> 服务器<br /> </td> 
   <td> 服务器<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 时区<br /> </td> 
   <td> 时区：请参阅 <a href="../../installation/using/time-zone-management.md" target="_blank">时区管理</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> 数据库中的 Unicode 数据<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> 带时区的日期字段：请参阅 <a href="../../installation/using/time-zone-management.md" target="_blank">时区管理</a>.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

在 **dataStore > dataSource > sqlParams** 节点，配置SQL参数：

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

在 **dataStore > dataSource >池** 节点，配置关联连接池的参数：

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
   <td> 短整型<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> 池中保留的空闲连接的数目.<br /> </td> 
   <td> 短整型<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> 拒绝新连接之前允许的连接的最大数目。请参阅 <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">技术说明</a>.<br /> </td> 
   <td> 短整型<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> 连接的最大空闲时间。0 表示默认值.<br /> </td> 
   <td> 短整型<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

以下是 **dataStore > virtualDir** 节点。 这是虚拟目录到实际目录映射的配置。

有关其他信息，请参阅 [管理公共资源](file-res-management.md).

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
   <td> 虚拟目录的名称 <br /> </td> 
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

以下是 **dataStore > precossCommand** 节点。 这些是用于预处理“加载文件”工作流活动的授权命令。

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
   <td> 命令行 <br /> </td> 
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

以下是 **dnsConfig** （DNS配置）节点。

有关其他信息，请参阅 [部分](../../installation/using/configuring-campaign-server.md).

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
   <td> 域名：默认域名。 由SMTP HELO命令使用。 默认情况下，使用在Windows中声明的第一个网络接口的网络参数；或在Linux（域或搜索条目）下解析file/etc/resolv.conf。 <br /> </td> 
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
   <td> DNS 查询的重试次数.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> 超时<br /> </td> 
   <td> DNS 查询的超时时间（以毫秒为单位）.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>注释 **nameSevers**:默认情况下，使用网络
>在Windows中声明的第一个网络接口的参数
>未在UNIX中定义。 定义域名服务器(DNS)
>MTA用来获取为
>域。
>
>如果未定义此值，MTA将在主机网络配置中搜索此信息。 如果可以使用多个DNS，则不同的DNS地址必须用逗号分隔(例如：212.155.207.1,212.155.207.2)。 如果您的投放服务器具有多个网络接口，则MTA使用的DNS列表是第一个。 在这种情况下，我们建议将 **nameServer** 参数来避免任何歧义。

>[!CAUTION]
>
>如果网络主机配置使用DHCP，则MTA将找不到DHCP提供的DNS列表。 在这种情况下，我们建议在Windows控制面板的网络参数中指定DNS列表。

## 执行 {#exec}

以下是 **执行** （命令执行）节点。

有关其他信息，请参阅 [限制授权的外部命令](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

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
   <td> 包含要添加到的命令的文件的路允许列表径。 <br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户<br /> </td> 
   <td> 以其他用户的身份执行命令.<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

以下是 **htmlToPdf** 节点。 这是将网页转换为PDF文档的服务配置。

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
   <td> 最大值. 一台计算机上一次允许的转换进程数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 模式<br /> </td> 
   <td> 用于转换的工具。 可能的值包括：phantomjs， wkhtmltopdf，其他，已禁用<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “phantomjs” <br /> </td> 
  </tr> 
  <tr> 
   <td> 超时<br /> </td> 
   <td> 转化超时：最大转化时间（以秒为单位）。 超出此阈值后，转换过程将停止，并引发错误。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> 详细<br /> </td> 
   <td> 详细模式：以详细模式启动，以诊断可能的错误。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> 等待进程时的延迟：延迟（以秒为单位）。 如果超出此延迟，则停止转换并引发错误。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Phantomjs的示例：

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

以下是 **ims** 节点。 这是Campaign使用连接到其他服务的配置 [IMS](../../integrations/using/about-adobe-id.md).

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
   <td> 客户端 ID<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> 密钥（已使用 AES 进行加密）<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> 授权代码（已使用 AES 进行加密）<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> IMS 服务器 URL<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> 技术帐户客户端 ID<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> 技术帐户密钥（已使用 AES 进行加密）<br /> </td> 
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
   <td> 技术帐户私钥（已使用 AES 进行加密）<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

以下是 **javaScript** 节点。 这是JavaScript解释器的配置。

有关其他信息，请参阅 [报表文档](../../reporting/using/actions-on-reports.md#memory-allocation).

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
   <td> 运行垃圾收集器之前的最大大小（以 MB 为单位）.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> 每个堆栈块的大小（以 kilo octet 为单位）. 这是一个内存管理调整参数，大多数用户都不应该调整此参数。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

以下是 **mailExchanger** 节点。 这是SMTP服务器的配置。

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
   <td> SMTP服务器：用于传输电子邮件的SMTP服务器的IP地址。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> 用于电子邮件传输的 SMTP 服务器的 TCP 端口。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模块 {#module}

以下是 **模块** 节点。 这是命名空间限制模块xtk的配置。

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
   <td> 创建新实体时使用的默认命名空间.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “cus”<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 监测 {#monitoring}

以下是 **监测** 节点。 这是监视服务配置。

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
   <td> 长整型<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> 监控服务运行的 Unix 脚本.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> 要由监控服务执行的 Windows 脚本.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 乌孔夫 {#ooconv}

以下是 **乌孔夫** 节点。 这是文档转换服务器的配置。

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
   <td> 允许 OpenOffice 服务器执行的最大转换次数。如果超过此数目，服务器将重新启动。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> 强制关闭前 OpenOffice 服务器的最大空闲时间。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> OpenOffice 服务器用于侦听的端口的间隔.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 文档转换服务器的 URL.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

以下是 **proxyConfig** 节点。 这是代理参数的配置。

有关其他信息，请参阅 [代理连接配置](file-res-management.md).

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
   <td> 已启用<br /> </td> 
   <td> 使用代理服务器.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 覆盖<br /> </td> 
   <td> 例外：应忽略代理参数的地址列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 唯一代理服务器：对所有类型的代理使用相同的配置。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP代理/安全代理 {#http-proxy---secure-proxy-}

在 **proxyConfig > HTTP代理/安全代理** 节点，请配置以下参数。

有关其他信息，请参阅 [代理连接配置](file-res-management.md).

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
   <td> 用于连接代理服务器的登录名<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 密码<br /> </td> 
   <td> 用于连接代理服务器的密码<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 代理服务器端口<br /> </td> 
   <td> 短整型<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

以下是 **threadPool** 节点。

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
   <td> 池中的最大线程数。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

以下是 **urlPermission** 节点。 这是Javascript代码可访问的URL列表。

域和正则表达式列表，用于指定在Javascript代码中遇到的URL是否可以由Adobe Campaign服务器使用。

如果找不到URL，则会根据指定的默认模式执行默认操作。

有关其他信息，请参阅 [外连接保护](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> 如果URL不在授权列表（枚举）中，则执行默认操作。 可能的值包括“忽略”（授权时不显示警告消息，这要求禁用保护）、“警告”（授权并发出警告消息）和“拒绝”（禁止访问URL）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 拒绝<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> 调试URL选择机制的跟踪：在URL验证过程中发出其他消息。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

对于每个URL，添加 **url** 节点（具有以下参数）：

有关其他信息，请参阅 [外连接保护](../../installation/using/configuring-campaign-server.md#url-permissions).

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

如果记录满足 **dnsSuffix** 但不是 **urlRegEx**，将检查以下记录。

例如，要授权访问域business.com的所有URL，我们可以定义两条记录：

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

和

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

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
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

以下是 **xtkJobs** 节点。 这是服务器作业的配置。

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
   <td> 长整型<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 存档 {#archiving}

以下是 **存档** 节点。 这是后台执行的存档操作的配置。

有关其他信息，请参阅 [激活电子邮件存档（内部部署）](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

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
   <td> 要同时处理的 EML 的数量<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> 已发送消息的存档策略（枚举）。 可能的值为“0”（无存档）和“1”（将已发送邮件的存档传输到SMTP服务器）。<br /> </td> 
   <td> 字节<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> 压缩存档的大小：压缩存档中的最大文件数。<br /> </td> 
   <td> 长整型<br /> </td> 
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
   <td> 未处理电子邮件自动存档之前的延迟：未处理的电子邮件存档前的天数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> 每个更新事件之间的延迟（以秒为单位）.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 删除未处理的电子邮件之前的天数.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
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
   <td> 激活SMTPS支持：在远程服务器支持时，激活以安全模式(STARTTLS/SMTPS)发送电子邮件。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> 与归档 SMTP 服务器的连接数.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> 要使用的SMTP中继的DNS名称或IP地址列表（以逗号分隔）。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> SMTP 服务器的 IP 端口。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

以下是 **inMail** 节点。 这是入站电子邮件管理模块的配置。

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
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> 验证实例名称：如果为true，则消息ID标头中包含的Adobe Campaign实例名称必须与当前实例相同。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> 转发地址：规则未处理默认电子邮件传送地址。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> 错误地址：用于传输无效电子邮件的默认地址（MIME编码错误）。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> 忽略消息大小：用于忽略POP3服务器返回的消息的大小。 在这种情况下，模块需要“。” 消息的结尾。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 消息读取期：消息队列轮询频率。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> 要更新的日志数上限：定义在更新数据库之前要保留在内存中的日志消息的最大数量。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> 要在 POP3 会话期间读取的消息的最大数目。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 会话持续时间：消息处理会话的最长持续时间。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3轮询期<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> 读取消息的队列大小<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> 与POP3服务器的通信超时。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> 要轮询的帐户的数据库重新加载频率。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

在 **inMail > msgDump** 节点，请配置以下参数。 这是已处理消息的转储配置。

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
   <td> 转储<br /> </td> 
   <td> 以文本格式保存所有入站消息。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
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

以下是 **interactiond** 节点。 这是入站交互事件的写入守护程序的配置。

有关其他信息，请参阅 [交互 — 数据缓冲区](../../installation/using/interaction---data-buffer.md).

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
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> 最大值. 共享内存中用于调用数据的字符数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> 最大值. 共享内存中存储的事件数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> 在建议之后直接排序的合格优惠的最大数量，用于存储以供统计.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 响应时间统计的聚合持续时间（以秒为单位）. 0表示已停用统计存储。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> 最大值. 存储在共享内存中用于识别个人的字符数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

以下是 **mta** 节点。 这是投放代理的配置。

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
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '-tracefilter:nlmta <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> 保存已发送电子邮件的路径：如果不为空，则保存已发送电子邮件的所有源文件的路径。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> 转储目录：如果不为空，则复制此目录中已发送邮件的MIME信封。 用于故障排除。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS查询日志延迟：显示日志的时间（以毫秒为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> 错误统计频率：在数据库中生成统计信息和存储之间的时间。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> 生成错误统计信息并将其存储在数据库中。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> 显示日志消息的级别。写入数据库的日志的严重性级别。 由MTA生成的日志消息并非总是写入数据库中。 通过此参数，您可以定义在数据库中必须写入消息的级别。 如果定义级别2，则也会写入级别1和0的消息，而如果定义级别1，则只会写入级别1和0的消息。 可能的值包括：0（错误）、1（警告）、2（信息）<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> mta 进程可使用的最大内存大小（以 MB 为单位）。在超出此限制时，进程将重新启动，以便为系统释放它占用的内存。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 要考虑的连接阈值. 如果 errorPeriodSec 指定的时段内的连接总数完全低于阈值，则不会为给定路径生成错误统计信息。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> 要考虑的错误阈值：如果errorPeriodSec指定时段的错误总数严格低于阈值，则不会为给定路径生成错误统计信息。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> 要考虑的消息阈值. 如果 errorPeriodSec 指定的时段内的已发送消息总数完全低于阈值，则不会为给定路径生成错误统计信息。<br /> </td> 
   <td> 长整型<br /> </td> 
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
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> 删除已存档电子邮件之前的延迟：清除dataLogPath中指定目录中的已存档电子邮件前间隔的天数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> 重试丢失的消息：如果子进程已停用，将重试部分投放。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> 启用签名机制。 这可提高电子邮件中跟踪链接的安全性。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> 投放统计服务器的地址，给定为 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. 请参阅 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">统计服务器的坐标</a>. 
      <br /> 
     </td> 
   <td> 字符串<br /> </td> 
   <td> 如果未定义，则默认端口为7777。<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSupport<br /> </td> 
   <td> 按域启用TLS:启用可由MX配置的TLS（需要最新的统计服务器）。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真 <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> 使用的协议版本：通信协议版本（v5.11和6.0.2服务器为1,v6.1服务器为2）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 如果未定义，则使用最新版本。 <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> 如果设置为“true”，则您的实例将使用 <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">增强的MTA</a>.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> 验证模式：激活验证模式(不进行报文的物理传输；用于模拟和测试)。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
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
   <td> 'nlserver，内部版本$(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

在 **缓存** 节点，请配置以下参数。 这是本地文件缓存配置。

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
   <td> 在以下情况下回收：句点，以秒为单位，此后将自动从缓存中删除文件以回收存储。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> 最大缓存大小 (Mb)。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> 清除频率：执行缓存清除机制之间的时段（以秒为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中继 {#relay}

在 **mta >中继** 节点，请配置以下参数。 这是邮件投放的邮件服务器配置。

该列表的处理方式与MX DNS查询返回的MX列表相同，通常只要第一个MX可用，就使用下一个MX，依此类推。

有关其他信息，请参阅 [SMTP中继](../../installation/using/configuring-campaign-server.md#smtp-relay).

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
   <td> 要使用的SMTP中继的DNS名称或IP地址列表（以逗号分隔）。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> SMTP 服务器的 IP 端口。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 主控 {#master}

在 **mta >主控** 节点，请配置以下参数。 这是主服务器的配置。

有关其他信息，请参阅 [部分](../../installation/using/configuring-campaign-server.md#mta-child-processes).

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
   <td> 要投放的作业的数据库轮询频率。该值表示数据库轮询频率（以秒为单位）。为了获得等待投放的作业列表，MTA 会定期轮询数据库。当没有作业等待时，轮询周期由该值定义。否则，如果作业已转移到子服务器，则此轮询持续时间会自动减少到一秒，以便可以尽快再次处理新作业，即一旦子服务器再次可用。这并不意味着数据库查询将每秒进行一次，直到子服务器再次可用。事实上，只有在至少有一个子服务器可用时才进行数据库访问。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> 数据库连接失败后的等待时段。数据库连接失败通常是因数据库服务器自身导致的。例如，服务器也可能出于维护目的而停止。DataBaseRetryDelay 参数定义在数据库连接失败的情况下两次连接尝试之间的持续时间。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 私钥 (DomainKeys) 缓存的有效期。用于根据 DomainKeys 建议 (http://antispam.yahoo.com/domainkeys) 签署电子邮件的私钥作为选项存储在数据库中。domainKeysReloadPeriodSec 参数定义 MTA 可将这些密钥保存在缓存中的时间（以秒为单位）。在此延迟之后，必须从数据库中重新加载所有密钥。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> 最大子服务器数。表示运行的服务器的最大数量。建议将此数量限制在与服务器内存资源兼容的最佳值。这可以在投放期间进行检查。使用的内存不应超过可用物理内存的三分之一，否则将使用交换。请参阅 <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA子进程</a>.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> 最小子服务器数。MTA 尝试至少保持此数量的服务器运行。如果少于此值，它会每秒重新启动新服务器一次，直至达到此值。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 启动时的子服务器的数量。动态监控子服务器数量；当 MTA 启动时，它会创建此值所指示数量的子服务器。通常，为了节省主机资源，子服务器的启动速度不能超过每秒一台服务器。但是，当 MTA 启动时，该限制将被取消，以便尽快提供子服务器。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 孩子 {#child}

在 **mta >子项** 节点，请配置以下参数。 这是子服务器的配置。

有关其他信息，请参阅 [电子邮件发送优化](../../installation/using/email-deliverability.md#email-sending-optimization).

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
   <td> 可选命令行参数 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 超时，直到空闲子服务器停止。如果子服务器的空闲时间大于此参数，它会自动终止以释放主机资源。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> 最长消息保留时间。如果准备好的消息因限制而无法发送或无法连接到目标 MTA，则该消息将被放弃并在下次重试时进行处理。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> 每个子服务器向 FCM 发出的并行 Http 请求的最大数量.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> 每个子服务器的最大消息计数。每个 MTA 子级均将处理此数量的消息并终止。请务必指定一个数字，以使 MTA 中的内存或资源泄漏不会造成损害（通常为几千）。即使 MTA 代码中没有已知的内存泄漏，嵌入式 JavaScript 和 XSL 引擎也不是完全可靠的。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 待处理消息：内存中待发送消息的最大数量。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 子进程可使用的最大内存大小(MB)。超出此限制后，进程将停止，以便它使用的内存将释放到系统。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 放弃投放连接器的 SOAP 连接后的超时（以秒为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> 始终从优先级最高的 MX 开始.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> 恢复时连续尝试的最大次数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子> smtp** 节点，请配置以下参数。 这是SMTP会话的配置。

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
   <td> 在远程服务器支持时以安全模式 (STARTTLS/SMTPS) 激活电子邮件投放。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> 空闲会话超时。仅当会话被重新用于将多条消息传输到给定域时使用此参数。当 MTA 完成消息传输时，它使用的 SMTP 会话不会系统地关闭。如果消息已准备好发送到同一个域，则将重复使用同一 SMTP 会话，这就是会话不会自动关闭的原因。利用 IdleSessionTimeout 参数，您可以定义 SMTP 会话可保持活动状态以等待另一条消息的时间。一旦该持续时间结束，会话将自动关闭。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> 重试连接前的初始延迟. 每次连接失败时，此延迟都会加倍。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 子服务器的 SMTP 会话的最大数目。为了投放消息，MTA 初始化与收件人 MTA 的 SMTP 连接。给定子服务器的最大并发和活动 SMTP 会话数受此值限制。如果将此值乘以 maxSpareServers，则可以得到给定子服务器可以同时处理的消息的最大数量。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子项> smtp > IPAfinity** 节点，请配置以下参数。 这是使用IP地址管理用于优化传出SMTP流量的喜好的配置。

有关其他信息，请参阅 [要使用的IP地址列表](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) 和 [管理具有相关性的出站SMTP流量](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

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
   <td> 逻辑名称：用户链接到亲和度的名称。 名称用分号分隔；<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子项> smtp > IP** 节点，请配置以下参数。

有关其他信息，请参阅 [要使用的IP地址列表](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

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
   <td> 关联的物理地址。例如：“192.168.0.1”<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> 关联的公共地址 ID。用作统计信息服务器的密钥。必须是数字。请参阅此<a href="../../installation/using/email-deliverability.md#managing-ip-addresses">章节</a>。<br /> </td> 
   <td> 长整型<br /> </td> 
  </tr> 
  <tr> 
   <td> 权重<br /> </td> 
   <td> 指定此 IP 相对于其他 IPS 的使用频率（权重越大，频率越高）。<br /> </td> 
   <td> 长整型<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> 要包含的域掩码的逗号分隔列表.<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> 要排除的域掩码的逗号分隔列表.<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> 与 IP 地址关联的计算机名称。在发出 SMTP HELO 命令时使用。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

以下是 **nmac** 节点。 这是推送通知投放的配置。

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
   <td> useHTTProxy<br /> </td> 
   <td> 使用 shared/proxyHTTP 中定义的 HTTP 代理. <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中继 {#relay-1}

以下是 **nmac >中继** 节点。 这会配置对消息传递的中继的使用(ios http2 connector)。

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
   <td> 要使用的中继的DNS地址或名称。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 中继端口<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> 证书链（PEM 文件）。使用模拟服务器时很有用.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 流水线 {#pipelined}

以下是 **流水线** 节点。 这是Pipeline Services的事件处理模块的配置。

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
   <td> 保存公钥时在开发人员连接中生成的应用程序的名称。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> 用于获取网关令牌的 URL.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 用于获取令牌的私钥（在AES中使用XtkKey选项加密）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> 禁用身份验证：在未进行身份验证的情况下连接到Pipeline Services。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 用于发现管道服务 URL 的 URL.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> 状态保存期：进程内部信息保存在文件中的频率。 如果为0，则不活动。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 监听URL:强制管道服务的监听URL。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> 状态服务器端口：用于查询进程状态的HTTP服务器端口。 如果为0，则不活动。<br /> </td> 
   <td> 长整型<br /> </td> 
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
   <td> 存储指针之前的延迟：在此期间，指针将至少存储一次在数据库中（在活动不力时，此指针非常有用）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> 使用个性化的 JavaScript 连接器进行事件处理的线程数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> 事件处理的线程数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> 发生失败时处理之间的延迟.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 在此时段后放弃：如果在此时间段后处理仍然失败，请放弃事件。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 修复 {#repair}

以下是 **修复** 节点。 这是数据库修复模块的配置。

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
   <td> 交货操作修复模块：延迟（以分钟为单位），修复模块可在延迟后处理投放操作。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

以下是 **securityZone** 节点。

有关其他信息，请参阅 [定义安全区](../../installation/using/security-zones.md).

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
   <td> 为 Web 应用程序授权调试模式.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 授权用户在无法提供密码的情况下使用应用程序.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> 授权使用 HTTP 进行操作员登录.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjent<br /> </td> 
   <td> 授权在表达式中使用 SQLDATA.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> 授权用户/密码会话令牌.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> 标签<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 内部名称<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> 不要使用安全令牌.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> 显示错误详细信息<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
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

以下是 **securityZone > subNetwork** 节点。

有关其他信息，请参阅 [定义安全区](../../installation/using/security-zones.md).

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
   <td> label<br /> </td> 
   <td> 标签<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> 蒙版<br /> </td> 
   <td> 掩码或地址<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 内部名称<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> 代理<br /> </td> 
   <td> 此子网络用于访问实例的（反向）代理的掩码或地址。在此情况下，将测试“X-Forwarded-For”标头而不是此代理。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 短信 {#sms}

以下是 **短信** 节点。 这是入站短信管理模块的配置。

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
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> SMPP 连接器保存工作文件的最大天数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> SMPP 工作文件的最大大小（以 MB 为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 会话连续性框架的重复：max 两帧之间用于通知接收会话仍处于启用状态的时段（以秒为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> 搜索频率：短信帐户投票期。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> 帐户重新加载频率：要轮询的帐户的数据库重新加载频率。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> SR处理延迟的秒数：只有恢复日期早于当前时间的SR减去srReadDelay给定的持续时间（以秒为单位）。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 超时<br /> </td> 
   <td> 与短信网关的通信超时。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

以下是 **sms >网络大小** 节点。

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
   <td> 与 Netsize 建立连接时的超时（以秒为单位）.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

以下是 **stat** 节点。 这是MTA统计模块的配置。

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
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 端口<br /> </td> 
   <td> 服务器侦听端口. 请参阅此<a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">章节</a>。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

以下是 **syslogd** 节点。 这是日志管理模块的配置。

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
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> 日志文件的最大大小（以 Mb 为单位）. <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> 要保留的 logins.log 文件的最大数量. <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟踪 {#tracking}

以下是 **跟踪** 节点。 这是跟踪服务器的配置。

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
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> 禁用从以前的内部版本生成的格式错误的URL。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> 合并期<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> 删除重复的开口：删除重复的打开跟踪日志，以限制在Outlook等邮件阅读器中预览邮件的效果。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> 最多忽略X%的错误：只要尚未考虑的日记帐比率未达到此值，就不要更新跟踪指标。 <br /> </td> 
   <td> 字节<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> 更新错误指示器：重新计算错误指示器前的最大持续时间。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> 在以下期间计算指标：在投放有效日期之后的持续时间，在此之后将不再计算合并指标。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 通过调用远程跟踪服务器请求的日志数.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Phishbowl服务端点集成的API密钥。 这可保护从旧版本生成的格式错误的URL的重定向。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Phishbowl服务端点集成的端点。 这可保护从旧版本生成的格式错误的URL的重定向。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> 最多忽略X%的跟踪：只要尚未考虑的日记帐比率未达到此值，就不要更新跟踪指标。<br /> </td> 
   <td> 字节<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> 更新跟踪指标：重新计算跟踪指示器之前的最大持续时间。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> 浏览器标识符缓存的大小。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

以下是 **trackinglogd** 节点。 这是跟踪日志写入守护程序的配置。

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
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 最大写入重试数：在日志文件中写入失败时可以创建的文件的最大数量。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 最大日志大小：磁盘上日志使用的最大空间(MB)。 不能小于100 MB。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 最大日志计数：共享内存中存储的最大日志数。 不能少于10000。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 清除前的日志数：开始清除日志文件之前插入的日志数。 不得低于50000。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> 为额外的 Web 跟踪参数保存在共享内存中的最大字符数.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

以下是 **web** 节点。 这是Web模块的配置。

有关其他信息，请参阅 [部分](configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> 作为字符串传递的 JVM 选项。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> 最大线程数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> 最小线程数。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat监听控制端口：请参阅 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>.<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP侦听端口：请参阅 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>.<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SubmitDelivery调用的队列大小：可排队的SubmitDelivery SOAP调用的最大数量。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：有关给定进程消耗的RAM量（以MB为单位）的警告<br /> </td> 
   <td> 长整型<br /> </td> 
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
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> 在模块模式中启动 SOAP 路由器。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

以下是 **web > jsp** 节点。 这是JSP使用的参数的配置。

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
   <td> 调试<br /> </td> 
   <td> 是否在调试模式下执行 JSP.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> 下载文件夹：客户端控制台的安装程序下载路径。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp”<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> .fo 文件路径。<br /> </td> 
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

的 **web > jsp > classpath** 节点包含启动JVM时要使用的所有类路径的列表。 以下是默认配置：

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
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

以下是 **web > jssp** 节点。 这是JSSP使用的参数的配置。

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
   <td> 在每次查询后启用 JavaScript 上下文的垃圾收集器。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> JavaScript上下文提供的最大页面数。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

的 **web > jsp > classpath** 节点包含启动JVM时要使用的所有类路径的列表。

### 中继 {#relay-2}

以下是 **web >中继** 节点。 这是两个区域之间HTTP请求的中继配置。

有关其他信息，请参阅 [部分](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> 在调试模式下启动 Web 服务器中的 HTTP 中继模块.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> 禁止字符（域）：URI的“authority”部分中的禁止字符列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> 禁止字符（路径）：URI的“路径”部分中的禁止字符列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> “mod_dir”模块选项的值：在查询文件夹时要使用的文件列表。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> 启动 HTTP 中继模块.<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> 在Web服务器中启动HTTP中继模块。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> 超时<br /> </td> 
   <td> 删除禁止的 URL 之前的等待时间.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

添加 **web >中继> url** 用于每个要中继的URL的节点（插入顺序定义优先级），其参数如下。

有关其他信息，请参阅 [动态页面安全和中继](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 和 [部分](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> 拒绝<br /> </td> 
   <td> 拒绝访问这些 URL（返回 HTTP 403 错误）<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> 要中继的DNS别名：要中继的DNS别名掩码列表（以逗号分隔）(例如：“*.adobe.com”)。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> 无论安全区域（如webApps）如何，都会授权HTTP访问。 <br /> </td> 
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
   <td> 添加初始URL路径：附加要中继到目标页面URL的完整路径。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 状态<br /> </td> 
   <td> 公共资源的同步状态（枚举）。 可能的值包括“正常”（正常执行）、“黑名单”(在出现错误404时添加阻止列表到的URL)和“备用”（如果存在，则在备用服务器上上传文件）。<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 正常<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> 目标页面的URL:请参阅 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 超时<br /> </td> 
   <td> 被中继请求的最长执行时间（以秒为单位）.<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> 要中继的 URL 掩码（例如：“/nl*”、“*.jsp”）。<br /> </td> 
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

添加 **web > relay > responseHeader** 节点，用于向转发到中继的回复添加每个HTTP标头。

有关其他信息，请参阅 [管理HTTP头](../../installation/using/configuring-campaign-server.md#managing-http-headers).

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
   <td> 标头姓名<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
  <tr> 
   <td> 值<br /> </td> 
   <td> 标头值 <br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是默认配置：

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### 重定向 {#redirection}

以下是 **web >重定向** 节点。 这是重定向模块的配置。

有关其他信息，请参阅 [部分](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> 组织ID:Adobe Experience Cloud中的唯一组织标识符，尤其用于VisitorID服务和IMS SSO。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> 描述用于永久性Cookie的策略的值（与P3P Compact Policy格式兼容）。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> “CAO DSP COR CUR A DEVa TAIa我们的BUS IND UNI COM NAV”<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> 要配置以明确指示要设置Cookie的域的逗号分隔域列表。 <br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> 与跟踪实例关联的数据库标识符.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> 按调用记录计数：默认情况下，在调用方法GetTrackingLogs时返回的日志数。<br /> </td> 
   <td> 长整型<br /> </td> 
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
   <td> 最大作业计数：缓存中投放操作的最大数量。 不得低于50。 <br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIP<br /> </td> 
   <td> 如果设置为false，则r/test返回的响应中的sourceIP值将为空字符串。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> 启动重定向服务。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> 以模块模式启动重定向服务。<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Web跟踪：为未知用户访问的页面创建日志。 <br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> 重定向服务器使用的密码.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是 **web >重定向> spareServer** 节点。

有关其他信息，请参阅 [冗余跟踪](../../installation/using/configuring-campaign-server.md#redundant-tracking).

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
   <td> 在以下情况下，请考虑：如果表达式返回true，则会考虑跟踪服务器。 <br /> </td> 
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
   <td> 额外的重定向服务器 URL<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

以下是 **web > spamCheck** 节点。 这是电子邮件防垃圾邮件评分评估参数的配置。

有关其他信息，请参阅 [配置SpamAssassin](../../installation/using/configuring-spamassassin.md).

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
   <td> 用于评估电子邮件的防垃圾邮件得分的命令(例如“perl spamcheck.pl”)。<br /> </td> 
   <td> 字符串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

以下是 **wfserver** 节点。 这是工作流进程配置。

有关其他信息，请参阅 [高可用性工作流和相关性](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

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
   <td> 关联<br /> </td> 
   <td> 关联<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 阿尔格<br /> </td> 
   <td> 启动参数<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自动开始<br /> </td> 
   <td> 布尔值<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 期间<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 启动进程时要执行的 JavaScript 的 ID.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 内存消耗警报：有关给定进程所消耗的RAM量（以Mb为单位）的警报。<br /> </td> 
   <td> 长整型<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 内存消耗警告：警告给定进程消耗的RAM量（以Mb为单位）。<br /> </td> 
   <td> 长整型<br /> </td> 
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
   <td> 进程自动重新启动的时间. 请参阅 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自动进程重新启动</a>.<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 启动优先级. 低优先级模块首先启动和最后停止。因此 syslogd 模块的优先级必须为 0。<br /> </td> 
   <td> 短整型<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
