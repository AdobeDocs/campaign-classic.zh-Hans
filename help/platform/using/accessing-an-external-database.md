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
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 访问外部数据库{#accessing-an-external-database}

## 关于联合数据访问 {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>联 **合数据访问** (FDA)模块是可选的。 请检查您的Adobe Campaign许可协议。
>  
>此外，通过FDA访问外部数据库只能用于内部或混合安装。

### 工作原理 {#operating-principle}

FDA选项允许您从SQL源收集数据并自动检测目标表的结构。

要使用此功能，您必须：

1. 拥有一个与Adobe Campaign FDA模块兼容的外部数据库。 兼容性矩阵中详细列出了数据库系统和兼容 [版本](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。 用户还必须在Adobe Campaign [中](#remote-database-access-rights) ，以及外部数据库上具有必要的权限。
1. [在Adobe Campaign服务器上](#specific-configurations-by-database-type) ，安装与您的数据库相对应的驱动程序。
1. [创建和配置一个外部帐户](#connecting-to-the-database) ，该帐户允许您在Adobe Campaign和外部数据库之间建立连接。 有关可用外部帐户的详细信息，请参阅此 [页](../../platform/using/external-accounts.md)。
1. [在Adobe Campaign中创建外部数据库的读取架构](#creating-the-data-schema) 。 这允许您识别外部数据库的数据结构。
1. 最终， [从先前创建的架构创建新的目标映射](#defining-data-mapping) ，如果您的分发的收件人来自外部数据库，则此映射为新目标映射。 这就存在某些限制，特别是在个性化交付方面。

创建数据读取架构后，即可在Adobe Campaign工作流程中处理数据。 如需详细信息，请参阅[此部分](../../workflow/using/executing-a-workflow.md#architecture)。

### 最佳实践和建议 {#best-practices-and-recommendations}

FDA选项用于在工作流中以批处理模式处理外部数据库中的数据。 在另一个环境中使用FDA，例如，对于单一业务，必须采取预防措施（个性化、交互、实时交付等）。

在开始利用外部数据库之前，执行性能测试以检测任何可能的问题并使用此选项进行优化。

避免需要尽可能使用Adobe Campaign和外部数据库的操作。 为此，您可以：

* 将Adobe Campaign数据库导出到外部数据库，并仅在将结果重新导入Adobe Campaign之前从外部数据库执行操作。
* 从外部Adobe Campaign数据库收集数据并在本地执行操作。

如果您希望使用外部数据库中的数据在提交中实现个性化，请收集要在工作流中使用的数据，以便在临时表中提供。 然后使用临时表中的数据个性化您的交付。

### 限制 {#limitations}

FDA选项对您使用的外部数据库系统具有软限制。

出于性能原因，我们不建议使用此功能来执行统一操作（交付个性化、交互模块、实时）。

## 按数据库类型的特定配置 {#specific-configurations-by-database-type}

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及安装驱动程序并声明属于Adobe Campaign服务器上每个RDBMS的环境变量。

一般而言，您需要在Adobe Campaign服务器上的外部数据库上安装相应的客户端层。

>[!NOTE]
>
>兼容版本列在 [Campaign兼容性表中](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA) 。

### 配置对Hadoop的访问 {#configure-access-to-hadoop}

在FDA中连接到Hadoop外部数据库需要Adobe Campaign服务器上的以下配置。

#### 适用于Windows {#for-windows}

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

#### 对于Linux {#for-linux}

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

### 配置对MySQL的访问权限 {#configure-access-to-mysql}

有关如何配置MySQL数据库的详细信息，请参阅本 [文](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html)。

### 配置对Netezza的访问 {#configure-access-to-netezza}

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

### 配置对Oracle的访问权限 {#configure-access-to-oracle}

在FDA中连接到Oracle外部数据库需要在Adobe Campaign服务器上进行以下其他配置。

#### 对于Linux {#for-linux-1}

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

#### 适用于Windows {#for-windows-1}

1. 安装Oracle客户端。
1. 在C:Oracle文件夹中，创建一个 **包含您的TNS定义的tnsnames.ora** 文件。

   添加一个TNS_ADMIN环境变量，将C:Oracle作为值并重新启动计算机。

### 配置对Sybase IQ的访问 {#configure-access-to-sybase-iq}

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

### 配置对Teradata的访问 {#configure-access-to-teradata}

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

### 配置对SAP HANA的访问 {#configure-access-to-sap-hana}

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

   * **LD_LIBRARY_PATH**:它应包括指向SAP Hana客户端的链接(默认情况下为/usr/sap/hdbclient/ [libodbcHDB](http://libodbchdb.so/) .so)。
   * **ODBCINI**:odbc.ini文件的位置(例如/etc/odbc.ini)。

1. 创建SAP Hana外部帐户，如创建共享连 [接一节中所述](#creating-a-shared-connection) 。

## 远程数据库访问权限 {#remote-database-access-rights}

首先，为了使用户能够通过FDA对外部数据库执行操作，后者必须在Adobe Campaign中具有特定的名称。

1. 在Adobe **[!UICONTROL Administration > Access Management > Named Rights]** Campaign资源管理器中选择节点。
1. 通过指定所选标签创建新权限。
1. 字段 **[!UICONTROL Name]** 必须采用以下格式 **用户：base@server**，其中：

   * **user** 与外部数据库中用户的名称相对应。
   * **base** 与外部数据库的名称相对应。
   * **server** 对应于外部数据库服务器的名称。

      >[!NOTE]
      >
      >Oracle **中的** :base部件是可选的。

1. 保存指定的右侧，然后从Adobe Campaign浏览器的节 **[!UICONTROL Administration > Access Management > Operators]** 点将其链接到所选用户。

然后，要处理外部数据库中包含的数据，Adobe Campaign用户必须对数据库至少拥有“写入”权限才能创建工作表。 Adobe Campaign会自动删除这些内容。

一般而言，下列权利是必要的：

* **CONNECT**:连接到远程数据库，
* **读取数据**:只读访问包含客户数据的表，
* **阅读“MetaData”**:访问服务器数据目录以获得表结构，
* **加载**:在工作表中成批加载（处理集合和连接时需要）,
* **为TABLE** / **INDEX/PROCEDURE/FUNCTION创建／删除**,
* **说明** （建议）:以便在遇到问题时监控性能，
* **写入数据** （取决于集成方案）。

>[!NOTE]
>
>数据库管理员需要使这些权限与每个数据库引擎的特定权限相匹配。 有关详细信息，请参阅 [RDBMS特定权限](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html)。

## 连接到数据库 {#connecting-to-the-database}

要启用与外部数据库的连接，必须指示连接参数，即目标数据源和需要加载数据的表的名称。

>[!CAUTION]
>
>Adobe Campaign用户需要外部数据库和Adobe Campaign应用程序服务器的特定权限才能处理来自外部数据库的数据。 有关详细信息，请参阅远程数 [据库访问权限部分](#remote-database-access-rights) 。
>
>要避免任何故障，访问远程共享数据的操作员必须从不同的空间工作。

### 创建共享连接 {#creating-a-shared-connection}

要启用与共享外部数据库的连接，只要此连接处于活动状态，就可以通过Adobe Campaign访问该数据库。

1. 配置必须通过节点预先定 **[!UICONTROL Administration > Platform > External accounts]** 义。
1. 单击按 **[!UICONTROL New]** 钮并选择类 **[!UICONTROL External database]** 型。
1. 定义外 **[!UICONTROL Connection]** 部数据库的参数。

   对于与 **ODBC** **[!UICONTROL Server]** type数据库的连接，字段必须包含ODBC数据源的名称，而不包含服务器名称。 此外，可能需要某些附加配置，具体取决于所使用的数据库。 请参阅“按数 [据库类型的特定配置](#specific-configurations-by-database-type) ”部分。

1. 输入参数后，单击按钮 **[!UICONTROL Test the connection]** 以批准这些参数。

   ![](assets/wf-external-account-create.png)

1. 如有必要，请取消选 **[!UICONTROL Enabled]** 中此选项，以禁用对此数据库的访问，而不删除其配置。
1. 要允许Adobe Campaign访问此数据库，必须部署SQL函数。 单击选 **[!UICONTROL Parameters]** 项卡，然后单击 **[!UICONTROL Deploy functions]** 按钮。

   ![](assets/wf-external-account-functions.png)

您可以在选项卡中为表和索引定义特定的工作表空间 **[!UICONTROL Parameters]** 空间。

### 使用Windows身份验证创建连接 {#creating-a-connection-with-windows-authentication}

您还可以通过FDA使用Windows身份验证进行连接。 操作步骤：

* 确保Adobe Campaign服务由与本地系统帐户不同的Windows帐户执行。
* 确保Adobe Campaign运营商为Adobe Campaign应用程序服务器和外部数据库分配了足够的权限。
* 无需指定和，即可创建相应的外 **[!UICONTROL Account]** 部帐户 **[!UICONTROL Password]**。 仅指定数据库的名称。

### 创建临时连接 {#creating-a-temporary-connection}

您可以从工作流活动直接定义到外部数据库的连接。 在这种情况下，它将位于本地外部数据库上，保留该数据库以用于当前工作流：它不会保存在外部帐户中。 可以在工作流的不同活动（尤其是、活动或活动）上创 **[!UICONTROL Query]**&#x200B;建此类 **[!UICONTROL Data loading (RDBMS)]**&#x200B;型的 **[!UICONTROL Enrichment]** 准时连接 **[!UICONTROL Split]** 。

>[!CAUTION]
>
>不建议使用此类配置，但可定期用于收集数据。 但是，您应创建外部帐户，如创建共 [享连接部分中所示](#creating-a-shared-connection) 。

例如，在查询活动中，创建到外部数据库的定期连接的步骤如下：

1. 单击该 **[!UICONTROL Add data...]** 选项，然后选 **[!UICONTROL External data]** 择选项。
1. 选择选 **[!UICONTROL Locally defining the data source]** 项。

   ![](assets/wf_add_data_local_external_data.png)

1. 在下拉列表中选择目标数据库引擎。 输入服务器的名称并提供身份验证参数。

   还指定外部数据库的名称。

   ![](assets/wf_add_data_local_external_data_param.png)

   Click the **[!UICONTROL Next]** button.

1. 选择存储数据的表。

   您可以直接在相应的字段中输入表的名称，或单击编辑图标以访问数据库表的列表。

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 单击按 **[!UICONTROL Add]** 钮可定义外部数据库数据与Adobe Campaign数据库中数据之间的一个或多个对帐字段。 和 **[!UICONTROL Edit expression]** 的图 **[!UICONTROL Remote field]** 标 **[!UICONTROL Local field]** 允许您访问每个表的字段列表。

   ![](assets/wf_add_data_local_external_data_join.png)

1. 如果需要，请指定过滤条件和数据排序模式。
1. 选择要在外部数据库中收集的其他数据。 为此，请双击要添加的字段，以在中显示这些字段 **[!UICONTROL Output columns]**。

   ![](assets/wf_add_data_local_external_data_select.png)

   单击 **[!UICONTROL Finish]** 以确认此配置。

### 安全连接 {#secure-connection}

在配置外部FDA帐户时，您可以安全地访问外部数据库。

为此，请在使用的端口的服务&#x200B;**器地址和地址后添加“:ssl**”。 例如： **192.168.0.52:4501:ssl**。

数据随后将通过安全SSL协议发送。

### 其他配置 {#additional-configurations}

如有必要，您可以创建用于处理外部数据库中数据的架构。 同样，Adobe Campaign允许您定义外部表中数据的映射。 这些配置是常规的，不仅适用于工作流。

>[!NOTE]
>
>有关在Adobe Campaign中创建架构和定义新数据映射的详细信息，请参 [阅此页](../../configuration/using/about-schema-edition.md)。

## 创建数据架构 {#creating-the-data-schema}

要在外部数据库上创建架构，请单击 **[!UICONTROL New]** 数据架构列表上方的按钮，然后选择 **[!UICONTROL Access external data]**。

![](assets/wf_new_schema_fda.png)

输入架构的名称和说明，然后选择将启用与数据库连接的外部帐户。 这允许访问外部基础中可用的表列表。 选择包含要收集的数据的表。

![](assets/wf_new_schema_select_table_fda.png)

Click **[!UICONTROL OK]** to confirm. Adobe Campaign会自动检测选定表的结构并生成逻辑架构。

>[!NOTE]
>
>Adobe Campaign不生成链接。

单击 **[!UICONTROL Save]** 以确认创建。

![](assets/wf_new_schema_generate_fda.png)

在映射表（标准或FDA映射）时，会自动创建索引。

## 定义数据映射 {#defining-data-mapping}

Adobe Campaign允许您定义外部表中数据的映射。

为此，在创建外部表的架构后，您需要创建新的交付映射以将此表中的数据用作交付目标。

为此，请应用以下步骤：

1. 创建新的交付映射并选择定位维，例如您刚创建的架构。

   ![](assets/wf_new_mapping_create_fda.png)

1. 指示存储传送信息的字段（姓、名、电子邮件、地址等）。

   ![](assets/wf_new_mapping_define_join.png)

1. 指定信息存储的参数，包括扩展架构的后缀，以便它们能够轻松识别。

   ![](assets/wf_new_mapping_define_names.png)

   您可以选择是将排除(**excludelog**)、消息(**broadlog**)存储在单独的表中。

   您还可以选择是否管理此交付映射的跟踪(跟&#x200B;**踪日志**)。

1. 然后选择要考虑的扩展。 扩展类型取决于平台的参数和选项（查看许可证合同）。

   ![](assets/wf_new_mapping_define_extensions.png)

   单击按 **[!UICONTROL Save]** 钮以启动交付映射创建：所有链接的表都会根据选定参数自动创建。

## 其他选项 {#additional-options}

### 到远程实例的HTTP中继 {#http-relay-to-a-remote-instance}

您可以使用HTTP协议访问在远程实例中配置的外部数据库。

>[!NOTE]
>
>并非所有SQL数据类型都受此功能支持。 根本不支持Blob数据类型。 其他数据类型可能无法工作，具体取决于目标数据库（例如，Microsoft SQL server上的时间戳）。 请与Adobe支持部门联系以了解更多信息。

这简化了两个实例之间的数据传输和同步。 它还允许您绕过实例与远程数据库之间的任何通道以及客户端层的安装以访问此数据库。 目标实例可以是托管实例。

>[!CAUTION]
>
>此选项仅用于简化数据复制流(ETL)。
>
>例如，它允许云托管实例直接访问“内部部署”托管数据库中的数据。 但是，它不打算允许直接从云在“预置”托管数据库中进行定位。

为此，必须配置两个实例的外部帐户，以便本地实例可以使用HTTP协议与远程实例通信：

* 本地实例：选择新的连 **[!UICONTROL HTTP relay to a remote database]** 接类型。

   在批量负载数据传输时，还要指定缓冲区大小。 如果要减小传输的数据的大小，请选择压缩选项。

   必须 **[!UICONTROL Data source]** 使用以下语法定义：&quot;nms:extAccount: `<internal_name_of_the_external_account>`”

   ![](assets/fda_over_http_1.png)

   >[!NOTE]
   >
   >我们建议您使用HTTPS连接。

* 远程实例：在通过HTTP中继访问的数据库的FDA外部帐户中，检查的目标 **[!UICONTROL 'HTTP relay to a remote database' account option]**。

   ![](assets/fda_over_http_2.png)

以下示例显示了新的可能操作模式：

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>远程实例的默认数据库也必须通过外部帐户进行访问。

此操作方法避免了每个实例的清除工作流删除使用该实例作为中继的数据库的工作表。

因此，在上一个示例中，远程实例的清除工作流将不会对红色的FDA数据库执行任何操作，因为本地实例使用它。

### 直接创建临时架构 {#directly-creating-temporary-schemas}

如果要管理对FDA外部数据库的多次访问，则可使用新选项在配置外部帐户时直接创建工作架构。

>[!NOTE]
>
>此选项仅适用于PostgreSQL。

![](assets/fda_work_table.png)

### 利用外部数据优化电子邮件个性化 {#optimizing-email-personalization-with-external-data}

从内部版本8740开始， **[!UICONTROL Prepare the personalization data with a workflow]** 该选项现在在交付属 **[!UICONTROL Analysis]** 性的选项卡中可用。

在分发分析过程中，此选项会自动创建并执行一个工作流，该工作流将链接到目标的所有数据存储在临时表中，包括FDA中链接的表中的数据。

通过选中此选项，您可以显着提高执行个性化的性能。

### 云消息- FDA同步 {#cloud-messaging---fda-synchronization}

当Cloud Messaging服务器和Marketing服务器长期未同步时，Marketing服务器上缺失的广播数量可能很大。 为了通过FDA优化广播同步， **已添加NmsMidSourcing_LogsPeriodHour** 选项。 这允许指定最大时间段（以小时为单位），以限制每次执行同步工作流时恢复的广播日志数。

该选项将添加到控制台中的节 **[!UICONTROL Administration > Options]** 点。

>[!CAUTION]
>
>此选项仅 **能用** 于通过FDA同步大量广播。

>[!NOTE]
>
>仅当存在上次恢复日期时，才考虑此选项(**NmsMidSourcing_LastBroadLog_*选项** )。

### 消息中心——对XtkFolder表的读取访问权限 {#message-center---read-access-on-the-xtkfolder-table}

从构建8141及更高版本开始，如果消息中心使用FDA作为存档模式，则需要手动操作。

您需要向与外部FDA帐户链接的用户授予对XtKF旧表的读取权限。

例如，对于PostgreSQL数据库，该命令如下所示：

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

此用户必须具有对以下表的读取权限：

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
此修改将删除“关系xtkfolder的权限已拒绝”错误消息。

如果在外部FDA帐户中选择的工作架构不是现成的Neolane帐户，则无需对访问权限进行此修改。

## 在工作流中使用来自外部数据库的数据 {#using-data-from-an-external-database-in-a-workflow}

在多个Adobe Campaign工作流程活动中，您可以使用外部数据库中存储的数据。

### 对外部数据进行过滤 {#filtering-on-external-data}

查询活动允许您添加外部数据并在定义的筛选器配置中使用它。

For more on this, refer to the [Query](../../workflow/using/targeting-data.md#selecting-data) section.

### 创建子集 {#creating-sub-sets}

拆分活动允许您创建子集。 您可以使用外部数据来定义要使用的筛选条件。

For more on this, refer to the [Split](../../workflow/using/split.md) section.

### 加载外部数据库 {#loading-external-database}

可以在数据加载(RDBMS)中使用外部数据。 此活动显示在数据加 [载部分](../../workflow/using/data-loading--rdbms-.md) 。

### 添加信息和链接 {#adding-information-and-links}

丰富化活动允许您向工作流的工作台添加其他数据，以及指向外部表的链接。 因此，它可以利用外部数据库中的数据。 此活动在“丰富化” [部分中](../../workflow/using/enrichment.md) 。
