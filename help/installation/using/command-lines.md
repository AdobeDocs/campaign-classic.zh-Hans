---
product: campaign
title: 命令行
description: 命令行
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# 命令行{#command-lines}



以下命令行要求能够访问应用程序服务器。 对于由Adobe托管的部署，这些命令只能由Adobe执行。

## 创建实例 {#creating-an-instance}

实例创建可以使用命令行执行，语法为：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(其中 **英文** 和 **fra** 是以下各项的可能值： `[lang]` parameter)

命令 **nlserver config -addinstance：instance1/demo&#42;/eng** 使您能够创建一个名为的实例 **instance1** 英语版的DNS掩码演示&#42;.

## 声明数据库 {#declaring-a-database}

可以使用以下语法，从命令行将现有数据库与实例相关联：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

以下值可用于 **`[rdbms]`** 参数：

* **postgresql**：对于PostgreSQL，
* **oracle**：对于Oracle，
* **mssql**：对于Microsoft SQL Server，
* **DB2**：对于DB2引擎。

以下命令配置 **演示** 具有称为的SQL类型服务器的实例 **基础6**，链接到 **营销活动** 帐户及其 **密码** 在 **dbsrv** 服务器：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
