---
product: campaign
title: 配置对Hadoop的访问权限
description: 了解如何在FDA中配置对Hadoop的访问权限
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 1%

---

# 配置对Hadoop的访问权限 {#configure-access-to-hadoop}



使用Campaign **联合数据访问** (FDA)选项处理存储在外部数据库中的信息。 按照以下步骤配置对Hadoop的访问权限。

1. 配置[Hadoop数据库](#configuring-hadoop)
1. 在Campaign中配置Hadoop[外部帐户](#hadoop-external)

## 配置Hadoop3.0 {#configuring-hadoop}

在Adobe Campaign服务器上连接到FDA中的Hadoop外部数据库需要以下配置。 请注意，此配置适用于Windows和Linux。

1. 根据您的操作系统版本，下载用于Hadoop的ODBC驱动程序。 可以在[此页面](https://www.cloudera.com/downloads.html)中找到驱动程序。

1. 然后，您需要安装ODBC驱动程序并为Hive连接创建DSN。 可在[此页面](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)中找到说明

1. 下载并安装ODBC驱动程序后，需要重新启动Campaign Classic。 为此，请运行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，您可以配置[!DNL Hadoop]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#hadoop-external)。

## hadoop外部帐户 {#hadoop-external}

[!DNL Hadoop]外部帐户允许您将Campaign实例连接到Hadoop外部数据库。

1. 在Campaign Classic中，配置您的[!DNL Hadoop]外部帐户。 在&#x200B;**[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**。

1. 选择&#x200B;**[!UICONTROL External database]**&#x200B;作为外部帐户的&#x200B;**[!UICONTROL Type]**。

1. 配置&#x200B;**[!UICONTROL Hadoop]**&#x200B;外部帐户，您必须指定：

   * **[!UICONTROL Type]**： ODBC (Sybase ASE，Sybase IQ)

   * **[!UICONTROL Server]**： DNS的名称

   * **[!UICONTROL Account]**：用户的名称

   * **[!UICONTROL Password]**：用户帐户密码

   * **[!UICONTROL Database]**：如果未在DSN中指定数据库的名称。 如果在DSN中指定，它可以留空

   * **[!UICONTROL Time zone]**：服务器时区

   ![](assets/hadoop3.png)

连接器支持以下ODBC选项：

| 名称 | 值 |
|---|---|
| ODBCMgr | iODBC |
| 仓库 | 1/2/4 |

该连接器还支持以下Hive选项：

| 名称 | 值 | 说明 |
|---|---|---|
| 批量密钥 | Azure Blob或DataLake访问密钥 | 对于wasb://或wasbs://批量加载器(即，批量加载工具是否以wasb://或wasbs://开头)。 <br>它是用于批量加载的blob或DataLake存储桶的访问密钥。 |
| hdfsPort | 端口号<br>默认设置为8020 | 对于HDFS批量加载(即，批量加载工具是否以webhdfs://或webhdfss://开头)。 |
| bucketsNumber | 20 | 创建聚簇表时的存储段数。 |
| 文件格式 | PARQUET | 工作表的默认文件格式。 |


## 配置Hadoop2.1 {#configure-access-hadoop-2}

如果您需要连接到Hadoop2.1，请按照下面介绍的[Windows](#for-windows)或[Linux](#for-linux)步骤操作。

### WindowsHadoop2.1 {#for-windows}

1. 安装适用于Windows的ODBC和[Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886)驱动程序。
1. 通过运行ODBC DataSource Administrator工具创建DSN (数据Source名称)。 提供了用于Hive的系统DSN示例供您修改。

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. 创建Hadoop外部帐户，如[此部分](#hadoop-external)中所述。

### 适用于Linux的Hadoop2.1 {#for-linux}

1. 安装适用于Linux的unixodbc。

   ```
   apt-get install unixodbc
   ```

1. 从HortonWorks下载并安装适用于Apache Hive的ODBC驱动程序： [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html)。

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

1. 创建DSN(数据Source名称)并编辑odbc.ini文件。 然后，为配置单元连接创建一个DSN。

   以下是HDInsight设置名为“病毒式”的连接的一个示例：

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
   >此处的&#x200B;**UseNativeQuery**&#x200B;参数非常重要。 Campaign具有配置单元感知功能，除非设置UseNativeQuery，否则将无法正常工作。 通常，驱动程序或Hive SQL Connector将重写查询并篡改列顺序。

   身份验证设置取决于配置单元/Hadoop配置。 例如，对于HD Insight，使用AuthMech=6进行用户/密码身份验证，如[此处](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)所述。

1. 导出变量。

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. 通过/usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini设置Hortonworks驱动程序。

   您必须使用UTF-16才能与Campaign和unix-odbc (libodbcinst)连接。

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
