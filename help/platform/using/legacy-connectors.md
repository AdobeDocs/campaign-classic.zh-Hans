---
title: 传统连接器
seo-title: 传统连接器
description: 传统连接器
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# 传统连接器 {#legacy-connectors}

传统联合数据访问连接器仍受Adobe支持。 但是，我们建议用本页中列出的更新替代内容来替换 [它们](../../platform/using/specific-configuration-database.md)。

## 配置对Hadoop 2.1的访问 {#configure-access-to-hadoop}

### 适用于Windows {#for-windows}

1. 安装适用于Windows [的ODBC和Azure](https://www.microsoft.com/en-us/download/details.aspx?id=40886) HD Insight驱动程序。
1. 通过运行ODBC数据源管理工具创建DSN（数据源名称）。 Hive的系统DSN范例供您修改。

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. 创建Hadoop外部帐户，详 [情请见](../../platform/using/external-accounts.md#hadoop-external-account) 。

### 对于Linux {#for-linux}

1. 安装unixodbc for Linux。

   ```
   apt-get install unixodbc
   ```

1. 从HortonWorks下载并安装Apache Hive的ODBC驱动程序： [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/)。

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. 检查ODBC文件位置。

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. 创建DSN（数据源名称）并编辑odbc.ini文件。 然后，为您的配置单元连接创建DSN。

   以下是HDInsight设置一个名为“病毒”的连接的示例：

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >此处 **的UseNativeQuery** 参数非常重要。 活动识别配置单元，除非设置UseNativeQuery，否则将无法正常工作。 通常，驱动程序或Hive SQL Connector将重写查询并篡改列顺序。

   身份验证设置取决于Hive/Hadoop配置。 例如，对于HD Insight，请使用AuthMech=6进行用户／密码身份验证，如 [下所述](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)。

1. 导出变量。

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. 通过/usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini设置Hortonworks驱动程序。

   必须使用UTF-16才能连接活动和unix-odbc(libodbcinst)。

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. 您现在可以使用isql测试连接。

   ```
   isql vorac
   isql vorac -v
   ```

1. 创建Hadoop外部帐户，详 [情请见](../../platform/using/external-accounts.md#hadoop-external-account) 。

## 配置对Netezza的访问 {#configure-access-to-netezza}

在联合数据访问下连接到Netezza外部数据库需要在Adobe Campaign服务器上进行以下其他配置：

1. 根据您使用的操作系统，安装Netezza的ODBC驱动程序：

   * **nz-linuxclient-v7.2.0.0.tar.gz** for Linux。 选择与您的操作系统（linux或linux64）对应的文件夹，并开始unpack命令。 您可以保留默认建议在存储库中执行的安装：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.zip** for Windows 解压缩文件并开始与操作系统对应的可执行脚本：nzodbcsetup.exe或nzodbcsetup64.exe。 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行： **/etc/odbc.ini** ，用于常规参数， **/etc/odbcinst.ini** ，用于声明驱动程序。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;对应于odbcinst.ini文件的位置。

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. 指定环境服务器的Adobe Campaign变量：

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。 “/usr/local/nz”与安装驱动程序时默认提供的安装存储库相对应。 您需要在此指定已为安装选择的存储库。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini文件的位置。 Netezza还要求使用odbc.ini文件的第二个变量。

1. 在Campaign Classic中，您随后可以配置Netezza外部帐户。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 并选 **[!UICONTROL External database]** 择为 **[!UICONTROL Type]**。

1. 要配置 **[!UICONTROL Netezza]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:内泰扎

   * **[!UICONTROL Server]**:Netezza服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

>[!NOTE]
>
>不考虑对包含自动生成的主键的模式执行的操作。
>
>该表将在模式中定 **义的第** 一个索引上使用Organize on子句。 由于此子句限制为Netezza的1到4列，因此此索引不能包含4列以上。

## 配置对Sybase IQ的访问 {#configure-access-to-sybase-iq}

在联合数据访问下连接到Sybase IQ外部数据库需要在Adobe Campaign服务器上进行以下其他配置：

1. 确保unixodbc包在服务器上。
1. 安 **装iq_odbc**。 安装结束时可能会出错。 可以忽略此错误。
1. 安 **装iq_client_common**。 安装结束时可能会发生Java错误。 可以忽略此错误。
1. 配置ODBC驱动程序。 配置可以在标准文件中执行：/etc/odbc.ini用于常规参数，/etc/odbcinst.ini用于声明驱动程序：

   * **/etc/odbc.ini** (将字符等 `<server_alias>` 值替换为您自己的值):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. 在LD_LIBRARY_PATH变量中为新libodbc16.so库添加路径。 为此：

   * 如果您使用customer.sh文件声明您的路径：为LD_LIBRARY_PATH变量添加路径/opt/sybase/IQ-16_0/lib64。
   * 否则，请使用Unix命令。

1. 在Campaign Classic中，您随后可以配置Sybase IQ外部帐户。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 并选 **[!UICONTROL External database]** 择为 **[!UICONTROL Type]**。

1. 要配置 **[!UICONTROL Sybase IQ]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE、Sybase IQ)

   * **[!UICONTROL Server]**:与第5步中定义的ODBC`<server_alias>`连接()相对应。 不一定是服务器本身的名称。

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

>[!NOTE]
>
>对于Windows，必须在Adobe Campaign服务器上安装Sybase IQ客户端并创建ODBC连接。 确保在Windows中Adobe Campaign服务器(nlserver)作为服务运行时创建系统数据源。

## 配置对Teradata的访问 {#configure-access-to-teradata}

在联合数据访问下连接到Teradata外部数据库需要在Adobe Campaign服务器上进行某些附加配置。 有关如何配置Teradata数据库的详细信息，请参 [阅此页](../../platform/using/appendices-fda.md#teradata-configuration)。

1. 安装用 [于Teradata的ODBC驱动程序](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)。

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

1. 在Campaign Classic中，您随后可以配置Teradata外部帐户。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 并选 **[!UICONTROL External database]** 择为 **[!UICONTROL Type]**。

1. 要配置 **[!UICONTROL Teradata]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:Teradata

   * **[!UICONTROL Server]**:Teradata服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

## 配置对SAP HANA的访问 {#configure-access-to-sap-hana}

在联合数据访问中连接到SAP HANA外部数据库需要Adobe Campaign服务器上的某些附加配置：

1. 根据您使用的操作系统，安装用于SAP HANA的ODBC驱动程序：

   * **适用于Linux的hdb_client_linux** .tgz。 解压后，启动hdbinst命令并按照说明完成驱动程序安装。
   * **适用于Windows的hdb_client_windows** .zip。 解压缩文件并开始可执行文件： **hdbinst.exe**。 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可以在标准文件中执行：/etc/odbc.ini用于常规参数，/etc/odbcinst.ini用于声明驱动程序。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot;与odbcinst.ini文件的 **位置相对应** 。

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. 指定环境服务器的Adobe Campaign变量：

   * **LD_LIBRARY_PATH**:默认情况下，它应包含指向SAP Hana客户端(/usr/sap/hdbclient/libodbcHDB.so)的链接。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。

1. 在Campaign Classic中，您随后可以配置SAP Hana外部帐户。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]** 并选 **[!UICONTROL External database]** 择为 **[!UICONTROL Type]**。

1. 要配置 **[!UICONTROL SAP Hana]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**:SAP Hana

   * **[!UICONTROL Server]**:SAP Hana服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码
