---
product: campaign
title: 配置对Vertica的访问权限
description: 了解如何在FDA中配置对Vertica的访问
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 2%

---

# 配置对Vertica的访问权限 {#configure-fda-vertica}

![](../../assets/v7-only.svg)

使用Campaign **联合数据访问** (FDA)选项，用于处理存储在外部数据库中的信息。 请按照以下步骤配置对 [!DNL Vertica].

1. 配置 [!DNL Vertica] on [CentOS](#vertica-centos), [Windows](#vertica-windows) 或 [德比安](#vertica-debian)
1. 配置 [!DNL Vertica] [外部帐户](#vertica-external) 在Campaign中

>[!NOTE]
>
>[!DNL Vertica] 连接器可用于混合部署和内部部署。 有关详细信息，请参见[此页面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## CentOS上的Vertica {#vertica-centos}

配置 [!DNL Vertica] 在CentOS上，执行以下步骤：

1. 下载用于 [!DNL Vertica]. [单击此处](https://www.vertica.com/download/vertica/client-drivers/) 并下载最新的Linux RPM。

1. 然后，您需要使用以下命令安装unixODBC:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. 如果您之前已安装 [!DNL Vertica] 服务器上，将已安装ODBC驱动程序。 在这种情况下，请按如下方式更新驱动器：

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. 在Adobe Campaign中，您随后可以配置 [!DNL Vertica] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#vertica-external).

## Windows上的Vertica {#vertica-windows}

1. 下载 [用于Windows的ODBC驱动程序](https://www.vertica.com/download/vertica/client-drivers/). 要安装Windows驱动程序，您需要启用.NET Framework 3.5，否则安装向导将尝试自动启用并下载它。

1. 在Windows中配置ODBC驱动程序。 有关更多信息，请参阅 [本页](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. 在Adobe Campaign中，您随后可以配置 [!DNL Vertica] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#vertical-external).

## 德比语上的维蒂卡 {#vertica-debian}

1. 下载用于 [!DNL Vertica]. [单击此处](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 开始下载。

1. 然后，您需要使用以下命令安装unixODBC:

   ```
   apt-get install unixODBC
   ```

1. 如果您之前已安装 [!DNL Vertica] 服务器上，将已安装ODBC驱动程序。 在这种情况下，请按如下方式更新驱动器：

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
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. 在Adobe Campaign中，您随后可以配置 [!DNL Vertica] 外部帐户。 有关如何配置外部帐户的更多信息，请参阅 [此部分](#vertica-external).

## Vertica外部帐户 {#vertica-external}

您需要创建 [!DNL Vertica] 外部帐户将Campaign实例连接到 [!DNL Vertica] 外部数据库。

1. 从Campaign **[!UICONTROL Explorer]**，单击 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 单击 **[!UICONTROL New]**。

1. 选择 **[!UICONTROL External database]** 作为外部帐户的 **[!UICONTROL Type]**.

1. 配置 **[!UICONTROL Vertica]** 外部帐户，您必须指定：

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**:的URL [!DNL Vertica] 服务器

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

   ![](assets/vertica.png)

连接器支持以下选项：

| Option | 说明 |
|---|---|
| 时区名称 | 默认为空，这表示使用Campaign Classic应用程序服务器的系统时区。 可以使用选项强制使用TIMEZONE会话参数。 |

