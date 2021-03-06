---
product: campaign
title: 配置对Teradata的访问
description: 了解如何在FDA中配置对Teradata的访问
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3a5856c3-b642-4722-97ff-6ae7107efdbe
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 1%

---

# 配置对Teradata的访问 {#configure-access-to-teradata}

![](../../assets/v7-only.svg)

使用Campaign [联合数据访问](../../installation/using/about-fda.md) (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对Teradata的访问。

1. 安装和配置 [Teradata驱动程序](#teradata-config)
1. 配置Teradata [外部帐户](#teradata-external) 在Campaign中
1. 设置 [其他配置](#teradata-additional-configurations) (对于Teradata和Campaign服务器)

## Teradata配置 {#teradata-config}

您需要安装Teradata驱动程序才能与Campaign实施连接。

1. 安装 [用于Teradata的ODBC驱动程序](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   它由三个包组成，这些包可以按以下顺序安装在Red Hat（或CentOS）/Suse上：

   * TeraGSS
   * tdicu1510（使用setup_wrapper.sh安装）
   * tdobc1510（使用setup_wrapper.sh安装它）

1. 配置ODBC驱动程序。 配置可以在标准文件中执行： **/etc/odbc.ini** 对于常规参数和用于声明驱动程序的/etc/odbcinst.ini:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      “InstallDir”对应于 **odbcinst.ini** 文件。

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

1. 指定Adobe Campaign服务器的环境变量：

   * **LD_LIBRARY_PATH**:/opt/teradata/client/15.10/lib64和/opt/teradata/client/15.10/odbc_64/lib。
   * **奥德布奇尼**:odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NLSPATH**:opermsgs.cat文件的位置(/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>在FDA中连接到Teradata外部数据库需要在Adobe Campaign服务器上执行其他配置步骤。 [了解详情](#teradata-additional-configurations)。

## Teradata外部帐户{#teradata-external}

利用Teradata外部帐户，可将Campaign实例连接到Teradata外部数据库。

1. 从Campaign **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 选择 **[!UICONTROL External database]** as **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. 配置 **[!UICONTROL Teradata]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**:选择 **[!UICONTROL Teradata]** 类型。

   * **[!UICONTROL Server]**:teradata服务器的URL或名称

   * **[!UICONTROL Account]**:用于访问Teradata数据库的帐户名称

   * **[!UICONTROL Password]**:用于连接到Teradata数据库的密码

   * **[!UICONTROL Database]**:数据库的名称（可选）

   * **[!UICONTROL Options]**:要通过Teradata传递的选项。 使用以下格式：“parameter=value”。 使用半列作为值之间的分隔符。

   * **[!UICONTROL Timezone]**:在Teradata中设置时区。 [了解详情](#timezone)

连接器支持以下选项：

| Option | 说明 |
|---|---|
| TD_MAX_SESSIONS | 指定Teradata并行传输程序可为操作员作业获取的最大登录会话数。 <br>[有关更多信息，请参阅此页面](https://documentation.sas.com/doc/en/pgmsascdc/9.4_3.5/ds2ref/p1naft0um1kn3vn1ubgkrjdf7c3a.html). |
| 时区名称 | 服务器时区的名称。 |
| CharacterSet | 用于配置Teradata字符集。 <br>[有关更多信息，请参阅此页面](https://docs.teradata.com/r/ODBC-Driver-for-Teradata-User-Guide/May-2017/Configuration-of-odbc.ini-in-UNIX/Linux-and-Apple-OS-X/Teradata-DSN-Options#rub1478609534082__table_N102D3_N102B6_N102B3_N10001). |
| IANAAppCodePage | ODBC应用程序代码页。 <br>[有关更多信息，请参阅此页面](https://docs.teradata.com/r/ODBC-Driver-for-Teradata-User-Guide/May-2017/ODBC-Driver-for-Teradata-Application-Development/International-Character-Set-Support/Application-Code-Page) |

### 添加其他ODBC外部帐户 {#add-external}

>[!NOTE]
>
> 此选项不适用于低于7.3.1版本的内部版本。

teradata驱动程序提供其自己的ODBC库，但此库可能与其他ODBC外部帐户不兼容。

如果要配置另一个同样使用ODBC的外部帐户(例如Snowflake)，则需要将ODBCLib选项添加到默认ODBC库(`/usr/lib/x86_64-linux-gnu/libodbc.so` 关于Debian和 `/usr/lib64/libodbc.so` （在RHEL/CentOS中）。

![](assets/ext_account_24.png)

### 查询分段

当多个Adobe Campaign用户连接到同一FDATeradata外部帐户时， **[!UICONTROL Query banding]** 选项卡，用于在会话中设置查询带（即一组键/值对）。

![](assets/ext_account_20.png)

配置此选项后，每次Campaign用户对Teradata数据库执行查询时，Adobe Campaign都会发送元数据，元数据包含与该用户关联的键列表。 然后，Teradata管理员可以将此数据用于审核目的或管理访问权限。

>[!NOTE]
>
>有关 **[!UICONTROL Query banding]**，请参阅 [Teradata文档](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

要配置查询分段，请执行以下步骤：

1. 使用  **[!UICONTROL Default]** 输入在用户没有关联查询带时使用的默认查询带。 如果此字段留空，则没有查询带的用户将无法使用Teradata。

1. 使用 **[!UICONTROL Users]** 字段来指定每个用户的查询范围。 您可以根据需要添加任意数量的键/值对，例如priority=1;workload=high。 如果用户未分配查询带，则 **[!UICONTROL Default]** 字段。

1. 检查 **[!UICONTROL Active]** 用于激活此功能的框

#### 外部帐户疑难解答 {#external-account-troubleshooting}

如果在测试连接时出现以下错误 **TIM-030008日期“2”：缺少字符(iRc=-53)** 确保已正确安装ODBC驱动程序，并为Campaign服务器设置LD_LIBRARY_PATH(Linux)/PATH(Windows)。

错误 **ODB-240000 ODBC错误： [Microsoft][ODBC Driver Manager] 未找到数据源名称，且未指定默认驱动程序。** 如果使用16.X驱动程序，则在Windows中发生。 Adobe Campaign在odbcinst.ini中希望teradata名为“{teradata}”。

* 从Campaign 18.10开始，您可以在外部帐户的选项中添加ODBCDriverName=&quot;Teradata数据库ODBC驱动程序16.10&quot;。 版本号可以更改，通过运行odbcad32.exe并访问“Drivers（驱动程序）”选项卡，可以找到确切的名称。

* 如果您使用的是旧版Campaign，则必须将驱动程序安装所创建odbcinst.ini的Teradata部分复制到名为Teradata的新部分。 Regedit可在此用例中使用。 如果您的基数为latin1，则必须添加 **APICharSize=1** 中。

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

外部数据库需要以下权限：创建/拖放/执行自定义过程，创建/拖放/插入/选择表。 如果要在Adobe Campaign实例上使用md5和sha2函数，则可能还必须创建用户模式函数。

确保配置正确的时区。 它应该与将在Adobe Campaign实例中创建的外部帐户中设置的内容相匹配。

Adobe Campaign不会对它将在数据库中创建的对象设置保护模式（回退）。 您可能需要对用户设置一个默认值，Adobe Campaign将使用该用户通过以下查询连接到Teradata数据库：

| 禁用默认回退 |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### MD5安装 {#md5-installation}

如果要在Adobe Campaign实例中使用md5函数，则必须在Teradata数据库上从此处安装用户模式函数 [页面](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip)。

下载文件的sha1如下所示：65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e。

要安装md5，请执行以下操作：

1. 解压缩md5_20080530.zip文件。

1. 转到md5/src目录。

1. 使用两者连接到Teradata数据库。

1. 运行以下beq命令：

   ```
   .run file = hash_md5.btq
   ```

### SHA2安装 {#sha2-installation}

如果要在Adobe Campaign实例中使用sha2函数，则必须在Teradata数据库上从此处安装用户模式函数 [页面](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip)。

下载文件的sha1如下所示e87438d37424836358bd3902cf1adeb629349780。

要安装sha2，请执行以下操作：

1. 解压缩teradata-udf-sha2-1.0.zip文件。

1. 转到teradata-udf-sha2-1.0/src目录。

1. 使用两者连接到Teradata数据库。

1. 运行以下两个beq命令：

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### UDF_UTF16TO8安装 {#UDF-UTF16TO8-installation}

如果要在Adobe Campaign实例中使用udf_utf16to8函数，则必须在Teradata数据库上从 **Teradataunicode工具包** 此 [页面](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip)。

下载文件的sha1如下所示e58235f434f52c71316a577cb48e20b97d24f470。

要安装udf_utf16to8，请执行以下操作：

1. 解压缩utk_release1.7.0.0.zip文件。

1. 在提取的文件中查找udf_utf16to8.o，然后导航到包含该文件的目录。 它应命名为utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01TeradataUDFs/suselinux-x8664/udf_installation/。

1. 使用两者连接到Teradata数据库。

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

## Linux的Campaign服务器配置 {#campaign-server-linux}

安装驱动程序时需要满足以下条件：

* TeradataODBC驱动程序，可在此中找到 [页面](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata工具和实用程序（用于批量加载），可在此 [页面](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

文件名和sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

如果您的Linux分发没有包，您可以按照CentOS 7中的说明（例如使用docker）进行安装，然后在Adobe Campaign服务器上复制/opt/teradata的内容。

### ODBC驱动程序安装 {#odbc-installation}

要安装ODBC驱动程序，请执行以下操作：

1. 提取tdodbc1620__linux_indep.16.20.00.00-1.tar.gz文件。

1. 转到tdobc1620目录。

1. 您可能需要修复设置脚本：

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. 运行setup_wrapper.sh。

### Teradata工具和实用程序安装 {#teradata-tools-installation}

要安装工具，请执行以下操作：

1. 提取TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz文件。

1. 转到TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu目录。

1. 运行setup_wrapper.sh。

1. 转到TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2目录。

1. 运行setup_wrapper.sh。

1. 转到TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tpbase目录。

1. 运行setup_wrapper.sh。

1. libtelapi.so文件应在/opt/teradata/client/16.20/lib64中可用。

## Windows的Campaign服务器配置 {#campaign-server-windows}

您首先需要下载适用于Windows的Teradata工具和实用程序。 您可以从此处下载它 [页面](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

确保安装ODBC驱动程序和Teradata并行传输器库。 它将安装用于对Teradata库进行批量加载的telapi.dll。

确保驱动程序和实用程序的路径位于nlserver在执行期间将具有的PATH变量中。 默认情况下，路径为C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit)。

## 时区 {#timezone}

Teradata使用的时区名称不是标准名称，您可以在 [Teradata网站](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign将尝试将外部配置中给定的时区转换为一些Teradata了解的时区。 如果找不到通信，则会在会话中找到其他时区的GMT+X（或GMT-X）时区，并在日志中显示警告。

转换完成后，将读取名为datakit目录中的teradata_timezones.txt文件：在linux下为/usr/local/neolane/nl6/datakit。 如果编辑此文件，请确保联系Adobe Campaign团队以在源代码中进行更改，否则下次更新Campaign时会覆盖此文件。

使用 — verbose开关运行nlserver时，将指示用于连接的时区，例如：

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

如果使用的时区不正确，则可以在外部帐户中添加名为“TimeZoneName”的选项。 在这种情况下，请使用Teradata值，例如“TimeZoneName=Europe Central”。

在Teradata文档中使用批量加载或“快速加载”时，Campaign无法指示时区。 因此，建议设置Campaign用于连接的用户的默认时区：

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
