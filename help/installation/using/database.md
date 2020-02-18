---
title: 数据库
seo-title: 数据库
description: 数据库
seo-description: null
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c25e2a4f2280cdcc61e0522f8235149410b5dacf

---


# 数据库{#database}

只要数据库服务器之间有网络连接，该数据库服务器就可以在任何给定操作系统上运行，而不管应用程序服务器或服务器使用的操作系统。

只要可以与Adobe Campaign的不同组件建立连接，数据库服务器的操作系统就不重要。

另请检查“数 [据库访问层](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) ”部分。

## Microsoft SQL Server {#microsoft-sql-server}

本机客户端必须安装在Adobe Campaign应用程序服务器上。

可以通过ODBC驱动程序配置面板检查服务器上的本机客户端，位于 **SQL Server Native Client 10.0** （对于Microsoft SQL Server 2008和2008 R2客户端）或 **SQL Server Native Client 11.0** （对于Microsoft SQL Server 20）下客户端)。

必须存在以下访问DLL:

* **sqlncli10.dll** for Microsoft SQL Server 2008和2008 R2客户端，
* **sqlncli11.dll** for Microsoft SQL Server 2012、2014、2016和2017客户端。

   访问DLL可在Microsoft网站上找到。

>[!NOTE]
>
>不支持从Linux中运行的应用程序服务器访问Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支持具有多字节字符的列名称。

需要 **正确配置NLS_NCHAR_CHARACTERSET** 和 **NLS_CHARACTERSET** 参数，以使数据库在Unicode或ANSI中工作。

Adobe Campaign使用默认的Oracle编码。 使用其他编码可能会触发兼容性问题：在这种情况下，请联系技术支持。

要了解您的编码，请使用以下 **sqlplus命令** :

```
SELECT * FROM nls_database_parameters ;
```

* 对于Unicode安装，支持的编码包括：

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* 对于ANSI安装（非Unicode），只支持以下编码：

```
  NLS_CHARACTERSET WE8MSWIN1252
```

要登录到 **sqlplus**，请使用Oracle用户配置文件：

```
su - oracle 
sqlplus 
[login] [password]
```

您还可以在Linux中 [引用Oracle Client](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)。

## PostgresSQL {#postgressql}

我们建议您在安装数据库引擎时安装UTF-8支持。 这样，您将能够创建Unicode数据库。

**相关主题**

* [Adobe Campaign Classic表格中的取消登录选项](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)