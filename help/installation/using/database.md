---
product: campaign
title: Campaign Classic数据库建议
description: 数据库建议
feature: Installation, Instance Settings
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 2%

---

# 数据库{#database}



数据库服务器可以在任何给定的操作系统上运行，而不管应用程序服务器使用的操作系统是什么，只要它们之间有网络连接。

只要可以与Adobe Campaign的不同组件建立连接，数据库服务器的操作系统就并不重要。

另外请查看 [数据库访问层](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) 部分。

## Microsoft SQL 服务器 {#microsoft-sql-server}

必须在Adobe Campaign应用程序服务器上安装本机客户端。

您可以通过ODBC驱动程序配置面板（位于下）检查服务器上的本机客户端 **SQL Server Native Client 11.0**.

必须存在以下访问DLL： **sqlncli11.dll**.

访问DLL可在Microsoft网站上找到。

>[!NOTE]
>
>不支持从在Linux中运行的应用程序服务器访问Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支持具有多字节字符的列名。

此 **NLS_NCHAR_CHARACTERSET** 和 **NLS_CHARACTERSET** 为了使数据库在Unicode或ANSI中工作，需要正确配置参数。

Adobe Campaign使用默认的Oracle编码。 使用其他编码可能会触发兼容性问题：在这种情况下，请联系技术支持。

要了解您的编码，请使用以下内容 **sqlplus** 命令：

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

登录 **sqlplus**，使用Oracle用户配置文件：

```
su - oracle 
sqlplus 
[login] [password]
```

您还可以参阅 [Linux中的Oracle客户端](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

建议您在安装数据库引擎时安装UTF-8支持。 这样，您将能够创建Unicode数据库。

**相关主题**

* [Adobe Campaign Classic表格中的Unlogged选项](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
