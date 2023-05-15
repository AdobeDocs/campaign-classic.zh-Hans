---
product: campaign
title: 配置对Vertica analytics的访问权限
description: 了解如何在FDA中配置对Vertica analytics的访问
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 配置对Vertica analytics的访问权限 {#configure-fda-vertica}



使用Campaign **联合数据访问** (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对 [!DNL Vertica Analytics].

1. 配置 [!DNL Vertica Analytics] on [CentOS](#vertica-centos), [Windows](#vertica-windows) 或 [德比安](#vertica-debian)
1. 配置 [!DNL Vertica Analytics] [外部帐户](#vertica-external) 在Campaign中

![](assets/snowflake_3.png)

## vertica analyticsCentOS {#vertica-centos}

配置 [!DNL Vertica Analytics] 在CentOS上，执行以下步骤：

1. 下载用于 [!DNL Vertica Analytics]. [单击此处](https://www.vertica.com/download/vertica/client-drivers/) 并下载最新的Linux RPM。

1. 然后，您需要使用以下命令安装unixODBC:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. 如果您之前已安装 [!DNL Vertica Analytics] 服务器上，将已安装ODBC驱动程序。 在这种情况下，请按如下方式更新驱动器：

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [VerVertica Analyticstica]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. 在Adobe Campaign中，您随后可以配置 [!DNL Vertica Analytics] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#vertica-external).

## vertica analytics {#vertica-windows}

1. 下载 [用于Windows的ODBC驱动程序](https://www.vertica.com/download/vertica/client-drivers/). 要安装Windows驱动程序，您需要启用.NET Framework 3.5，否则安装向导将尝试自动启用并下载它。

1. 在Windows中配置ODBC驱动程序。 有关更多信息，请参阅 [本页](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. 在Adobe Campaign中，您随后可以配置 [!DNL Vertica Analytics] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#vertical-external).

## vertica analyticsDebian {#vertica-debian}

1. 下载用于 [!DNL Vertica Analytics]. [单击此处](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 开始下载。

1. 然后，您需要使用以下命令安装unixODBC:

   ```
   apt-get install unixODBC
   ```

1. 如果您之前已安装 [!DNL Vertica Analytics] 服务器上，将已安装ODBC驱动程序。 在这种情况下，请按如下方式更新驱动器：

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [Vertica Analytics]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. 在Adobe Campaign中，您随后可以配置 [!DNL Vertica Analytics] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#vertica-external).

## vertica analytics外部帐户 {#vertica-external}

您需要创建 [!DNL Vertica Analytics] 外部帐户将Campaign实例连接到 [!DNL Vertica Analytics] 外部数据库。

1. 从Campaign **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]**。

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL Vertica Analytics]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**:的URL [!DNL Vertica Analytics] 服务器

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

   ![](assets/vertica.png)

连接器支持以下选项：

| Option | 说明 |
|---|---|
| 时区名称 | 默认为空，这表示使用Campaign Classic应用程序服务器的系统时区。 可以使用选项强制使用TIMEZONE会话参数。 |

