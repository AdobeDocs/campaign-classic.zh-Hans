---
product: campaign
title: 联合数据访问入门
description: 了解如何在外部数据库中访问和处理数据
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# 联合数据访问入门 {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign提供 **联合数据访问** (FDA)选项，用于处理存储在一个或多个外部数据库中的信息：您无需更改Adobe Campaign数据的结构即可访问外部数据。

## 先决条件 {#operating-principle}

FDA选项允许您在第三方数据库中扩展数据模型。 它将自动检测目标表的结构并使用SQL源中的数据。

要使用此功能，下面列出了先决条件：

* **配置**:兼容外部数据库的列表，取决于 [托管模型](../../installation/using/hosting-models.md).
* **外部数据库版本**:您需要具有与Adobe Campaign FDA模块兼容的外部数据库。

   Campaign中详细列出了每个托管模型的数据库系统和兼容版本 [兼容性矩阵](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **权限**:用户还必须具有 [必要权限](../../installation/using/remote-database-access-rights.md) 在Adobe Campaign和外部数据库中。

