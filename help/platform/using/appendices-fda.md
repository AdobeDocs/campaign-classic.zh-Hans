---
title: 附录
seo-title: 联合数据访问附录
description: 联合数据访问附录
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 0%

---


# 附录 {#fda-appendices}

## Teradata其他配置 {#teradata-configuration}

### 兼容性 {#teradata-compatibility}

**基于Unicode**

| 数据库版本 | 驱动程序版本 | 所需的最低活动版本 | 注释 |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic17.9 | 在Linux下：具有时间戳的查询可能会失败（在内部版本8937中修复为18.4，在版本8977中修复为18.10）在调试模式下，可能会出现与驱动程序中内存使用不良相关的警告。 |
| 15 | 16 | Campaign Classic17.9 | 建议在Linux下设置Teradata 15数据库。 |
| 16 | 16 | Campaign Classic18.10 | 未完全处理带代理对的Unicode字符。 在数据中使用替代字符应可行。 在查询的筛选条件下使用代理不进行此更改是行不通的。 |
| 16 | 15 | 不支持 |   |

**基于拉丁语1**

Adobe Campaign Classic17.9之前的版本仅支持Teradata Latin-1数据库。

从Adobe Campaign Classic17.9开始，我们现在默认支持Unicode中的Teradata数据库。

具有Latin-1 TeradataCampaign Classic库迁移到最新外部帐户版本的客户必须在选项中添加参数APICharSize=1。

### 数据库配置 {#database-configuration}

#### 用户配置 {#user-configuration}

需要以下权限：创建／删除／执行自定义过程，创建／删除／插入／选择表。 如果要在Adobe Campaign实例上使用md5和sha2函数，则可能还必须创建用户模式函数。

确保配置正确的时区。 它应与在外部帐户实例中创建的Adobe Campaign中将设置的内容匹配。

Adobe Campaign不会为它将在数据库中创建的对象设置保护模式（回退）。 您可能需要为Adobe Campaign使用以下查询连接Teradata数据库时使用的用户设置默认值：

| 禁用默认回退 |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### MD5安装 {#md5-installation}

如果要在Adobe Campaign实例中使用md5函数，则必须从此页面(md5_20080530.zip)在Teradata [库](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) 上安装用户模式函数。

下载文件的sha1如下所示：65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e。

安装md5:

1. 解压缩md5_20080530.zip文件。

1. 转到md5/src目录。

1. 使用它们连接到Teradata数据库。

1. 运行以下betq命令：

   ```
   .run file = hash_md5.btq
   ```

#### SHA2安装 {#sha2-installation}

如果要在Adobe Campaign实例中使用sha2函数，则必须从此页(teradata-udf-sha2-1.0.zip)在Teradata [库](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) 上安装用户模式函数。

下载文件的sha1如下所示：e87438d37424836358bd3902cf1adeb629349780。

安装sha2:

1. 解压缩teradata-udf-sha2-1.0.zip文件。

1. 转到teradata-udf-sha2-1.0/src目录。

1. 使用它们连接到Teradata数据库。

1. 运行以下两个beq命令：

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### UDF_UTF16TO8安装 {#UDF-UTF16TO8-installation}

