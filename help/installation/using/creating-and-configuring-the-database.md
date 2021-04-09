---
solution: Campaign Classic
product: campaign
title: 创建和配置数据库
description: 创建和配置数据库
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 1%

---

# 创建和配置数据库{#creating-and-configuring-the-database}

创建数据库时，Adobe Campaign提供了两个不同的选项：

1. 创建或循环使用数据库：如果要创建新数据库或重复使用现有数据库，请选择此选项。 请参阅[案例1:创建/循环使用数据库](#case-1--creating-recycling-a-database)。
1. 使用现有数据库：如果管理员已创建空数据库并且您想使用它，请选择此选项；或扩展现有数据库的结构。 请参阅[案例2:使用现有数据库](#case-2--using-an-existing-database)。

下面详细介绍了配置步骤。

>[!CAUTION]
>
>开始库、用户和模式的名称不得以数字或包含特殊字符。
>
>只有&#x200B;**internal**&#x200B;标识符可以执行这些操作。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

## 案例1:创建/循环使用数据库{#case-1--creating-recycling-a-database}

创建数据库或循环使用现有库的步骤如下。 某些配置取决于所使用的数据库引擎：

涉及以下步骤：

* [第1步 — 选择数据库引擎](#step-1---selecting-the-database-engine),
* [步骤2 — 连接到服务器](#step-2---connecting-to-the-server),
* [第3步 — 数据库的连接和特性](#step-3---connection-and-characteristics-of-the-database),
* [步骤4 — 要安装的包](#step-4---packages-to-install),
* [第5步 — 创建步骤](#step-5---creation-steps),
* [第6步 — 创建数据库](#step-6---creating-the-database)。

### 步骤1 — 选择数据库引擎{#step-1---selecting-the-database-engine}

在下拉列表中选择数据库引擎。

![](assets/s_ncs_install_db_select_engine.png)

支持的数据库列在活动[兼容性矩阵](../../rn/using/compatibility-matrix.md)中。

确定服务器并选择要执行的操作类型。 在这种情况下，**[!UICONTROL Create or recycle a database]**。

![](assets/s_ncs_install_db_oracle_creation01.png)

根据所选数据库引擎，服务器标识信息可能不同。

* 对于&#x200B;**Oracle**&#x200B;引擎，填充为应用程序服务器定义的&#x200B;**TNS名称**。
* 对于&#x200B;**PostgreSQL**&#x200B;或&#x200B;**DB2**&#x200B;引擎，必须指定应用程序服务器上定义的DNS名称（或IP地址）才能访问数据库服务器。
* 对于&#x200B;**Microsoft SQL Server**&#x200B;引擎，必须定义：应用程序服务器上定义的用于访问数据库服务器的DNS名称（或IP地址）：**DNS**&#x200B;或&#x200B;**DNS`\<instance>`**（实例模式），

   >[!CAUTION]
   >
   > 从20.3开始，Windows NT身份验证已停用。 **[!UICONTROL SQL Server authentication]** 现在是Microsoft SQL Server唯一可用的身份验证模式。[阅读更多](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### 步骤2 — 连接到服务器{#step-2---connecting-to-the-server}

在&#x200B;**[!UICONTROL Server access]**&#x200B;窗口中，定义数据库服务器访问。

![](assets/s_ncs_install_db_oracle_creation02.png)

要执行此操作，请输入&#x200B;**管理系统帐户**&#x200B;的名称和密码，该帐户具有访问数据库的权限，例如：

* **系统** 用于Oracle数据库，
* **对** 于Microsoft SQL Server数据库，
* **** PostgreSQL数据库，
* **db2inst1** 用于DB2数据库。

### 步骤3 — 数据库{#step-3---connection-and-characteristics-of-the-database}的连接和特性

通过以下步骤可配置登录数据库的设置。

![](assets/s_ncs_install_db_oracle_creation03.png)

您需要定义以下设置：

* 指定要创建的数据库的名称。

   >[!NOTE]
   >
   >对于DB2数据库，数据库名称不能超过8个字符。

* 输入链接到此数据库的帐户的口令。
* 指示数据库是否必须位于Unicode中。

   使用&#x200B;**[!UICONTROL Unicode database]**&#x200B;选项，可以在Unicode中存储所有字符类型，而不考虑语言。

   >[!NOTE]
   >
   >对于Oracle数据库，**[!UICONTROL Unicode storage]**&#x200B;选项允许您使用&#x200B;**NCLOB**&#x200B;和&#x200B;**NVARCHAR**&#x200B;类型字段。
   > 
   >如果不选择此选项，Oracle库的字符集（字符集）必须启用所有语言的存储（建议使用AL32UTF8）。

* 为数据库选择时区，并指定是否希望它以UTC（如果可用）显示。

   有关详细信息，请参阅[时区管理](../../installation/using/time-zone-management.md)。

### 步骤4 — 安装{#step-4---packages-to-install}的程序包

选择要安装的包。

请参阅您的许可协议以检查您有权安装哪些解决方案和选项，如“交互”或“社交营销”。

![](assets/s_ncs_install_modules.png)

### 步骤5 — 创建步骤{#step-5---creation-steps}

在&#x200B;**[!UICONTROL Creation steps]**&#x200B;窗口中，可以显示和编辑用于创建表的SQL脚本。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 对于Oracle、Microsoft SQL Server或PostgreSQL数据库，管理员还可以定义创建存储库对象时使用的&#x200B;**数据参数**。

   这些参数会接收确切的表空间名(警告：区分大小写)。 它们分别存储在&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;节点中的以下选项中（请参阅[此部分](../../installation/using/configuring-campaign-options.md#database)）：

   * **WdbcOptions_TableSpaceUser**:基于模式的用户表
   * **WdbcOptions_TableSpaceIndex**:根据模式
   * **WdbcOptions_TableSpaceWork**:无模式的工作表
   * **WdbcOptions_TableSpaceWorkIndex**:没有模式的工作表索引

* 对于Oracle库，Adobe Campaign用户必须有权访问Oracle库，通常作为&#x200B;**oinstall**&#x200B;组的成员。
* 通过&#x200B;**[!UICONTROL Set or change the administrator password]**&#x200B;选项，您可以输入链接到具有管理员权限的Adobe Campaign操作员的口令。

   为了安全起见，我们建议定义Adobe Campaign帐户管理员密码。

### 第6步 — 创建数据库{#step-6---creating-the-database}

在向导的最后阶段，您可以创建数据库。 单击&#x200B;**[!UICONTROL Start]**&#x200B;进行确认。

![](assets/s_ncs_install_db_oracle_creation06.png)

创建数据库后，您可以重新连接以完成实例配置。

您现在必须开始部署向导以完成实例的配置。 请参阅[部署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

链接到实例的Adobe Campaign库的连接设置存储在安装目录下的文件&#x200B;**`/conf/config-<instance>.xml`**&#x200B;中。

与“活动”帐户链接的base61数据库上的Microsoft SQL Server配置示例，其密码为加密密码：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 案例2:使用现有数据库{#case-2--using-an-existing-database}

数据库以及用户必须由数据库管理员创建，并且访问权限配置正确。

例如，对于Oracle数据库，最低要求的权限是：授予CONNECT、资源和无限表空间。

要使用现有数据库，配置步骤如下：

* [第1步 — 选择数据库引擎](#step-1---choosing-the-database-engine),
* [第2步 — 数据库连接设置](#step-2---database-connection-settings),
* [步骤3 — 要安装的包](#step-3---packages-to-install),
* [第4步 — 创建步骤](#step-4---creation-steps),
* [第5步 — 创建数据库](#step-5---creating-the-database)。

### 步骤1 — 选择数据库引擎{#step-1---choosing-the-database-engine}

从下拉列表中选择数据库引擎。

![](assets/s_ncs_install_db_select_engine.png)

确定服务器并选择要执行的操作类型。 在这种情况下，**[!UICONTROL Use an existing database]**。

![](assets/s_ncs_install_db_oracle_exists_01.png)

根据所选数据库引擎，服务器标识信息可能不同。

* 对于&#x200B;**Oracle**&#x200B;引擎，填充为应用程序服务器定义的&#x200B;**TNS名称**。
* 对于&#x200B;**PostgreSQL**&#x200B;或&#x200B;**DB2**&#x200B;引擎，必须指定应用程序服务器上定义的DNS名称（或IP地址）才能访问数据库服务器。
* 对于&#x200B;**Microsoft SQL Server**&#x200B;引擎，必须定义：

   1. 在应用程序服务器上定义的用于访问数据库服务器的DNS名称（或IP地址），
   1. 用于访问Microsoft SQL Server的安全方法：**[!UICONTROL SQL Server authentication]**&#x200B;或&#x200B;**[!UICONTROL Windows NT authentication]**。

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### 步骤2 — 数据库连接设置{#step-2---database-connection-settings}

在&#x200B;**[!UICONTROL Database]**&#x200B;窗口中，定义数据库连接设置。

![](assets/s_ncs_install_db_oracle_exists_02.png)

您需要定义以下设置：

* 输入要使用的数据库的名称，
* 输入与此数据库关联的帐户的名称和密码，

   >[!NOTE]
   >
   >确保模式名和用户名都匹配。 建议通过活动控制台客户端创建数据库。
   >对于Oracle数据库，无需输入帐户名。

* 指示数据库是否应为Unicode。

### 步骤3 — 安装{#step-3---packages-to-install}的程序包

选择要安装的包。

请参阅您的许可协议以检查您有权安装哪些解决方案和选项，如“交互”或“潜在客户”。

![](assets/s_ncs_install_modules.png)

### 步骤4 — 创建步骤{#step-4---creation-steps}

在&#x200B;**[!UICONTROL Creation steps]**&#x200B;窗口中，可以显示和编辑用于创建表的SQL脚本。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 对于Oracle、Microsoft SQL Server或PostgreSQL数据库，管理员可以定义创建存储库对象时使用的&#x200B;**数据参数**。
* 对于Oracle库，Adobe Campaign用户必须有权访问Oracle库，通常作为&#x200B;**oinstall**&#x200B;组的成员。
* 通过&#x200B;**[!UICONTROL Set or change the administrator password]**&#x200B;选项，您可以输入链接到具有管理员权限的Adobe Campaign操作员的口令。

   为了安全起见，我们建议定义Adobe Campaign帐户管理员密码。

### 第5步 — 创建数据库{#step-5---creating-the-database}

在向导的最后阶段，您可以创建数据库。 单击&#x200B;**[!UICONTROL Start]**&#x200B;进行确认。

![](assets/s_ncs_install_db_oracle_creation06.png)

数据库创建完成后，您可以重新连接以完成实例配置。

您现在必须开始部署向导以完成实例的配置。 请参阅[部署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

链接到实例的Adobe Campaign库的连接设置存储在安装目录下的文件&#x200B;**`/conf/config-<instance>.xml`**&#x200B;中。

与“活动”帐户链接的base61数据库上的Microsoft SQL Server配置示例，其密码为加密密码：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
