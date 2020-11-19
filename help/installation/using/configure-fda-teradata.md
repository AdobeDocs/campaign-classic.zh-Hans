---
title: 配置访问Teradata
description: 了解如何在联合数据访问配置访问Teradata
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 30eaabba8962c518c734cc4e9ad27065cfe9d467
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---


# 配置访问Teradata {#configure-access-to-teradata}

使用活动 [联合数据访问](../../installation/using/about-fda.md) (联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置访问Teradata。

1. 安装和配置 [Teradata驱动程序](#teradata-config)
1. 在Teradata中 [配置活动](#teradata-external) 外部帐户
1. 为Teradata [和活动服务器](#teradata-additional-configurations) 设置其他配置

## Teradata配置 {#teradata-config}

您需要为Teradata安装驱动程序，才能实现与活动的连接。

1. 为Teradata [安装ODBC驱动程序](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)。

   它由三个包组成，按照以下顺序可安装在Red Hat（或CentOS）/Suse上：

   * TeraGSS
   * tdicu1510（使用setup_wrapper.sh安装它）
   * tdobc1510（使用setup_wrapper.sh安装它）

1. 配置ODBC驱动程序。 配置可以在标准文件中执行： **/etc/odbc.ini** for general parameters and /etc/odbcinst.ini for scarting drivers:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;与odbcinst.ini文件的 **位置相对应** 。

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. 指定环境服务器的Adobe Campaign变量：

   * **LD_LIBRARY_PATH**:/opt/teradata/client/15.10/lib64和/opt/teradata/client/15.10/odbc_64/lib。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NLSPATH**:opermsgs.cat文件的位置(/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>在联合数据访问下连接到Teradata外部数据库需要在Adobe Campaign服务器上执行其他配置步骤。 [了解详情](#teradata-additional-configurations)。


## Teradata外部帐户{#teradata-external}

teradata外部帐户允许您将活动实例连接到Teradata外部数据库。

1. 从活动 **[!UICONTROL Explorer]**&#x200B;中，单 **[!UICONTROL Administration]** 击/ **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]** 并选 **[!UICONTROL External database]** 择为 **[!UICONTROL Type]**。

   ![](assets/ext_account_19.png)

1. 要配置 **[!UICONTROL Teradata]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:选择类 **[!UICONTROL Teradata]** 型。

   * **[!UICONTROL Server]**:您的Teradata服务器的URL或名称

   * **[!UICONTROL Account]**:用于访问Teradata数据库的帐户的名称

   * **[!UICONTROL Password]**:用于连接Teradata数据库的口令

   * **[!UICONTROL Database]**:数据库名称（可选）

   * **[!UICONTROL Options]**:通过Teradata的选项。 使用以下格式：“parameter=value”。 使用半列作为值之间的分隔符。

   * **[!UICONTROL Timezone]**:时区设定在Teradata。 [了解详情](#timezone)

### 查询条带

当多个Adobe Campaign用户连接到同一个联合数据访问 **[!UICONTROL Query banding]** Teradata外部帐户时，该选项卡允许您在会话中设置查询带，即一组键／值对。

![](assets/ext_account_20.png)

配置此选项后，每次活动用户对Teradata查询库执行时，Adobe Campaign都会发送元数据，元数据由与此用户关联的键列表组成。 此数据随后可由Teradata管理员用于审计或管理访问权限。

>[!NOTE]
>
>For more information on **[!UICONTROL Query banding]**, refer to the [Teradata documentation](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

要配置查询条带，请按照以下步骤操作：

1. 使用 **[!UICONTROL Default]** 输入默认查询带，在用户没有关联查询带时使用该带。 如果此字段留空，则没有查询带的用户将无法使用Teradata。

1. 使用字 **[!UICONTROL Users]** 段为每个用户指定查询带。 您可以添加所需数量的键／值对，如priority=1;workload=high。 如果用户未分配查询带， **[!UICONTROL Default]** 将应用该字段。

1. 选中该 **[!UICONTROL Active]** 复选框以激活此功能

#### 外部帐户疑难解答 {#external-account-troubleshooting}

如果测试连接时出现以 **下错误TIM-030008日期“2”:缺少字符(iRc=-53)** ，请确保正确安装ODBC驱动程序，并为活动服务器设置LD_LIBRARY_PATH(Linux)/PATH(Windows)。

错误 **ODB-240000 ODBC错误： [找不到][ODBC Driver Manager] Microsoft数据源名称，未指定默认驱动程序。** 如果使用16.X驱动程序，则出现在Windows中。 Adobe Campaign希望在odbcinst.ini中将teradata命名为“{teradata}”。

* 从活动18.10开始，可在外部帐户选项中添加ODBCDriverName=&quot;Teradata数据库ODBC驱动程序16.10&quot;。 版本号可以更改，可以通过运行odbcad32.exe并访问“驱动程序”选项卡找到确切名称。

* 如果您使用的是旧版活动，则必须将驱动程序安装创建的odbcinst.ini的“Teradata”部分复制到名为“Teradata”的新部分。 Regedit在此情况下可以使用。 如果您的基数为latin1，则必须在选 **项中添加** APICharSize=1。

## 其他配置 {#teradata-additional-configurations}

<!--
### Compatibility {#teradata-compatibility}

**Based in Unicode**

| Database version | Driver version |  Minimal Campaign version required |  Note |
|:-:|:-:|:-:|:-:|
| 15  |  15 |  Campaign Classic 17.9 | Under Linux: Queries with timestamp may fail (fixed in build 8937 for 18.4 and 8977 for 18.10) In debug mode, warnings relative to bad memory usage in the driver may occur. |
| 15  | 16  | Campaign Classic 17.9  | Recommended setup for a Teradata 15 database under Linux.  |
|  16 | 16  | Campaign Classic 18.10 |  Unicode characters with surrogate pairs are not fully handled. Using surrogate characters in data should work. Using surrogates in a filtering condition of a query will not work without this change. |
| 16  |  15 |  Campaign Classic 19.0 |  &nbsp; |

**Based in Latin1**

Versions previous to Adobe Campaign Classic 17.9 only supported Teradata Latin-1 database.

Starting from Adobe Campaign Classic 17.9, we now support by default Teradata database in Unicode.

Customers with a Latin-1 Teradata database migrating to a recent Campaign Classic release will have to add the parameter APICharSize=1 in the options of the external account.
-->

### 用户配置 {#user-configuration}

外部数据库需要以下权限：创建／删除／执行自定义过程，创建／删除／插入／选择表。 如果要在Adobe Campaign实例上使用md5和sha2函数，则可能还必须创建用户模式函数。

确保配置正确的时区。 它应与在外部帐户实例中创建的Adobe Campaign中将设置的内容匹配。

Adobe Campaign不会为它将在数据库中创建的对象设置保护模式（回退）。 您可能需要为Adobe Campaign使用以下查询连接到Teradata数据库的用户设置默认值：

| 禁用默认回退 |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### MD5安装 {#md5-installation}

如果要在Adobe Campaign实例中使用md5函数，则必须从此页面在Teradata库上安 [装](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) md5模式函数(md5_20080530.zip)。

下载文件的sha1如下所示：65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e。

安装md5:

1. 解压缩md5_20080530.zip文件。

1. 转到md5/src目录。

1. 使用更好的方式连接到您的Teradata数据库。

1. 运行以下betq命令：

   ```
   .run file = hash_md5.btq
   ```

### SHA2安装 {#sha2-installation}

如果要在Adobe Campaign实例中使用sha2函数，则必须从此页( [teradata](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) -udf-sha2-1.0.zip)在Teradata数据库上安装用户模式函数。

下载文件的sha1如下所示：e87438d37424836358bd3902cf1adeb629349780。

安装sha2:

1. 解压缩teradata-udf-sha2-1.0.zip文件。

1. 转到teradata-udf-sha2-1.0/src目录。

1. 使用更好的方式连接到您的Teradata数据库。

1. 运行以下两个beq命令：

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### UDF_UTF16TO8安装 {#UDF-UTF16TO8-installation}

如果要在Adobe Campaign实例中使用udf_utf16to8函数，则必须从此页的 **Teradataunicode工具包** ( [](https://downloads.teradata.com/download/tools/unicode-tool-kit) utk_release1.7.0.0.zip)在Teradata数据库上安装用户模式函数。

下载文件的sha1如下所示：e58235f434f52c71316a577cb48e20b97d24f470。

安装udf_utf16to8:

1. 解压缩utk_release1.7.0.0.zip文件。

1. 在提取的文件中查找udf_utf16to8.o，然后导航到包含该文件的目录。 它应命名为utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01TeradataUDFs/suselinux-x8664/udf_installation/。

1. 使用更好的方式连接到您的Teradata数据库。

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

## 活动服务器Linux配置 {#campaign-server-linux}

驱动程序安装需要以下各项：

* TeradataODBC驱动程序，可在本页中找 [到](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata工具和实用程序（用于批量加载），可在本页中找 [到](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

文件名和sha1:

* tdobc1620_linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44

* TeradataToolsAndUtilitiesBase_linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbaa6f8639387b19c563

如果Linux分发没有包，则可以按照CentOS 7中的说明（例如使用docker）进行安装，然后在Adobe Campaign服务器上复制/opt/teradata的内容。

### ODBC驱动程序安装 {#odbc-installation}

安装ODBC驱动程序：

1. 解压tdodbc1620__linux_indep.16.20.00.00-1.tar.gz文件。

1. 转到tdobc1620目录。

1. 您可能需要修复安装脚本：

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. 运行setup_wrapper.sh。

### Teradata工具和实用程序安装 {#teradata-tools-installation}

安装工具：

1. 解压TeradataToolsAndUtilitiesBase_linux_indep.16.20.01.00.tar.gz文件。

1. 转至TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu目录。

1. 运行setup_wrapper.sh。

1. 转至TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2目录。

1. 运行setup_wrapper.sh。

1. 转至TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase目录。

1. 运行setup_wrapper.sh。

1. libtelapi.so文件应位于/opt/teradata/client/16.20/lib64中。

## 活动Windows服务器配置 {#campaign-server-windows}

您首先需要下载适用于Windows的Teradata工具和实用程序。 您可以从此页面下 [载](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

确保安装ODBC驱动程序和Teradata并行传输器库。 它将安装telapi.dll，用于在Teradata数据库上进行批量加载。

确保驱动程序和实用程序的路径位于nlserver在执行过程中将具有的PATH变量中。 默认路径为C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\项目Files\Teradata\Client\15.10\bin on 64 bit)。

## 时区 {#timezone}

Teradata使用不标准的时区名称，您可以在Teradata站点上找 [到列表](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA)。 Adobe Campaign将尝试将外部配置中给定的时区转换为Teradata所理解的时区。 如果找不到通信，则会话将找到衣柜GMT+X（或GMT-X）时区，日志中会显示警告。

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