如果要在Adobe Campaign实例中使用udf_utf16to8函数，则必须从此页的 **Teradataunicode工具包** ( [](https://downloads.teradata.com/download/tools/unicode-tool-kit) utk_release1.7.0.0.zip)在Teradata库上安装用户模式函数。

下载文件的sha1如下所示：e58235f434f52c71316a577cb48e20b97d24f470。

安装udf_utf16to8:

1. 解压缩utk_release1.7.0.0.zip文件。

1. 在提取的文件中查找udf_utf16to8.o，然后导航到包含该文件的目录。 它应命名为utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/。

1. 使用它们连接到Teradata数据库。

1. 键入以下beq命令：

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   ```

### 活动服务器Linux配置 {#campaign-server-linux}

驱动程序安装需要以下各项：

* Teradata ODBC驱动程序，可在本页中找 [到](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata工具和实用程序（用于批量加载），可在本页中找 [到](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

文件名和sha1:

* tdobc1620_linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44

* TeradataToolsAndUtilitiesBase_linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbaa6f8639387b19c563

如果Linux分发没有包，则可以按照CentOS 7中的说明进行安装（例如使用docker），然后将/opt/teradata的内容复制到Adobe Campaign服务器上。

#### ODBC驱动程序安装 {#odbc-installation}

安装ODBC驱动程序：

1. 解压tdodbc1620__linux_indep.16.20.00.00-1.tar.gz文件。

1. 转到tdobc1620目录。

1. 您可能需要修复安装脚本：

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. 运行setup_wrapper.sh。

#### Teradata工具和实用程序安装 {#teradata-tools-installation}

安装工具：

1. 解压TeradataToolsAndUtilitiesBase_linux_indep.16.20.01.00.tar.gz文件。

1. 转至TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu目录。

1. 运行setup_wrapper.sh。

1. 转至TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2目录。

1. 运行setup_wrapper.sh。

1. 转至TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase目录。

1. 运行setup_wrapper.sh。

1. libtelapi.so文件应在/opt/teradata/client/16.20/lib64中可用。

#### 驱动程序配置 {#driver-configuration}

To learn more on driver configuration, refer to this [section](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### 环境变量 {#environment-varaiables}

要进一步了解环境服务器的Adobe Campaign变量，请参阅本 [节](../../platform/using/legacy-connectors.md#configure-access-to-teradata)。

### 活动Windows服务器配置 {#campaign-server-windows}

您首先需要下载Teradata Tools和Windows实用程序。 您可以从此页面下 [载](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

确保安装ODBC驱动程序和Teradata Parallel Transporter基础。 它将安装telapi.dll，用于在Teradata数据库上进行批量加载。

确保驱动程序和实用程序的路径位于nlserver在执行过程中将具有的PATH变量中。 默认路径为C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\项目Files\Teradata\Client\15.10\bin on 64 bit)。

### 外部帐户疑难解答 {#external-account-troubleshooting}

如果测试连接时出现以 **下错误TIM-030008日期“2”:缺少字符(iRc=-53)** ，请确保正确安装ODBC驱动程序，并为活动服务器设置LD_LIBRARY_PATH(Linux)/PATH(Windows)。

错误 **ODB-240000 ODBC错误：[找不到][ODBC Driver Manager]Microsoft数据源名称，未指定默认驱动程序。** 如果使用16.X驱动程序，则出现在Windows中。 Adobe Campaign希望在odbcinst.ini中将teradata命名为“{teradata}”。
如果您有18.10Adobe Campaign服务器版本，可在外部帐户选项中添加ODBCDriverName=&quot;Teradata数据库ODBC驱动程序16.10&quot;。 版本号可以更改，可以通过运行odbcad32.exe并访问“驱动程序”选项卡找到确切名称。
对于低于18.10的版本，您必须将驱动程序安装创建的odbcinst.ini的Teradata部分复制到名为Teradata的新部分，在这种情况下，可以使用regedit。

如果您的基数为latin1，则必须在选项中添加APICharSize=1。

### 时区 {#timezone}

Teradata使用的时区名称不是标准名称，您可以在Teradata站点上找 [到列表](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA)。 Adobe Campaign将尝试将外部配置中给定的时区转换为Teradata了解的时区。 如果找不到通信，则会话将找到衣柜GMT+X（或GMT-X）时区，日志中会显示警告。

转换完成后，将读取名为teradata_timezones.txt的文件，该文件应位于以下datakit目录中：/usr/local/neolane/nl6/datakit under linux. 如果编辑此文件，请确保与Adobe Campaign团队联系以更改源代码，否则，在下次活动更新期间将覆盖此文件。

使用-verbose开关运行nlserver时，将指示用于连接的时区，例如：

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

如果使用的时区不正确，则可以在外部帐户上添加名为“TimeZoneName”的选项。 在这种情况下，请使用Teradata值，例如“TimeZoneName=Europe Central”。

在Teradata文档中使用批量加载或“快速加载”时，活动无法指示时区。 因此，建议设置活动用来连接的用户的默认时区：

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## MySQL 5.7配置 {#mysql-57-configuration}

### 服务器配置 {#server-configuration-mysql}

服务器配置不需要任何特定的安装步骤。 Adobe Campaign应使用latin1数据库（MySQL上的默认数据库）或unicode数据库。

### 驱动程序安装 {#driver-installation-mysql}

#### Debian {#debian-mysql}

从此页下载mysql-apt-config. [deb](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en)。

安装客户端库：

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

从此页面下载C连 [接器](https://dev.mysql.com/downloads/connector/c)。 我们建议下载版本5.7。

确保将包含libmysqlclient.dll的目录添加到nlserver将使用的PATH环境变量中。

#### CentOS {#centos-mysql}

从本页下载mysql57-community-release.noarch. [rpm](https://dev.mysql.com/downloads/repo/yum)。

安装客户端库：

$ yum install mysql57-community-release-el7-9.noarch.rpm$ yum install mysql-community-libs

### 外部帐户配置 {#external-account-mysql}

外部帐户配置不需要任何特定步骤。 确保根据数据库设置时区和使用Unicode数据。
