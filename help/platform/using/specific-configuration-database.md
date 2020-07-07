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
source-git-commit: 4f1f1cd9c5ebb77fbb01cadad6c587ed2fe64dcc
workflow-type: tm+mt
source-wordcount: '1835'
ht-degree: 1%

---


# 按数据库类型的特定配置 {#specific-configurations-by-database-type}

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及安装驱动程序并声明属于环境服务器上每个RDBMS的Adobe Campaign变量。

有关传统连接器（如Teradata、Hadoop 2.1或Netezza）的更多信息，请参阅本 [页](../../platform/using/legacy-connectors.md)。

通常，您需要在Adobe Campaign服务器上的外部数据库上安装相应的客户端层。

>[!NOTE]
>
>兼容版本列在 [活动兼容性表中](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA)。

## 配置对Azure突触的访问 {#configure-access-to-azure-synapse}

### Azure突触外部帐户 {#azure-external}

外部帐户 [!DNL Azure] 允许您将活动实例连接到Azure突触外部数据库。
要创建外部帐户 [!DNL Azure Synapse] 外部帐户，请执行以下操作：

1. 在Campaign Classic中，配置您的 [!DNL Azure Synapse] 外部帐户。 在中， **[!UICONTROL Explorer]**&#x200B;单击 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**.

1. 选 **[!UICONTROL External database]** 择作为外部帐户 **[!UICONTROL Type]**。

1. 配置 [!DNL Azure Synapse] 外部帐户，必须指定：

   * **[!UICONTROL Type]**: Azure突触Analytics

   * **[!UICONTROL Server]**: Azure突触服务器的URL

   * **[!UICONTROL Account]**: 用户的名称

   * **[!UICONTROL Password]**: 用户帐户密码

   * **[!UICONTROL Database]**: 数据库的名称
   ![](assets/azure_1.png)

### CentOS上的Azure突触 {#azure-centos}

**先决条件：**

* 您需要根权限才能安装ODBC驱动程序。
* Microsoft提供的Red Hat Enterprise ODBC驱动程序也可与CentOS一起使用，以连接到SQL Server。
* 版本13.0将适用于Red Hat 6和7。

在CentOS上配置Azure突触：

