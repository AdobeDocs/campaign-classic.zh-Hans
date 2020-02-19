---
title: 访问外部数据库
seo-title: 访问外部数据库
description: 访问外部数据库
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a0698ad55afb391bdc652a00b43b20df6fb9851b

---


# 按数据库类型的特定配置 {#specific-configurations-by-database-type}

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及安装驱动程序并声明属于Adobe Campaign服务器上每个RDBMS的环境变量。

一般而言，您需要在Adobe Campaign服务器上的外部数据库上安装相应的客户端层。

>[!NOTE]
>
>兼容版本列在 [Campaign兼容性表中](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA)。

<!--
## Configure access to Azure Synapse {#configure-access-to-azure-synapse}

### Azure Synapse on CentOS {#azure-centos}

1. Download mysql57-community-release.noarch.rpm. You can find it in this [page](https://dev.mysql.com/downloads/repo/yum).

1. Install the client library:

    ```
    $ yum install mysql57-community-release-el7-9.noarch.rpm
    $ yum install mysql-community-libs
    ```

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

### Azure Synapse on Debian {#azure-debian}

1. Download mysql-apt-config.deb. You can find it in this [page](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

1. Install the client library:

    ```
    $ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
    $ apt update
    $ apt install libmysqlclient20
    ```

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

### Azure Synapse on Windows {#azure-windows}

1. Download the C connector. You can find it in this [page](https://dev.mysql.com/downloads/connector/c).

1. Make sure the directory that contains libmysqlclient.dll is added to the PATH environment variable that nlserver will use.

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

-->

## 配置对雪花的访问 {#configure-access-to-snowflake}

>[!NOTE]
>
>雪花连接器可用于托管和内部部署。 For more on this, refer to this [page](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### CentOS上的雪花 {#snowflake-centos}

1. 下载Snowflake的ODBC驱动程序。 雪花的司机可在此找 [到](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm)。

1. 然后，您需要使用以下命令在CentOs上安装ODBC驱动程序：

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. 下载和安装ODBC驱动程序后，您需要重新启动Campaign Classic。 为此，请运行以下命令：

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 在Campaign Classic中，在Campaign Classic中配置Snowflake外部帐户。 从中 **[!UICONTROL Explorer]**&#x200B;展开菜 **[!UICONTROL Administration]** 单。

1. 展开菜 **[!UICONTROL Platform]** 单并单击 **[!UICONTROL External accounts]**。

1. 选择现成的外部帐 **[!UICONTROL Snowflake]** 户。

1. 要配置外部帐 **[!UICONTROL Snowflake]** 户，请执行以下操作：

   * **[!UICONTROL Server]**

      雪花服务器的URL。

   * **[!UICONTROL Account]**

      用户的名称。

   * **[!UICONTROL Password]**

      用户帐户密码。

   * **[!UICONTROL Database]**

      数据库的名称。
   ![](assets/snowflake.png)

1. 单击选 **[!UICONTROL Parameters]** 项卡，然后单击 **[!UICONTROL Deploy function]** 按钮以创建函数。

   ![](assets/snowflake_2.png)

连接器支持以下选项：

| 选项 | 值 | 说明 |
|---|---|---|
| 工作架构 |  | 用于工作表的数据库架构 |
| 仓库 |  | 要使用的默认仓库的名称。 它将覆盖用户的默认值。 |
| TimeZoneName |  | 默认为空，这表示使用Campaign Classic应用程序服务器的系统时区。 此选项可用于强制使用TIMEZONE session参数。 <br>[有关详细信息，请参见此页面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)。 |
| WeekStart | 0, 1-7 | 默认情况下，设置为0。 （WEEK_START session参数）有 <br>关此的详细信息，请参阅本 [页](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start)。 |
| UseCachedResult | 真／假 | 默认设置为TRUE。 此选项可用于禁用雪花缓存的结果（USE_CACHED_RESULTS会话参数）。有关 <br>此选项的详细信息，请参阅此 [页](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)。 |

### 德比亚雪花 {#snowflake-debian}

1. 下载Snowflake的ODBC驱动程序。 雪花的司机可在此找 [到](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html)。

1. 然后，您需要使用以下命令在Debian上安装ODBC驱动程序：

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. 下载和安装ODBC驱动程序后，您需要重新启动Campaign Classic。 为此，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，在Campaign Classic中配置Snowflake外部帐户。 从中 **[!UICONTROL Explorer]**&#x200B;展开菜 **[!UICONTROL Administration]** 单。

1. 展开菜 **[!UICONTROL Platform]** 单并单击 **[!UICONTROL External accounts]**。

1. 选择现成的外部帐 **[!UICONTROL Snowflake]** 户。

1. 要配置外部帐 **[!UICONTROL Snowflake]** 户，请执行以下操作：

   * **[!UICONTROL Server]**

      雪花服务器的URL。

   * **[!UICONTROL Account]**

      用户的名称。

   * **[!UICONTROL Password]**

      用户帐户密码。

   * **[!UICONTROL Database]**

      数据库名称
   ![](assets/snowflake.png)

1. 单击选 **[!UICONTROL Parameters]** 项卡，然后单击 **[!UICONTROL Deploy function]** 按钮以创建函数。

   ![](assets/snowflake_2.png)

连接器支持以下选项：

| 选项 | 值 | 说明 |
|---|---|---|
| 工作架构 |   | 用于工作表的数据库架构 |
| 仓库 |   | 要使用的默认仓库的名称。 它将覆盖用户的默认值。 |
| TimeZoneName |   | 默认为空，这表示使用Campaign Classic应用程序服务器的系统时区。 此选项可用于强制使用TIMEZONE session参数。 <br>[有关详细信息，请参见此页面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)。 |
| WeekStart | 0, 1-7 | 默认情况下，设置为0。 （WEEK_START session参数）有 <br>关此的详细信息，请参阅本 [页](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start)。 |
| UseCachedResult | 真／假 | 默认设置为TRUE。 此选项可用于禁用雪花缓存的结果（USE_CACHED_RESULTS会话参数）。有关 <br>此选项的详细信息，请参阅此 [页](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)。 |

### 窗口上的雪花 {#snowflake-windows}

1. 下载适 [用于Windows的ODBC驱动程序](https://docs.snowflake.net/manuals/user-guide/odbc-download.html)。 请注意，您需要管理员权限才能安装驱动程序。 For more on this, refer to this [page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. 配置ODBC驱动程序。 For more on this, refer to this [page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 安装和配置ODBC驱动程序后，您需要在Campaign Classic中配置Snowflake外部帐户。 从中 **[!UICONTROL Explorer]**&#x200B;展开菜 **[!UICONTROL Administration]** 单。

1. 展开菜 **[!UICONTROL Platform]** 单并单击 **[!UICONTROL External accounts]**。

1. 选择现成的外部帐 **[!UICONTROL Snowflake]** 户。

1. 要配置外部帐 **[!UICONTROL Snowflake]** 户，请执行以下操作：

   * **[!UICONTROL Server]**

      雪花服务器的URL。

   * **[!UICONTROL Account]**

      用户的名称。

   * **[!UICONTROL Password]**

      用户帐户密码。

   * **[!UICONTROL Database]**

      数据库名称
   ![](assets/snowflake.png)

1. 单击选 **[!UICONTROL Parameters]** 项卡，然后单击 **[!UICONTROL Deploy function]** 按钮以创建函数。

   ![](assets/snowflake_2.png)

连接器支持以下选项：

| 选项 | 值 | 说明 |
|---|---|---|
| 工作架构 |   | 用于工作表的数据库架构 |
| 仓库 |   | 要使用的默认仓库的名称。 它将覆盖用户的默认值。 |
| TimeZoneName |   | 默认为空，这表示使用Campaign Classic应用程序服务器的系统时区。 此选项可用于强制使用TIMEZONE session参数。 <br>[有关详细信息，请参见此页面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)。 |
| WeekStart | 0, 1-7 | 默认情况下，设置为0。 （WEEK_START session参数）有 <br>关此的详细信息，请参阅本 [页](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start)。 |
| UseCachedResult | 真／假 | 默认设置为TRUE。 此选项可用于禁用雪花缓存的结果（USE_CACHED_RESULTS会话参数）。有关 <br>此选项的详细信息，请参阅此 [页](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)。 |

## 配置对Hadoop 3.0的访问 {#configure-access-to-hadoop-3}

在FDA中连接到Hadoop外部数据库需要Adobe Campaign服务器上的以下配置。 请注意，此配置适用于Windows和Linux。

1. 根据您的操作系统版本，下载Hadoop的ODBC驱动程序。 驱动程序可在此页面上找 [到](https://www.cloudera.com/downloads.html)。

1. 然后，您需要安装ODBC驱动程序并为Hive连接创建DSN。 此处可找到说 [明](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. 下载和安装ODBC驱动程序后，您需要重新启动Campaign Classic。 为此，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，在Campaign Classic中配置Hadoop外部帐户。 从中 **[!UICONTROL Explorer]**&#x200B;展开菜 **[!UICONTROL Administration]** 单。

1. 展开菜 **[!UICONTROL Platform]** 单并单击 **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL Create]** 并选择“帐 **[!UICONTROL External database]** 户类型”。

1. 要配置外部帐 **[!UICONTROL  Hadoop]** 户，请执行以下操作：

   * **[!UICONTROL Type]**

      ODBC(Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**

      DNS的名称。

   * **[!UICONTROL Account]**

      用户的名称。

   * **[!UICONTROL Password]**

      用户帐户密码。

   * **[!UICONTROL Database]**

      数据库的名称（如果未在DSN中指定）。 如果在DSN中指定，则可将其留空。

   * **[!UICONTROL Time zone]**

      服务器时区
   ![](assets/hadoop3.png)

连接器支持以下ODBC选项：

| 名称 | 值 |
|---|---|
| ODBCMgr | iODBC |
| 仓库 | 1/2/4 |

连接器还支持以下Hive选项：

| 名称 | 值 | 说明 |
|---|---|---|
| bulkKey | Azureblob或DataLake访问密钥 | 对于wasb://或wasbs://批量加载程序(即，如果批量加载工具以wasb://或wasbs://启动)。 <br>它是用于批量加载的斑点或DataLake桶的访问密钥。 |
| hdfsPort | 端口号 <br>默认设置为8020 | 对于HDFS批量加载(即，如果批量加载工具以webhdfs://或webhdfss://开头)。 |
| bucketsNumber | 20 | 创建集群表时的时段数。 |
| fileFormat | 镶木 | 工作表的默认文件格式。 |

## 配置对Hadoop 2.1的访问 {#configure-access-to-hadoop}

有关如何在FDA中配置Hadoop外部数据库的详细信息，请参阅本 [文](https://helpx.adobe.com/campaign/kb/access-hadoop-2.html)。

### 适用于Windows {#for-windows}

1. 安装适用于Windows [的ODBC和Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) 驱动程序。
1. 通过运行ODBC DataSource Administrator工具创建DSN（数据源名称）。 Hive的系统DSN范例供您修改。

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. 创建Hadoop外部帐户，如创建共享连 [接部分中所述](#creating-a-shared-connection) 。

### 对于Linux {#for-linux}

1. 安装unixodbc for Linux。

   ```
   apt-get install unixodbc
   ```

1. 从HortonWorks下载并安装用于Apache Hive的ODBC驱动程序： [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/)。

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. 检查ODBC文件的位置。

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

1. 创建DSN（数据源名称）并编辑odbc.ini文件。 然后，为Hive连接创建DSN。

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
   >此处 **的UseNativeQuery** 参数非常重要。 Campaign是Hive感知型营销活动，除非设置UseNativeQuery，否则将无法正确运行。 通常，驱动程序或Hive SQL Connector将重写查询并篡改列排序。

   身份验证设置取决于Hive/Hadoop配置。 例如，对于HD Insight，请使用AuthMech=6进行用户／密码身份验证，如 [下所述](http://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)。

1. 导出变量。

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. 通过/usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini设置Hortonworks驱动程序。

   必须使用UTF-16才能连接Campaign和unix-odbc(libodbcinst)。

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

1. 创建Hadoop外部帐户，如创建共享连 [接部分中所述](#creating-a-shared-connection) 。

## 配置对Netezza的访问 {#configure-access-to-netezza}

在FDA中连接到Netezza外部数据库需要在Adobe Campaign服务器上进行以下其他配置：

1. 根据您使用的操作系统，安装Netezza的ODBC驱动程序：

   * **nz-linuxclient-v7.2.0.0.tar.gz** for Linux。 选择与您的操作系统（linux或linux64）对应的文件夹，然后启动unpack命令。 您可以将安装保留在默认情况下建议的存储库中执行：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.zip** for Windows 解压缩文件并启动与您的操作系统对应的可执行脚本：nzodbcsetup.exe或nzodbcsetup64.exe。 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可在标准文件中执行： **/etc/odbc.ini** for general parameters and **/etc/odbcinst.ini** for sarting drivers.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      “InstallDir”对应于odbcinst.ini文件的位置。

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

1. 指定Adobe Campaign服务器的环境变量：

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。 “/usr/local/nz”与安装驱动程序时默认提供的安装存储库相对应。 您需要在此指定已选择用于安装的存储库。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini文件的位置。 Netezza还要求使用odbc.ini文件的第二个变量。

1. 创建Netezza外部帐户，如创建共享连 [接一节所述](#creating-a-shared-connection) 。

>[!NOTE]
>
>不考虑对包含自动生成的主密钥的架构执行的操作。
>
>该表将在架构中定 **义的第一个索引上** ，使用“组织”on子句。 由于此子句限制为Netezza的1到4列，因此此索引不能包含4列以上。

## 配置对Oracle的访问权限 {#configure-access-to-oracle}

在FDA中连接到Oracle外部数据库需要在Adobe Campaign服务器上进行以下其他配置。

### 对于Linux {#for-linux-1}

1. 安装与Oracle版本对应的Oracle完整客户端。
1. 将您的TNS定义添加到您的安装中。 为此，请在/etc/oracle存储库的 **tnsnames.ora** 文件中指定这些名称。 如果此存储库不存在，请创建它。

   然后，创建新的TNS_ADMIN环境变量：导出TNS_ADMIN=/etc/oracle并重新启动计算机。

1. 将Oracle集成到您的Adobe Campaign服务器(nlserver)中。 为此，请检查 **customer.sh** 文件是否位于Adobe Campaign服务器树结构的“nl6”文件夹中，并且它包含指向Oracle库的链接。

   例如，对于11.2中的客户端：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >这些值（特别是ORACLE_HOME）取决于您的安装存储库。 请务必在引用这些值之前检查树结构。

1. 安装Oracle所需的库：

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

### 适用于Windows {#for-windows-1}

1. 安装Oracle客户端。
1. 在C:Oracle文件夹中，创建一个 **包含您的TNS定义的tnsnames.ora** 文件。

   添加一个TNS_ADMIN环境变量，将C:Oracle作为值并重新启动计算机。

## 配置对Sybase IQ的访问 {#configure-access-to-sybase-iq}

在FDA中连接到Sybase IQ外部数据库需要在Adobe Campaign服务器上进行以下其他配置：

1. 确保unixodbc包位于服务器上。
1. 安 **装iq_odbc**。 安装结束时可能发生错误。 此错误可以忽略。
1. 安 **装iq_client_common**。 安装结束时可能会发生Java错误。 此错误可以忽略。
1. 配置ODBC驱动程序。 配置可在标准文件中执行：/etc/odbc.ini用于常规参数，/etc/odbcinst.ini用于声明驱动程序：

   * **/etc/odbc.ini** (将字符等值替 `<server_alias>` 换为您自己的值):

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

1. 在LD_LIBRARY_PATH变量中为新libodbc16.so库添加路径。 为此，请执行以下操作：

   * 如果您使用customer.sh文件声明您的路径：为LD_LIBRARY_PATH变量添加路径/opt/sybase/IQ-16_0/lib64。
   * 否则，请使用Unix命令。

1. 创建新的FDA外部帐户，如创建共 [享连接部分所述](#creating-a-shared-connection) 。 对于Sybase IQ，服务器名与步骤5中定义的ODBC连接(`<server_alias>`)相对应。 它不一定是服务器本身的名称。

>[!NOTE]
>
>对于Windows，必须在Adobe Campaign服务器上安装Sybase IQ客户端并创建ODBC连接。 确保在Windows中作为服务运行Adobe Campaign服务器(nlserver)时创建系统数据源。

## 配置对Teradata的访问 {#configure-access-to-teradata}

在FDA中连接到Teradata外部数据库需要Adobe Campaign服务器上的某些附加配置。 有关如何配置Teradata数据库的详细信息，请参阅本 [文](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html)。

1. 安装Teradata [的ODBC驱动程序](http://downloads.teradata.com/download/connectivity/odbc-driver/linux)。

   它由三个包组成，按照以下顺序可安装在Red Hat（或CentOS）/Suse上：

   * TeraGSS
   * tdicu1510（使用setup_wrapper.sh安装它）
   * tdobc1510（使用setup_wrapper.sh安装它）

1. 配置ODBC驱动程序。 配置可在标准文件中执行：/etc/odbc.ini **** for general parameters and /etc/odbcinst.ini for sarting drivers:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      “InstallDir”与 **odbcinst.ini文件的位置相对应** 。

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
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。
   * **NLSPATH**:opermsgs.cat文件的位置(/opt/teradata/client/15.10/msg/opermsgs.cat)

## 配置对SAP HANA的访问 {#configure-access-to-sap-hana}

连接到FDA中的SAP HANA外部数据库需要Adobe Campaign服务器上的某些附加配置：

1. 根据您使用的操作系统安装SAP HANA的ODBC驱动程序：

   * **适用于Linux的hdb_client_linux.tgz** 。 解压后，启动hdbinst命令并按照说明完成驱动程序安装。
   * **适用于Windows的hdb_client_windows.zip** 。 解压缩文件并启动可执行文件： **hdbinst.exe**。 按照向导说明完成驱动程序的安装。

1. 配置ODBC驱动程序。 配置可在标准文件中执行：/etc/odbc.ini表示常规参数，/etc/odbcinst.ini表示声明驱动程序。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      “InstallDir”与 **odbcinst.ini文件的位置相对应** 。

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. 指定Adobe Campaign服务器的环境变量：

   * **LD_LIBRARY_PATH**:默认情况下，它应包含指向SAP Hana客户端(/usr/sap/hdbclient/libodbcHDB.so)的链接。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。

1. 创建SAP Hana外部帐户，如创建共享连 [接一节中所述](#creating-a-shared-connection) 。
