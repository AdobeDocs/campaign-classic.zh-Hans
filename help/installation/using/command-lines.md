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

## 创建实例{#creating-an-instance}

可以使用以下语法使用命令行执行实例创建：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

（其中&#x200B;**eng**&#x200B;和&#x200B;**fra**&#x200B;是`[lang]`参数的可能值）

使用命令&#x200B;**nlserver config -addinstance:instance1/demo*/eng**，您可以使用DNS掩码demo*创建一个名为&#x200B;**instance1**&#x200B;的英语实例。

## 声明数据库{#declaring-a-database}

您可以使用以下语法将现有数据库与命令行中的实例关联：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

**`[rdbms]`**&#x200B;参数可使用以下值：

* **postgresql**:对于PostgreSQL，
* **oracle**:对于Oracle,
* **mssql**:对于Microsoft SQL Server，
* **DB2**:DB2引擎。

以下命令使用SQL类型服务器（称为&#x200B;**base6**）配置&#x200B;**demo**&#x200B;实例，该服务器链接到&#x200B;**活动**&#x200B;帐户及其&#x200B;**密码**&#x200B;在&#x200B;**dbsrv**&#x200B;服务器上：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

