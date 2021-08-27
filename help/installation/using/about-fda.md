---
product: campaign
title: 访问外部数据库
description: 了解如何在外部数据库中访问和处理数据
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 联合数据访问入门 {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign提供了&#x200B;**联合数据访问**(FDA)选项，以便处理存储在一个或多个外部数据库中的信息：您无需更改Adobe Campaign数据的结构即可访问外部数据。

## 先决条件 {#operating-principle}

FDA选项允许您在第三方数据库中扩展数据模型。 它将自动检测目标表的结构并使用SQL源中的数据。

要使用此功能，下面列出了先决条件：

* **配置**:除了Snowflake之外，您需要 **内部** 或混 **** 合托管模型来设置联合数据访问。[了解详情](../../installation/using/hosting-models.md)
* **外部数据库版本**:您需要具有与Adobe Campaign FDA模块兼容的外部数据库。Campaign [兼容性矩阵](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中详细列出了数据库系统和兼容版本。
* **权限**:用户还必须在Adobe Campaign [和](../../installation/using/remote-database-access-rights.md) 外部数据库中拥有必要的权限。

