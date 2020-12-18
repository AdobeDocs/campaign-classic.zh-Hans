---
solution: Campaign Classic
product: campaign
title: Campaign Classic库建议
description: 数据库建议
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---


# 数据库{#database}

只要数据库服务器之间有网络连接，它就可以在任何给定的操作系统上运行，而不管应用程序服务器或服务器使用的操作系统。

只要能够与Adobe Campaign的不同组件建立连接，数据库服务器的操作系统就不重要。

另请检查[数据库访问层](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers)部分。

## Microsoft SQL Server {#microsoft-sql-server}

本机客户端必须安装在Adobe Campaign应用程序服务器上。

可以通过ODBC驱动程序配置面板（位于&#x200B;**SQL Server Native Client 11.0**&#x200B;下）检查服务器上的本机客户端。

必须存在以下访问DLL:**sqlncli11.dll**。

访问DLL可在Microsoft网站上找到。

>[!NOTE]
>
>不支持从在Linux中运行的应用程序服务器访问Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支持具有多字节字符的列名称。

**NLS_NCHAR_CHARACTERSET**&#x200B;和&#x200B;**NLS_CHARACTERSET**&#x200B;参数需要正确配置，以使数据库能够在Unicode或ANSI中工作。

Adobe Campaign使用默认的Oracle编码。 使用其他编码可能会触发兼容性问题：在这种情况下，请与技术支持联系。

要了解您的编码，请使用以下&#x200B;**sqlplus**&#x200B;命令：

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

要登录&#x200B;**sqlplus**，请使用Oracle用户用户档案:

```
su - oracle 
sqlplus 
[login] [password]
```

您还可以引用Linux中的[Oracle客户端](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)。

## PostgresSQL {#postgressql}

我们建议您在安装数据库引擎时安装UTF-8支持。 这样，您将能够创建Unicode数据库。

**相关主题**

* [Adobe Campaign Classic表中未登录的选项](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
