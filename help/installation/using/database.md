---
title: Campaign Classic库建议
description: 数据库建议
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---


# 数据库{#database}

只要数据库服务器之间有网络连接，它就可以在任何给定的操作系统上运行，而不管应用程序服务器或服务器使用的操作系统。

只要能够与Adobe Campaign的不同组件建立连接，数据库服务器的操作系统就不重要。

另请检查“数 [据库访问层](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) ”部分。

## Microsoft SQL Server {#microsoft-sql-server}

本机客户端必须安装在Adobe Campaign应用程序服务器上。

可以通过ODBC驱动程序配置面板在SQL Server Native Client 11.0下检查 **服务器上的本机客户端**。

必须存在以下访问DLL: **sqlncli11.dll**。

访问DLL可在Microsoft网站上找到。

>[!NOTE]
>
>不支持从在Linux中运行的应用程序服务器访问Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支持具有多字节字符的列名称。

需 **要正确配置NLS_NCHAR** _ **** CHARACTERSET和NLS_CHARACTERSET参数，以使数据库在Unicode或ANSI中工作。

Adobe Campaign使用默认的Oracle编码。 使用其他编码可能会触发兼容性问题：在这种情况下，请与技术支持联系。

要了解您的编码，请使用以下 **sqlplus命** 令：

```
SELECT * FROM nls_database_parameters ;
```

* 对于Unicode安装，支持的编码为：

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* 对于ANSI安装（非Unicode），仅支持以下编码：

```
  NLS_CHARACTERSET WE8MSWIN1252
```

要登录到 **sqlplus**，请使用Oracle用户用户档案:

```
su - oracle 
sqlplus 
[login] [password]
```

您还可以在Linux [中引用Oracle Client](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)。

## PostgresSQL {#postgressql}

我们建议您在安装数据库引擎时安装UTF-8支持。 这样，您将能够创建Unicode数据库。

**相关主题**

* [Adobe Campaign Classic表中未登录的选项](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
