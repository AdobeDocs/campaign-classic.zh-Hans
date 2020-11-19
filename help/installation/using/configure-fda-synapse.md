---
title: 配置对突触的访问
description: 了解如何在联合数据访问中配置对突触的访问
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: be3626e858ced32e9dbfd5d07da29a4ccf256ac4
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 1%

---


# 配置访问Azure synapse {#configure-access-to-azure-synapse}

使用活动 [联合数据访问](../../installation/using/about-fda.md) (联合数据访问)选项处理存储在外部数据库中的信息。 请按照以下步骤配置对MicrosoftAzure synapse分析的访问。

1. 在CentOS、Windows [或Debian](#azure-centos)上 [配置](#azure-windows) Azure synapse [。](#azure-debian)
1. 在Azure synapse中 [配置活动](#azure-external) 外部帐户

## azure synapseCentOS {#azure-centos}

>[!CAUTION]
>
>* 您需要根权限才能安装ODBC驱动程序。
>* Microsoft提供的Red Hat Enterprise ODBC驱动程序也可与CentOS一起使用，以连接到SQL Server。
>* 版本13.0将适用于Red Hat 6和7。


要在CentOS上配置Azure synapse，请执行以下步骤：

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

1. 在活动中，您随后可以配置 [!DNL Azure Synapse] 外部帐户。 有关如何配置外部帐户的详细信息，请参 [阅此部分](#azure-external)。

1. 由于Azure synapse分析通过TCP 1433端口进行通信，您需要在防火墙上打开此端口。 使用以下命令：

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >要允许来自Azure synapse分析团队的通信，您可能需要将公共IP添加到允许列表。 为此，请参阅Azure [文档](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。

1. 如果是iptables，请运行以下命令：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## azure synapseWindows版 {#azure-windows}

>[!NOTE]
>
>这是ODBC驱动程序版本13独有的，但Adobe Campaign Classic还可以使用SQL Server本机客户端驱动程序11.0和10.0。

在Windows上配置Azure synapse:

1. 首先，安装Microsoft ODBC驱动程序。 您可以在此页 [中找到它](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。

1. 选择要安装的以下文件：

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. 安装ODBC驱动程序后，可以根据需要测试它。 有关详细信息，请参见此 [ 页面](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)。

1. 在Campaign Classic中，您随后可以配置 [!DNL Azure Synapse] 外部帐户。 有关如何配置外部帐户的详细信息，请参 [阅此部分](#azure-external)。

1. 由于Azure synapse分析通过TCP 1433端口进行通信，您需要在Windows Defender Firewall上打开此端口。 For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

## azure synapse德比 {#azure-debian}

**先决条件:**

* 您需要根权限才能安装ODBC驱动程序。
* 安装msodbcsql包时需要Curl。 如果尚未安装，请运行以下命令：

   ```
   sudo apt-get install curl
   ```

在Debian上配置Azure synapse:

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

1. 在Campaign Classic中，您现在可以配置 [!DNL Azure Synapse] 外部帐户。 有关如何配置外部帐户的详细信息，请参 [阅此部分](#azure-external)。

1. 要在Debian上配置iptables以确保与Azure synapse分析器连接，请使用以下命令为主机名启用出站TCP 1433端口：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >要允许来自Azure synapse分析团队的通信，您可能需要将公共IP添加到允许列表。 为此，请参阅Azure [文档](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。


## azure synapse外部帐户 {#azure-external}

外部帐户 [!DNL Azure Synapse] 允许您将活动实例连接到Azure synapse外部数据库。

要创建您的 [!DNL Azure Synapse] 外部帐户，请按照以下步骤操作：

1. 在活动 **[!UICONTROL Explorer]**&#x200B;中， **[!UICONTROL Administration]** 单击“>” **[!UICONTROL Platform]** “>” **[!UICONTROL External accounts]**。

1. 单击 **[!UICONTROL New]**.

1. 选 **[!UICONTROL External database]** 择作为外部帐户 **[!UICONTROL Type]**。

   ![](assets/azure_1.png)

1. 配置 [!DNL Azure Synapse] 外部帐户，必须指定：

   * **[!UICONTROL Type]**:azure synapse分析

   * **[!UICONTROL Server]**:azure synapse服务器的URL

   * **[!UICONTROL Account]**:用户的名称

   * **[!UICONTROL Password]**:用户帐户密码

   * **[!UICONTROL Database]**:数据库的名称

