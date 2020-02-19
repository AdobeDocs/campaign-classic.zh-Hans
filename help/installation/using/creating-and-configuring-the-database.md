---
title: 创建和配置数据库
seo-title: 创建和配置数据库
description: 创建和配置数据库
seo-description: null
page-status-flag: never-activated
uuid: e5143d55-61fa-416a-80db-c29a0caf9a3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 7dd8a6a5-7cca-4e92-8226-1b9e450dfaf9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# 创建和配置数据库{#creating-and-configuring-the-database}

在创建数据库时，Adobe Campaign提供两个不同的选项：

1. 创建或循环使用数据库：如果要创建新数据库或重复使用现有数据库，请选择此选项。 请参阅 [案例1:创建／循环使用数据库](#case-1--creating-recycling-a-database)。
1. 使用现有数据库：如果管理员已创建空数据库并且您希望使用该数据库，请选择此选项；或扩展现有数据库的结构。 请参阅 [案例2:使用现有数据库](#case-2--using-an-existing-database)。

下面详细介绍了配置步骤。

>[!CAUTION]
>
>数据库、用户和架构的名称不能以数字开头或包含特殊字符。
>
>只有内部 **标识符** 才能执行这些操作。 For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

## 案例1:创建／循环使用数据库 {#case-1--creating-recycling-a-database}

下面介绍了创建数据库或循环使用现有库的步骤。 某些配置取决于所使用的数据库引擎：

涉及以下步骤：

* [第1步——选择数据库引擎](#step-1---selecting-the-database-engine),
* [第2步——连接到服务器](#step-2---connecting-to-the-server),
* [第3步——数据库连接和数据库特性](#step-3---connection-and-characteristics-of-the-database),
* [第4步——安装包](#step-4---packages-to-install),
* [第5步——创建步骤](#step-5---creation-steps),
* [第6步——创建数据库](#step-6---creating-the-database)。

### 第1步——选择数据库引擎 {#step-1---selecting-the-database-engine}

从下拉列表中选择数据库引擎。

![](assets/s_ncs_install_db_select_engine.png)

支持的数据库在兼容性矩阵一节 [中介绍](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

识别服务器并选择要执行的操作类型。 在这个例子中， **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

根据所选数据库引擎，服务器标识信息可能不同。

* 对于 **Oracle** engine，填充为应用程序服 **务器定义的TNS名称** 。
* 对于 **PostgreSQL** 或 **** DB2引擎，必须指定应用程序服务器上定义的DNS名称（或IP地址）才能访问数据库服务器。
* 对于 **Microsoft SQL Server** ，必须定义：

   1. 应用程序服务器上定义的用于访问数据库服务器的DNS名称（或IP地址）: **DNS** 或 **DNS\ `<instance>`**（实例模式）,
   1. 用于访问Microsoft SQL server的身份验证方法：或 **[!UICONTROL SQL Server authentication]** 者 **[!UICONTROL Windows NT authentication]**。

      ![](assets/s_ncs_install_db_mssql_creation01.png)

### 第2步——连接到服务器 {#step-2---connecting-to-the-server}

在窗口 **[!UICONTROL Server access]** 中，定义数据库服务器访问权限。

![](assets/s_ncs_install_db_oracle_creation02.png)

为此，请输入具有访问数据库权限的 **Administration系统帐户的名称** 和密码，例如：

* **系统** ，用于Oracle数据库，
* **sa** for a microsoft SQL Server database,
* **postgre** SQL数据库的后缀，
* **db2inst1** ，用于DB2数据库。

### 第3步——数据库连接和数据库特性 {#step-3---connection-and-characteristics-of-the-database}

通过以下步骤，您可以配置登录数据库的设置。

![](assets/s_ncs_install_db_oracle_creation03.png)

您需要定义以下设置：

* 指定要创建的数据库的名称。

   >[!NOTE]
   >
   >对于DB2数据库，数据库名称不能超过8个字符。

* 输入链接到此数据库的帐户的口令。
* 指示数据库是否必须位于Unicode中。

   通过 **[!UICONTROL Unicode database]** 此选项，您可以在Unicode中存储所有字符类型，而不管使用哪种语言。

   >[!NOTE]
   >
   >对于Oracle数据库，该选 **[!UICONTROL Unicode storage]** 项允许您使用 **NCLOB** 和 **NVARCHAR类型字段** 。
   > 
   >如果不选择此选项，则Oracle数据库的字符集（字符集）必须启用所有语言的数据存储（建议使用AL32UTF8）。

* 为数据库选择时区，并指定是否希望它以UTC（如果有）格式显示。

   有关详细信息，请参阅时 [区管理](../../installation/using/time-zone-management.md)。

### 第4步——安装包 {#step-4---packages-to-install}

选择要安装的包。

请参阅您的许可协议以检查您有权安装哪些解决方案和选项，如“交互”或“社交营销”。

![](assets/s_ncs_install_modules.png)

### 第5步——创建步骤 {#step-5---creation-steps}

窗口 **[!UICONTROL Creation steps]** 允许您显示和编辑用于创建表的SQL脚本。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 对于Oracle、Microsoft SQL server或PostgreSQL数据库，管理员还可以定义创建数据库对 **象时要使用的存储参数** 。

   这些参数会收到确切的表空间名称(警告：区分大小写)。 它们分别存储在节 **[!UICONTROL Administration > Platform > Options]** 点中的以下选项中：

   * **WdbcOptions_TableSpaceUser**:基于架构的用户表
   * **WdbcOptions_TableSpaceIndex**:基于架构的用户表索引
   * **WdbcOptions_TableSpaceWork**:无架构的工作表
   * **WdbcOptions_TableSpaceWorkIndex**:无架构的工作表索引

* 对于Oracle数据库，Adobe Campaign用户必须具有对Oracle库的访问权限，通常作为安装组的成员 **访问** 。
* 通过 **[!UICONTROL Set or change the administrator password]** 此选项，您可以输入与Adobe Campaign操作员链接的具有管理员权限的密码。

   为安全起见，我们建议定义Adobe Campaign帐户管理员密码。

### 第6步——创建数据库 {#step-6---creating-the-database}

在向导的最后一个阶段，您可以创建数据库。 Click **[!UICONTROL Start]** to confirm.

![](assets/s_ncs_install_db_oracle_creation06.png)

创建数据库后，您可以重新连接以完成实例配置。

您现在必须启动部署向导才能完成实例的配置。 请参阅部 [署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

链接到实例的数据库的连接设置存储在Adobe Campaign安 **`/conf/config-<instance>.xml`** 装目录中的文件中。

与“campaign”帐户关联的base61数据库上的Microsoft SQL server配置示例及其加密密码：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 案例2:使用现有数据库 {#case-2--using-an-existing-database}

数据库以及用户必须由数据库管理员创建，并且访问权限配置正确。

例如，对于Oracle数据库，最低要求的权限是：授予CONNECT、资源和无限表空间。

要使用现有数据库，配置步骤如下：

* [第1步——选择数据库引擎](#step-1---choosing-the-database-engine),
* [第2步——数据库连接设置](#step-2---database-connection-settings),
* [第3步——安装包](#step-3---packages-to-install),
* [第4步——创建步骤](#step-4---creation-steps),
* [第5步——创建数据库](#step-5---creating-the-database)。

### 第1步——选择数据库引擎 {#step-1---choosing-the-database-engine}

从下拉列表中选择数据库引擎。

![](assets/s_ncs_install_db_select_engine.png)

识别服务器并选择要执行的操作类型。 在这个例子中， **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

根据所选数据库引擎，服务器标识信息可能不同。

* 对于 **Oracle** engine，填充为应用程序服 **务器定义的TNS名称** 。
* 对于 **PostgreSQL** 或 **** DB2引擎，必须指定应用程序服务器上定义的DNS名称（或IP地址）才能访问数据库服务器。
* 对于 **Microsoft SQL Server** ，必须定义：

   1. 应用程序服务器上定义的用于访问数据库服务器的DNS名称（或IP地址）,
   1. 用于访问Microsoft SQL server的安全方法：或 **[!UICONTROL SQL Server authentication]** 者 **[!UICONTROL Windows NT authentication]**。

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### 第2步——数据库连接设置 {#step-2---database-connection-settings}

在窗口 **[!UICONTROL Database]** 中，定义数据库连接设置。

![](assets/s_ncs_install_db_oracle_exists_02.png)

您需要定义以下设置：

* 输入要使用的数据库的名称，
* 输入与此数据库关联的帐户的名称和口令，

   >[!NOTE]
   >
   >对于Oracle数据库，您无需输入帐户名。

* 指示数据库是否应为Unicode。

### 第3步——安装包 {#step-3---packages-to-install}

选择要安装的包。

请参阅您的许可协议以检查您有权安装哪些解决方案和选项，如“交互”或“潜在客户”。

![](assets/s_ncs_install_modules.png)

### 第4步——创建步骤 {#step-4---creation-steps}

窗口 **[!UICONTROL Creation steps]** 允许您显示和编辑用于创建表的SQL脚本。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 对于Oracle、Microsoft SQL server或PostgreSQL数据库，管理员可以定义创建数据库对象 **时要使用的存储参数** 。
* 对于Oracle数据库，Adobe Campaign用户必须具有对Oracle库的访问权限，通常作为安装组的成员 **访问** 。
* 通过 **[!UICONTROL Set or change the administrator password]** 此选项，您可以输入与Adobe Campaign操作员链接的具有管理员权限的密码。

   为安全起见，我们建议定义Adobe Campaign帐户管理员密码。

### 第5步——创建数据库 {#step-5---creating-the-database}

在向导的最后一个阶段，您可以创建数据库。 Click **[!UICONTROL Start]** to confirm.

![](assets/s_ncs_install_db_oracle_creation06.png)

数据库创建完成后，您可以重新连接以完成实例配置。

您现在必须启动部署向导才能完成实例的配置。 请参阅部 [署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

链接到实例的数据库的连接设置存储在Adobe Campaign安 **`/conf/config-<instance>.xml`** 装目录中的文件中。

与“campaign”帐户关联的base61数据库上的Microsoft SQL server配置示例及其加密密码：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

