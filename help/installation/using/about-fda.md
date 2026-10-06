---
product: campaign
title: 联合数据访问入门
description: 了解如何访问和处理外部数据库中的数据
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
TQID: 'https://experienceleague.adobe.com/X-VyiKlGatskoXtPoLYhb8HrAgCRLLHxTbwXDFmg8jI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '164'
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

