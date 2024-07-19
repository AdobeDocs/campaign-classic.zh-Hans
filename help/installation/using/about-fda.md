---
product: campaign
title: 联合数据访问入门
description: 了解如何访问和处理外部数据库中的数据
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# 联合数据访问入门 {#about-federated-data-access}



Adobe Campaign提供了&#x200B;**联合数据访问** (FDA)选项，以便处理存储在一个或多个外部数据库中的信息：无需更改Adobe Campaign数据的结构即可访问外部数据。

## 先决条件 {#operating-principle}

FDA选项允许您在第三方数据库中扩展数据模型。 它将自动检测目标表的结构，并使用来自SQL源的数据。

为了使用此功能，下面列出了先决条件：

* **配置**：兼容的外部数据库列表取决于您的[托管模型](../../installation/using/hosting-models.md)。
* **外部数据库版本**：您需要具有与Adobe Campaign FDA模块兼容的外部数据库。

  Campaign [兼容性矩阵](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中详细列出了每个托管模型的数据库系统和兼容版本的列表。

* **权限**：用户还必须在Adobe Campaign和外部数据库中具有[必要的权限](../../installation/using/remote-database-access-rights.md)。

