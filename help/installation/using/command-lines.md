---
title: 命令行
seo-title: 命令行
description: 命令行
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 命令行{#command-lines}

以下命令行需要访问应用程序服务器的能力。 对于Adobe托管的部署，这些命令只能由Adobe执行。

## 创建实例 {#creating-an-instance}

可以使用命令行使用以下语法执行实例创建：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

( **where** eng **and** fra `[lang]` be possible values for the parameter)

使用 **命令nlserver config -addinstance:instance1/demo*/eng** ，您可以使用DNS掩码demo*创建一个名为instance1 **** 的英语实例。

## 声明数据库 {#declaring-a-database}

可以使用以下语法从命令行将现有数据库与实例关联：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

参数可能有以下 **`[rdbms]`** 值：

* **postgresql**:对于PostgreSQL,
* **oracle**:对于Oracle,
* **mssql**:对于Microsoft SQL Server,
* **DB2**:对于DB2引擎。

以下命令使用SQL实例 **服务器** (称为 **base6**)配置demo **，该服务器链接到营销活动帐户及其password password在dbsrv服务器********** 上的campaign帐户：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

