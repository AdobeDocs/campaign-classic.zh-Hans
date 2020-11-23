---
solution: Campaign Classic
product: campaign
title: 创建和配置数据库
description: 创建和配置数据库
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 1%

---


# 创建和配置数据库{#creating-and-configuring-the-database}

在创建Adobe Campaign库时，该数据库提供两个不同的选项：

1. 创建或循环使用数据库：如果要创建新数据库或重复使用现有数据库，请选择此选项。 请参阅 [案例1:创建／循环使用数据库](#case-1--creating-recycling-a-database)。
1. 使用现有数据库：如果管理员已创建空数据库并且您希望使用它，则选择此选项；或扩展现有数据库的结构。 请参 [阅案例2:使用现有数据库](#case-2--using-an-existing-database)。

下文详细介绍了配置步骤。

>[!CAUTION]
>
>模式库、用户和开始的名称不得以数字或包含特殊字符。
>
>只有内部 **标识符** 才能执行这些操作。 For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

## 案例1:创建／循环使用数据库 {#case-1--creating-recycling-a-database}

创建数据库或循环使用现有库的步骤如下所示。 某些配置取决于所使用的数据库引擎：

涉及以下步骤：

* [第1步——选择数据库引擎](#step-1---selecting-the-database-engine),
* [第2步——连接到服务器](#step-2---connecting-to-the-server),
* [第3步——数据库的连接和特性](#step-3---connection-and-characteristics-of-the-database),
* [第4步——安装软件包](#step-4---packages-to-install),
* [第5步——创建步骤](#step-5---creation-steps),
* [第6步——创建数据库](#step-6---creating-the-database)。

### 第1步——选择数据库引擎 {#step-1---selecting-the-database-engine}

在下拉列表中选择数据库引擎。

![](assets/s_ncs_install_db_select_engine.png)

支持的活动库列在 [兼容性矩阵中](../../rn/using/compatibility-matrix.md)。

识别服务器并选择要执行的操作类型。 在这个例子中， **[!UICONTROL Create or recycle a database]**。

![](assets/s_ncs_install_db_oracle_creation01.png)

服务器标识信息可能因所选数据库引擎而异。

* 对于 **Oracle** ，填充为应 **用程序服** 务器定义的TNS名称。
* 对于 **PostgreSQL** 或 **DB2引擎** ，必须指定在应用程序服务器上定义的DNS名称（或IP地址）才能访问数据库服务器。
* 对于 **Microsoft SQL Server** Engine，必须定义：应用程序服务器上定义的用于访问数据库服务器的DNS名称（或IP地址）: **DNS** 或 **DNS`\<instance>`** （实例模式）,

   >[!CAUTION]
   >
   > 从20.3开始，Windows NT身份验证将停止使用。 **[!UICONTROL SQL Server authentication]** 现在是Microsoft SQL Server唯一可用的身份验证模式。 [阅读更多](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### 第2步——连接到服务器 {#step-2---connecting-to-the-server}

在窗口 **[!UICONTROL Server access]** 中，定义数据库服务器访问权限。

![](assets/s_ncs_install_db_oracle_creation02.png)

为此，请输入具有访问数据库 **权限的** “管理”系统帐户的名称和密码，即：

* **oracle** 数据库系统，
* **sa** 对于Microsoft SQL Server数据库，
* **postgre** SQL数据库的postgres,
* **db2inst1** ，用于DB2数据库。

### 第3步——数据库的连接和特性 {#step-3---connection-and-characteristics-of-the-database}

通过以下步骤，可配置登录数据库的设置。

![](assets/s_ncs_install_db_oracle_creation03.png)

您需要定义以下设置：

* 指定要创建的数据库的名称。

   >[!NOTE]
   >
   >对于DB2数据库，数据库名称不得超过8个字符。

* 输入链接到此数据库的帐户的口令。
* 指示数据库是否必须位于Unicode中。

   该选 **[!UICONTROL Unicode database]** 项允许您以Unicode存储所有字符类型，而不考虑语言。

   >[!NOTE]
   >
   >对于Oracle数据库， **[!UICONTROL Unicode storage]** 该选项允许 **您使用** NCLOB **和** NVARCHAR类型字段。
   > 
   >如果不选择此选项，则Oracle数据库的字符集（字符集）必须启用所有语言的数据存储（建议使用AL32UTF8）。

* 为数据库选择时区，并指定是否希望它以UTC（如果可用）显示。

   有关此方面的详细信息，请参 [阅时区管理](../../installation/using/time-zone-management.md)。

### 第4步——要安装的包 {#step-4---packages-to-install}

选择要安装的包。

请参阅您的许可协议以检查您有权安装哪些解决方案和选项，如“交互”或“社交营销”。

![](assets/s_ncs_install_modules.png)

### 第5步——创建步骤 {#step-5---creation-steps}

该 **[!UICONTROL Creation steps]** 窗口允许您显示和编辑用于创建表的SQL脚本。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 对于Oracle、Microsoft SQL Server或PostgreSQL数据库，管理员还可以定义创建数据 **库对象时** 要使用的存储参数。

   这些参数接收确切的表空间名称(警告：区分大小写)。 它们分别存储在以 **[!UICONTROL Administration > Platform > Options]** 下选项的节点中(请参 [阅本节](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**:基于模式的用户表
   * **WdbcOptions_TableSpaceIndex**:根据模式
   * **WdbcOptions_TableSpaceWork**:无模式的工作表
   * **WdbcOptions_TableSpaceWorkIndex**:无模式的工作表索引

* 对于OracleAdobe Campaign库，用户必须具有访问Oracle库的权限，通常作为安装组的 **成员** 。
* 通过 **[!UICONTROL Set or change the administrator password]** 此选项，您可以输入与具有管理员权限的Adobe Campaign操作员链接的口令。

   我们建议为安全目的定义Adobe Campaign帐户管理员密码。

### 第6步——创建数据库 {#step-6---creating-the-database}

在向导的最后一个阶段，您可以创建数据库。 Click **[!UICONTROL Start]** to confirm.

![](assets/s_ncs_install_db_oracle_creation06.png)

创建数据库后，您可以重新连接以完成实例配置。

您现在必须开始部署向导以完成实例的配置。 请参阅 [部署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

链接到实例的Adobe Campaign库的连接设置存储在安装目 **`/conf/config-<instance>.xml`** 录下的文件中。

与“活动”帐户链接且其加密密码的base61数据库上的Microsoft SQL Server配置示例：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 案例2:使用现有数据库 {#case-2--using-an-existing-database}

数据库以及用户必须由数据库管理员创建，并且访问权限配置正确。

例如，对于Oracle数据库，最低要求权限为：授予CONNECT、资源和无限表空间。

要使用现有数据库，配置步骤如下：

* [第1步——选择数据库引擎](#step-1---choosing-the-database-engine),
* [第2步——数据库连接设置](#step-2---database-connection-settings),
* [第3步——安装软件包](#step-3---packages-to-install),
* [第4步——创建步骤](#step-4---creation-steps),
* [第5步——创建数据库](#step-5---creating-the-database)。

### 第1步——选择数据库引擎 {#step-1---choosing-the-database-engine}

从下拉列表中选择数据库引擎。

![](assets/s_ncs_install_db_select_engine.png)

识别服务器并选择要执行的操作类型。 在这个例子中， **[!UICONTROL Use an existing database]**。

![](assets/s_ncs_install_db_oracle_exists_01.png)

服务器标识信息可能因所选数据库引擎而异。

* 对于 **Oracle** ，填充为应 **用程序服** 务器定义的TNS名称。
* 对于 **PostgreSQL** 或 **DB2引擎** ，必须指定在应用程序服务器上定义的DNS名称（或IP地址）才能访问数据库服务器。
* 对于 **Microsoft SQL Server** Engine，必须定义：

   1. 应用程序服务器上定义的用于访问数据库服务器的DNS名称（或IP地址）,
   1. 用于访问Microsoft SQL Server的安全方法： **[!UICONTROL SQL Server authentication]** 或 **[!UICONTROL Windows NT authentication]**&#x200B;者

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### 第2步——数据库连接设置 {#step-2---database-connection-settings}

在窗口 **[!UICONTROL Database]** 中，定义数据库连接设置。

![](assets/s_ncs_install_db_oracle_exists_02.png)

您需要定义以下设置：

* 输入要使用的数据库的名称，
* 输入与此数据库关联的帐户的名称和口令，

   >[!NOTE]
   >
   >确保模式名和用户名都匹配。 建议通过活动控制台客户端创建数据库。
   >对于Oracle数据库，无需输入帐户名称。

* 指示数据库是否应为Unicode。

### 步骤3 —— 要安装的包 {#step-3---packages-to-install}

选择要安装的包。

请参阅您的许可协议以检查您有权安装哪些解决方案和选项，如“交互”或“潜在客户”。

![](assets/s_ncs_install_modules.png)

### 第4步——创建步骤 {#step-4---creation-steps}

该 **[!UICONTROL Creation steps]** 窗口允许您显示和编辑用于创建表的SQL脚本。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 对于Oracle、Microsoft SQL Server或PostgreSQL数据库，管理员可以定义创建数据 **库对象时** 要使用的存储参数。
* 对于OracleAdobe Campaign库，用户必须具有访问Oracle库的权限，通常作为安装组的 **成员** 。
* 通过 **[!UICONTROL Set or change the administrator password]** 此选项，您可以输入与具有管理员权限的Adobe Campaign操作员链接的口令。

   我们建议为安全目的定义Adobe Campaign帐户管理员密码。

### 第5步——创建数据库 {#step-5---creating-the-database}

在向导的最后一个阶段，您可以创建数据库。 Click **[!UICONTROL Start]** to confirm.

![](assets/s_ncs_install_db_oracle_creation06.png)

数据库创建完成后，您可以重新连接以完成实例配置。

您现在必须开始部署向导以完成实例的配置。 请参阅 [部署向导](../../installation/using/deploying-an-instance.md#deployment-wizard)。

链接到实例的Adobe Campaign库的连接设置存储在安装目 **`/conf/config-<instance>.xml`** 录下的文件中。

与“活动”帐户链接且其加密密码的base61数据库上的Microsoft SQL Server配置示例：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

