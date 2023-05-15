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



以下命令行需要能够访问应用程序服务器。 对于由Adobe托管的部署，这些命令只能由Adobe执行。

## 创建实例 {#creating-an-instance}

可以使用命令行使用语法执行实例创建：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(其中 **eng** 和 **fra** 是 `[lang]` parameter)

命令 **nlserver config -addinstance:instance1/demo&#42;/eng** 允许您创建一个名为 **instance1** 带DNS掩码演示的英文版&#42;.

## 声明数据库 {#declaring-a-database}

您可以使用以下语法从命令行将现有数据库与实例关联：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

对于 **`[rdbms]`** 参数：

* **postgresql**:对于PostgreSQL，
* **oracle**:对于Oracle,
* **msq**:对于Microsoft SQL Server，
* **DB2**:对于DB2引擎。

以下命令将配置 **演示** 具有SQL类型服务器(称为 **base6**，链接到 **营销活动** 帐户及其 **密码** 在 **dbsrv** 服务器：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
