---
product: campaign
title: 命令行
description: 命令行
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
TQID: https://experienceleague.adobe.com/e85vFL0iZ586ICGGH1CP6fgqGU717W1aPDWqmj40-3s
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 4%

---

# 命令行{#command-lines}



以下命令行要求能够访问应用程序服务器。 对于由Adobe托管的部署，这些命令只能由Adobe执行。

## 创建实例 {#creating-an-instance}

实例创建可以使用命令行执行，语法为：

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

（其中&#x200B;**eng**&#x200B;和&#x200B;**fra**&#x200B;是`[lang]`参数的可能值）

命令&#x200B;**nlserver config -addinstance:instance1/demo&#42;/eng**&#x200B;允许您使用DNS掩码演示&#42;创建名为&#x200B;**instance1**&#x200B;的英文实例。

## 声明数据库 {#declaring-a-database}

可以使用以下语法将现有数据库与命令行中的实例相关联：

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

**`[rdbms]`**&#x200B;参数可能具有以下值：

* **postgresql**：对于PostgreSQL，
* **oracle**：对于Oracle，
* **mssql**：对于Microsoft SQL Server，

以下命令使用名为&#x200B;**base6**&#x200B;的SQL类型服务器配置&#x200B;**demo**&#x200B;实例，该服务器链接到&#x200B;**dbsrv**&#x200B;服务器上的&#x200B;**campaign**&#x200B;帐户及其&#x200B;**密码**：

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
