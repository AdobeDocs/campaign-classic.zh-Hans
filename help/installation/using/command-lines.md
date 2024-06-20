---
product: campaign
title: 命令行
description: 命令行
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%

---

# 命令行{#command-lines}



以下命令行要求能够访问应用程序服务器。 对于由Adobe托管的部署，这些命令只能由Adobe执行。

## 创建实例 {#creating-an-instance}

实例创建可以使用命令行执行，语法为：

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(其中 **英文** 和 **周五** 的值是 `[lang]` parameter)

命令 **nlserver config -addinstance：instance1/demo&#42;/eng** 使您能够创建名为的实例 **实例1** 英文版的DNS掩码演示&#42;.

## 声明数据库 {#declaring-a-database}

可以使用以下语法将现有数据库与命令行中的实例相关联：

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

以下值可用于 **`[rdbms]`** 参数：

* **postgresql**：对于PostgreSQL，
* **oracle**：对于Oracle，
* **mssql**：对于Microsoft SQL Server，

以下命令配置 **演示** 具有SQL类型服务器的实例，称为 **基础6**，链接到 **营销活动** 帐户及其 **密码** 在 **dbsrv** 服务器：

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
