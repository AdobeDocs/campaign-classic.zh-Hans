---
solution: Campaign Classic
product: campaign
title: 配置对Vertica的访问权限
description: 了解如何在FDA中配置对Vertica的访问
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# 配置对Vertica的访问权限 {#configure-fda-vertica}

![](../../assets/v7-only.svg)

使用Campaign **联合数据访问**(FDA)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对[!DNL Vertica]的访问。

1. 在[CentOS](#vertica-centos)、[Windows](#vertica-windows)或[Debian](#vertica-debian)上配置[!DNL Vertica]
1. 在Campaign中配置[!DNL Vertica] [外部帐户](#vertica-external)


>[!NOTE]
>
>[!DNL Vertica] 连接器可用于混合部署和内部部署。有关详细信息，请参见[此页面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## CentOS上的Vertica {#vertica-centos}

要在CentOS上配置[!DNL Vertica]，请执行以下步骤：

1. 下载[!DNL Vertica]的ODBC驱动程序。 [单](https://www.vertica.com/download/vertica/client-drivers/) 击此处下载最新的Linux RPM。

1. 然后，您需要使用以下命令安装unixODBC:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. 如果您之前已安装[!DNL Vertica]服务器，则已安装ODBC驱动程序。 在这种情况下，请按如下方式更新驱动器：

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

1. 然后，在Adobe Campaign中，您可以配置[!DNL Vertica]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#vertica-external)。

## Windows上的Vertica {#vertica-windows}

1. 下载适用于Windows](https://www.vertica.com/download/vertica/client-drivers/)的[ODBC驱动程序。 要安装Windows驱动程序，您需要启用.NET Framework 3.5，否则安装向导将尝试自动启用并下载它。

1. 在Windows中配置ODBC驱动程序。 有关更多信息，请参见[此页面](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. 然后，在Adobe Campaign中，您可以配置[!DNL Vertica]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#vertical-external)。

## 德比语上的维蒂卡 {#vertica-debian}

1. 下载[!DNL Vertica]的ODBC驱动程序。 [单击此](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 处开始下载。

1. 然后，您需要使用以下命令安装unixODBC:

   ```
   apt-get install unixODBC
   ```

1. 如果您之前已安装[!DNL Vertica]服务器，则已安装ODBC驱动程序。 在这种情况下，请按如下方式更新驱动器：

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

1. 然后，在Adobe Campaign中，您可以配置[!DNL Vertica]外部帐户。 有关如何配置外部帐户的更多信息，请参阅[此部分](#vertica-external)。

## Vertica外部帐户 {#vertica-external}

您需要创建一个[!DNL Vertica]外部帐户，以将Campaign实例连接到[!DNL Vertica]外部数据库。

1. 在Campaign **[!UICONTROL Explorer]**&#x200B;中，单击&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**。

1. 选择&#x200B;**[!UICONTROL External database]**&#x200B;作为外部帐户的&#x200B;**[!UICONTROL Type]**。

1. 配置&#x200B;**[!UICONTROL Vertica]**&#x200B;外部帐户时，必须指定：

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**:服务器的 [!DNL Vertica] URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称
   ![](assets/vertica.png)
