---
product: campaign
title: Campaign Classic数据库建议
description: 数据库建议
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 数据库{#database}

数据库服务器可以在任何给定的操作系统上运行，而不管应用程序服务器或服务器使用的操作系统是什么，只要它们之间有网络连接。

只要与Adobe Campaign的不同组件有连接，数据库服务器的操作系统就不重要。

另请检查[数据库访问层](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers)部分。

## Microsoft SQL Server {#microsoft-sql-server}

本机客户端必须安装在Adobe Campaign应用程序服务器上。

可以通过&#x200B;**SQL Server本机客户端11.0**&#x200B;下的ODBC驱动程序配置面板检查服务器上的本机客户端。

必须存在以下访问DLL:**sqlncli11.dll**。

访问DLL可在Microsoft网站上找到。

>[!NOTE]
>
>不支持从在Linux中运行的应用程序服务器访问Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支持具有多字节字符的列名称。

需要正确配置&#x200B;**NLS_NCHAR_CHARACTERSET**&#x200B;和&#x200B;**NLS_CHARACTERSET**&#x200B;参数，以使数据库以Unicode或ANSI格式工作。

Adobe Campaign使用默认Oracle编码。 使用其他编码可能会触发兼容性问题：在这种情况下，请联系技术支持。

要了解编码信息，请使用以下&#x200B;**sqlplus**&#x200B;命令：

```
SELECT * FROM nls_database_parameters ;
```

* 对于Unicode安装，支持的编码包括：

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* 对于ANSI安装（非unicode），仅支持以下编码：

```
  NLS_CHARACTERSET WE8MSWIN1252
```

要登录到&#x200B;**sqlplus**，请使用Oracle用户配置文件：

```
su - oracle 
sqlplus 
[login] [password]
```

您还可以在Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)中引用[Oracle客户端。

## PostgresSQL {#postgressql}

我们建议您在安装数据库引擎时安装UTF-8支持。 这样，您就能够创建Unicode数据库。

**相关主题**

* [Adobe Campaign Classic表中的未记录选项](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