1. 首先，安装ODBC驱动程序。 您可以在此页中找 [到它](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。

   >[!NOTE]
   >
   >这是ODBC驱动程序的版本13专有的。

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. 如果需要，可以通过运行以下命令安装unixODBC开发头：

   ```
   sudo yum install unixODBC-devel
   ```

1. 安装驱动程序后，可以测试和验证ODBC驱动程序，并根据需要查询数据库。 运行以下命令：

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 在Campaign Classic中，您随后可以配置 [!DNL Azure Synapse] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#azure-external)。

1. 由于Azure Synapse Analytics通过TCP 1433端口进行通信，您需要在防火墙上打开此端口。 使用以下命令：

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >要允许从Azure突触分析端进行通信，您可能需要将公共IP添加到允许列表。 为此，请参阅Azure [文档](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。

1. 如果是iptables，请运行以下命令：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Windows上的Azure突触 {#azure-windows}

>[!NOTE]
>
>这仅对ODBC驱动程序的版本13有限，但Adobe Campaign经典也可以使用SQL Server本机客户端驱动程序11.0和10.0。

在Windows上配置Azure突触：

1. 首先，安装Microsoft ODBC驱动程序。 您可以在此页中找 [到它](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。

1. 选择要安装的以下文件：

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. 安装ODBC驱动程序后，可以根据需要测试它。 For more on this, refer to this [page](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. 在Campaign Classic中，您随后可以配置 [!DNL Azure Synapse] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#azure-external)。

1. 由于Azure Synapse Analytics通过TCP 1433端口进行通信，您需要在Windows Defender Firewall上打开此端口。 For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### Azure突触到Debian {#azure-debian}

**先决条件：**

* 您需要根权限才能安装ODBC驱动程序。
* 安装msodbcsql包时需要Curl。 如果尚未安装，请运行以下命令：

   ```
   sudo apt-get install curl
   ```

在Debian上配置Azure突触：

1. 首先，安装用于SQL Server的Microsoft ODBC驱动程序。 使用以下命令安装SQL Server的ODBC驱动程序13.1:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. 如果在调用sudo apt-get **update时出现以下错误“找不到方法驱动程序/usr/lib/apt/methods/https** ” **，应运行命令**:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. 您现在需要使用以下命令安装mssql-tools。 使用批量复制项目（或BCP）实用程序和运行查询时需要Mssq工具。

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. 如果需要，可以通过运行以下命令安装unixODBC开发头：

   ```
   sudo yum install unixODBC-devel
   ```

1. 安装驱动程序后，可以测试和验证ODBC驱动程序，并根据需要查询数据库。 运行以下命令：

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 在Campaign Classic中，您现在可以配置 [!DNL Azure Synapse] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#azure-external)。

1. 要在Debian上配置iptables以确保与Azure突触Analytics连接，请使用以下命令为主机名启用出站TCP 1433端口：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >要允许从Azure突触分析端进行通信，您可能需要将公共IP添加到允许列表。 为此，请参阅Azure [文档](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。

## 配置对雪花的访问 {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] connector可用于托管和内部部署。 For more on this, refer to [this article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### 雪花外部帐户 {#snowflake-external}

外部帐户 [!DNL Snowflake] 允许您将活动实例连接到Snowflake外部数据库。

1. 在Campaign Classic中，配置您的 [!DNL Snowflake] 外部帐户。 在中， **[!UICONTROL Explorer]**&#x200B;单击 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**.

1. 选 **[!UICONTROL External database]** 择作为外部帐户 **[!UICONTROL Type]**。

1. 配置 **[!UICONTROL Snowflake]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**: 服务器的 [!DNL Snowflake] URL

   * **[!UICONTROL Account]**: 用户的名称

   * **[!UICONTROL Password]**: 用户帐户密码

   * **[!UICONTROL Database]**: 数据库的名称
   ![](assets/snowflake.png)

1. 单击选 **[!UICONTROL Parameters]** 项卡，然 **[!UICONTROL Deploy functions]** 后单击按钮以创建函数。

   ![](assets/snowflake_2.png)

连接器支持以下选项：

| 选项 | 说明 |
|---|---|
| 工作架构 | 用于工作表的模式库 |
| 仓库 | 要使用的默认仓库的名称。 它将覆盖用户的默认设置。 |
| 时区名称 | 默认为空，这意味着使用Campaign Classic应用服务器的系统时区。 该选项可用于强制TIMEZONE会话参数。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)。 |
| WeekStart | WEEK_开始会话参数。 默认情况下，设置为0。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)。 |
| UseCachedResult | USE_CACHED_RESULTS会话参数。 默认设置为TRUE。 此选项可用于禁用雪花缓存结果。 <br>有关详细信息，请参见[此页面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)。 |

### CentOS上的雪花 {#snowflake-centos}

1. 下载ODBC驱动程序 [!DNL Snowflake]。 [单击此处](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) ,开始下载。
1. 然后，您需要使用以下命令在CentOs上安装ODBC驱动程序：

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. 下载和安装ODBC驱动程序后，需要重新启动Campaign Classic。 要执行此操作，请运行以下命令：

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 在Campaign Classic中，您随后可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#snowflake-external)。

### 德比亚雪花 {#snowflake-debian}

1. 下载ODBC驱动程序 [!DNL Snowflake]。 [单击此处](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) ,开始下载。

1. 然后，您需要使用以下命令在Debian上安装ODBC驱动程序：

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. 下载和安装ODBC驱动程序后，需要重新启动Campaign Classic。 要执行此操作，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，您随后可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#snowflake-external)。

### 窗口上的雪花 {#snowflake-windows}

1. 下载适 [用于Windows的ODBC驱动程序](https://docs.snowflake.net/manuals/user-guide/odbc-download.html)。 请注意，您需要管理员级权限才能安装驱动程序。 For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. 配置ODBC驱动程序。 For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 在Campaign Classic中，您随后可以配置 [!DNL Snowflake] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#snowflake-external)。

## 配置对Hadoop 3.0的访问 {#configure-access-to-hadoop-3}

### Hadoop外部帐户 {#hadoop-external}

外部帐户 [!DNL Hadoop] 允许您将活动实例连接到Hadoop外部数据库。

1. 在Campaign Classic中，配置您的 [!DNL Hadoop] 外部帐户。 在中， **[!UICONTROL Explorer]**&#x200B;单击 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**.

1. 选 **[!UICONTROL External database]** 择作为外部帐户 **[!UICONTROL Type]**。

1. 配置 **[!UICONTROL Hadoop]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**: ODBC(Sybase ASE、Sybase IQ)

   * **[!UICONTROL Server]**: DNS的名称

   * **[!UICONTROL Account]**: 用户的名称

   * **[!UICONTROL Password]**: 用户帐户密码

   * **[!UICONTROL Database]**: 如果未在DSN中指定数据库的名称。 如果在DSN中指定，则可将其留空

   * **[!UICONTROL Time zone]**: 服务器时区
   ![](assets/hadoop3.png)

连接器支持以下ODBC选项：

| 名称 | 值 |
|---|---|
| ODBCMgr | iODBC |
| 仓库 | 1/2/4 |

连接器还支持以下配置单元选项：

| 名称 | 值 | 说明 |
|---|---|---|
| bulkKey | Azureblob或DataLake访问密钥 | 对于wasb://或wasbs://批量加载程序(即，如果批量加载工具与wasb://或wasbs://开始)。 <br>它是用于批量加载的blob或DataLake存储桶的访问密钥。 |
| hdfsPort | 端口号 <br>默认设置为8020 | 对于HDFS批量加载(即，如果批量加载工具开始为webhdfs://或webhdfss://)。 |
| bucketsNumber | 20 | 创建聚簇表时的桶数。 |
| fileFormat | 镶木 | 工作表的默认文件格式。 |

### 配置Hadoop 3.0 {#configuring-hadoop}

在联合数据访问下连接到Hadoop外部Adobe Campaign库需要在服务器上进行以下配置。 请注意，此配置适用于Windows和Linux。

1. 根据您的操作系统版本，下载Hadoop的ODBC驱动程序。 驱动程序可在此页 [面上找到](https://www.cloudera.com/downloads.html)。

1. 然后，您需要安装ODBC驱动程序并为配置单元连接创建DSN。 说明可在此页 [中找到](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. 下载和安装ODBC驱动程序后，需要重新启动Campaign Classic。 要执行此操作，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，您随后可以配置 [!DNL Hadoop] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#hadoop-external)。

## 配置对Oracle的访问 {#configure-access-to-oracle}

### Oracle外部帐户 {#oracle-external}

外部帐户 [!DNL Oracle] 允许您将活动实例连接到Hadoop外部数据库。

1. 在Campaign Classic中，配置您的 [!DNL oracle] 外部帐户。 在中， **[!UICONTROL Explorer]**&#x200B;单击 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**.

1. 选 **[!UICONTROL External database]** 择作为外部帐户 **[!UICONTROL Type]**。

1. 配置 **[!UICONTROL Oracle]** 外部帐户，必须指定：

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: DNS的名称

   * **[!UICONTROL Account]**: 用户的名称

   * **[!UICONTROL Password]**: 用户帐户密码

   * **[!UICONTROL Time zone]**: 服务器时区
   ![](assets/oracle_config.png)

### Linux上的Oracle {#for-linux-1}

在联合数据访问下连接到Oracle外部数据库需要在Adobe Campaign服务器上进行以下其他配置。

1. 安装与您的Oracle版本对应的Oracle完整客户端。
1. 将TNS定义添加到安装中。 为此，请在/etc/oracle **存储库的tnsnames** .ora文件中指定它们。 如果此存储库不存在，请创建它。

   然后新建一个TNS_ADMIN环境变量： 导出TNS_ADMIN=/etc/oracle并重新启动计算机。

1. 将Oracle集成到Adobe Campaign服务器(nlserver)中。 为此，请检查Adobe Campaign服 **务器树结构的** “nl6”文件夹中是否存在customer.sh文件，以及它是否包含指向Oracle库的链接。

   例如，对于11.2中的客户端：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >这些值（特别是ORACLE_HOME）取决于您的安装存储库。 在引用这些值之前，请务必检查树结构。

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

1. 在Campaign Classic中，您随后可以配置 [!DNL Oracle] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#oracle-external)。

### Windows上的Oracle {#for-windows-1}

在联合数据访问下连接到Oracle外部数据库需要在Adobe Campaign服务器下面进行其他配置。

1. 安装Oracle客户端。

1. 在C:Oracle文件夹中，创建包 **含您的TNS定义** 的tnsnames.ora文件。

1. 添加一个TNS_ADMIN环境变量，将C:Oracle作为值并重新启动计算机。

1. 在Campaign Classic中，您随后可以配置 [!DNL Oracle] 外部帐户。 有关如何配置外部帐户的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#oracle-external)。