---
solution: Campaign Classic
product: campaign
title: 命令行
description: 命令行
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# 命令行{#command-lines}

以下命令行需要能够访问应用程序服务器。 对于由Adobe托管的部署，这些命令只能由Adobe执行。

## 创建实例 {#creating-an-instance}

可以使用命令行执行实例创建，语法为：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

( **eng** 和 **fra是参数** 的可能 `[lang]` 值)

使用命 **令nlserver config -addinstance:instance1/demo*/eng** ，您可以使用DNS掩码demo*创建一 **个名为instance** 1的英语实例。

## 声明数据库 {#declaring-a-database}

您可以使用以下语法从命令行将现有数据库与实例关联：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

参数可能有以下 **`[rdbms]`** 值：

* **postgresql**:对于PostgreSQL,
* **oracle**:oracle,
* **mssql**:对于Microsoft SQL Server,
* **DB2**:DB2引擎。

以下命令使用SQL **类型实例服务器** (称为 **base**)配置demo，该实例服务器链接到 **活动帐户** ，并 **在dbsrv6服务器上****** 使用密码：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

