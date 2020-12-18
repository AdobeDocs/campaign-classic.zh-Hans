---
solution: Campaign Classic
product: campaign
title: 配置访问Hadoop
description: 了解如何在联合数据访问配置访问Hadoop
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# 配置对Hadoop{#configure-access-to-hadoop}的访问

使用活动&#x200B;**联合数据访问**(联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置访问Hadoop。

1. 配置[Hadoop数据库](#configuring-hadoop)
1. 将Hadoop[外部帐户](#hadoop-external)配置为活动

## 配置Hadoop3.0 {#configuring-hadoop}

在联合数据访问中连接到Hadoop外部数据库需要Adobe Campaign服务器上的以下配置。 请注意，此配置适用于Windows和Linux。

1. 根据您的操作系统版本，下载Hadoop的ODBC驱动程序。 驱动程序可在[此页](https://www.cloudera.com/downloads.html)上找到。

1. 然后，您需要安装ODBC驱动程序并为配置单元连接创建DSN。 说明可在[此页](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)中找到

1. 下载和安装ODBC驱动程序后，需要重新启动Campaign Classic。 要执行此操作，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，您随后可以配置[!DNL Hadoop]外部帐户。 有关如何配置外部帐户的详细信息，请参阅[本节](#hadoop-external)。

## Hadoop外部帐户{#hadoop-external}

[!DNL Hadoop]外部帐户允许您将活动实例连接到Hadoop外部数据库。

1. 在Campaign Classic中，配置[!DNL Hadoop]外部帐户。 在&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**.

1. 选择&#x200B;**[!UICONTROL External database]**&#x200B;作为外部帐户的&#x200B;**[!UICONTROL Type]**。

1. 配置&#x200B;**[!UICONTROL Hadoop]**&#x200B;外部帐户，必须指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE,Sybase IQ)

   * **[!UICONTROL Server]**:DNS的名称

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:如果未在DSN中指定数据库的名称。如果在DSN中指定，则可将其留空

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
| bulkKey | Azureblob或DataLake访问密钥 | 对于wasb://或wasbs://批量加载程序(即，如果批量加载工具与wasb://或wasbs://开始)。 <br>它是用于批量加载的blob或DataLake存储桶的访问密钥。 |
| hdfsPort | 端口号<br>默认设置为8020 | 对于HDFS批量加载(即，如果批量加载工具开始为webhdfs://或webhdfss://)。 |
| bucketsNumber | 20 | 创建聚簇表时的桶数。 |
| fileFormat | 镶木 | 工作表的默认文件格式。 |


## 配置Hadoop2.1 {#configure-access-hadoop-2}

如果需要连接到Hadoop2.1，请按照以下步骤操作[Windows](#for-windows)或[Linux](#for-linux)。

### Hadoop2.1 for Windows {#for-windows}

1. 为Windows安装ODBC和[Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886)驱动程序。
1. 通过运行ODBC数据源管理工具创建DSN（数据源名称）。 Hive的系统DSN范例供您修改。

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. 创建Hadoop外部帐户，详见[本节](#hadoop-external)。

### Hadoop2.1 for Linux {#for-linux}

1. 安装unixodbc for Linux。

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
   >此处的&#x200B;**UseNativeQuery**&#x200B;参数非常重要。 活动识别配置单元，除非设置UseNativeQuery，否则将无法正常工作。 通常，驱动程序或Hive SQL Connector将重写查询并篡改列顺序。

   身份验证设置取决于配置单元/Hadoop配置。 例如，对于HD Insight，请使用AuthMech=6进行用户／密码身份验证，如[此处](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)所述。

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

1. 创建Hadoop外部帐户，详见[本节](#hadoop-external)。

