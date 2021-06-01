---
product: campaign
title: 配置对Hadoop的访问
description: 了解如何在FDA中配置对Hadoop的访问
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 1%

---

# 配置对Hadoop{#configure-access-to-hadoop}的访问

使用Campaign **联合数据访问**(FDA)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对Hadoop的访问。

1. 配置[Hadoop数据库](#configuring-hadoop)
1. 在Campaign中配置Hadoop[外部帐户](#hadoop-external)

## 配置Hadoop3.0 {#configuring-hadoop}

在FDA中连接到Hadoop外部数据库需要在Adobe Campaign服务器上进行以下配置。 请注意，此配置适用于Windows和Linux。

1. 下载ODBC驱动程序以进行Hadoop，具体取决于您的操作系统版本。 可在[此页面](https://www.cloudera.com/downloads.html)上找到驱动程序。

1. 然后，您需要安装ODBC驱动程序并为配置单元连接创建DSN。 有关说明，请参见[此页面](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. 下载并安装ODBC驱动程序后，需要重新启动Campaign Classic。 为此，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，您可以配置[!DNL Hadoop]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#hadoop-external)。

## Hadoop外部帐户{#hadoop-external}

[!DNL Hadoop]外部帐户允许您将Campaign实例连接到Hadoop外部数据库。

1. 在Campaign Classic中，配置[!DNL Hadoop]外部帐户。 从&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**。

1. 选择&#x200B;**[!UICONTROL External database]**&#x200B;作为外部帐户的&#x200B;**[!UICONTROL Type]**。

1. 配置&#x200B;**[!UICONTROL Hadoop]**&#x200B;外部帐户时，必须指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE，Sybase IQ)

   * **[!UICONTROL Server]**:DNS的名称

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:未在DSN中指定数据库的名称。如果在DSN中指定，则可将其留空

   * **[!UICONTROL Time zone]**:服务器时区

   ![](assets/hadoop3.png)

连接器支持以下ODBC选项：

| 名称 | 值 |
|---|---|
| ODBCMgr | iODBC |
| 仓库 | 1/2/4 |

连接器还支持以下配置单元选项：

| 名称 | 值 | 说明 |
|---|---|---|
| bulkKey | Azure blob或DataLake访问密钥 | 对于wasb://或wasbs://批量加载器(即，批量加载工具以wasb://或wasbs://开头)。 <br>它是blob或DataLake存储段的访问密钥，用于批量加载。 |
| hdfsPort | 端口号<br>默认设置为8020 | 对于HDFS批量加载(即，如果批量加载工具以webhdfs://或webhdfss://开头)。 |
| bucketsNumber | 20 | 创建群集表时的存储段数。 |
| fileFormat | 镶木 | 工作表的默认文件格式。 |


## 配置Hadoop2.1 {#configure-access-hadoop-2}

如果需要连接到Hadoop2.1，请按照下面描述的[Windows](#for-windows)或[Linux](#for-linux)的步骤操作。

### Hadoop2.1 for Windows {#for-windows}

1. 安装ODBC和[Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) Windows驱动程序。
1. 通过运行ODBC数据源管理员工具创建DSN（数据源名称）。 为配置单元提供系统DSN示例供您修改。

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. 创建Hadoop外部帐户，如[此部分](#hadoop-external)中所述。

### Hadoop2.1 for Linux {#for-linux}

1. 安装适用于Linux的unixodbc。

   ```
   apt-get install unixodbc
   ```

1. 从HortonWorks下载并安装Apache Hive的ODBC驱动程序：[https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html)。

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

1. 创建DSN（数据源名称）并编辑odbc.ini文件。 然后，为配置单元连接创建DSN。

   以下是HDInsight设置名为“病毒”的连接的示例：

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
   >此处的&#x200B;**UseNativeQuery**&#x200B;参数非常重要。 Campaign支持配置单元，除非设置UseNativeQuery，否则无法正常运行。 通常，驱动程序或配置单元SQL连接器将重写查询并篡改列排序。

   身份验证设置取决于配置单元/Hadoop配置。 例如，对于HD Insight，使用AuthMech=6进行用户/密码身份验证，如[此处](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)所述。

1. 导出变量。

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. 通过/usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini设置Hortonworks驱动程序。

   您必须使用UTF-16才能与Campaign和unix-odbc(libodbcinst)连接。

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

1. 创建Hadoop外部帐户，如[此部分](#hadoop-external)中所述。
