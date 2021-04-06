---
solution: Campaign Classic
product: campaign
title: 访问外部数据库
description: 了解如何访问和处理外部数据库中的数据
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 联合数据访问 {#about-federated-data-access}入门

Adobe Campaign提供&#x200B;**联合数据访问**(联合数据访问)选项，以便处理存储在一个或多个外部数据库中的信息：您可以访问外部数据，而无需更改Adobe Campaign数据的结构。

## 先决条件{#operating-principle}

联合数据访问选项允许您在第三方数据库中扩展数据模型。 它将自动检测目标表的结构并使用SQL源中的数据。

要使用此功能，以下列出了先决条件：

* **配置**:除了Snowflake，您需要 **一个** 前提 **** 或混合托管模型来设置联合数据访问[了解详情](../../installation/using/hosting-models.md)
* **外部数据库版本**:您需要有一个与Adobe Campaign联合数据访问模块兼容的外部数据库。活动[兼容性矩阵](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中详细介绍了数据库系统和兼容版本的列表。
* **权限**:用户还必须具有 [Adobe Campaign](../../installation/using/remote-database-access-rights.md) 和外部数据库的必要权限。

