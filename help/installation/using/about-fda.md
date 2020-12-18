---
solution: Campaign Classic
product: campaign
title: 访问外部数据库
description: 了解如何访问和处理外部数据库中的数据
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 4%

---


# 联合数据访问{#about-federated-data-access}入门

Adobe Campaign提供&#x200B;**联合数据访问**(联合数据访问)选项，以便处理存储在一个或多个外部数据库中的信息：您可以访问外部数据，而无需更改Adobe Campaign数据的结构。

## 先决条件{#operating-principle}

联合数据访问选项允许您在第三方数据库中扩展数据模型。 它将自动检测目标表的结构并使用SQL源中的数据。

要使用此功能，入门项目如下所示：

* **配置**:除Snowflake外，您需要一 **个** 本地 **** 或混合托管模型来设置联合数据访问[了解详情](../../installation/using/hosting-models.md)
* **外部数据库版本**:您需要有一个与Adobe Campaign联合数据访问模块兼容的外部数据库。活动[兼容性矩阵](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中详细介绍了列表库系统和兼容版本。
* **权限**:用户还必须具有 [Adobe Campaign](../../installation/using/remote-database-access-rights.md) 和外部数据库的必要权限。

## 限制{#limitations}

联合数据访问选项用于以工作流的批处理模式处理外部数据库中的数据。 为避免性能问题，不建议在单一操作环境中使用联合数据访问模块，例如：个性化、交互、实时消息等。

避免需要尽可能同时使用Adobe Campaign和外部数据库的操作。 为此，您可以：

* 将Adobe Campaign库导出到外部数据库，并在将结果重新导入Adobe Campaign之前仅从外部数据库执行操作。

* 从外部Adobe Campaign库收集数据并在本地执行操作。

如果您希望使用外部投放库的数据在中进行个性化，请收集要在工作流中使用的数据，以便在临时表中提供。 然后使用临时表中的数据个性化您的投放。

联合数据访问选项受您使用的外部数据库系统的限制。

## 建议{#recommendations}

### 创建临时模式{#create-temporary-schemas}

您可以通过高联合数据访问管理对Greenplum外部数据库的多次访问。 专用选项可让您在配置模式时直接创建工作外部帐户。

![](assets/fda_work_table.png)

>[!NOTE]
>
>此选项仅对PostgreSQL Greenplum可用。

### 使用外部数据{#optimizing-email-personalization-with-external-data}优化电子邮件个性化

您可以在专用工作流中预处理消息个性化。 要执行此操作，请使用投放属性&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;选项。

在投放分析期间，此选项自动创建并执行一个工作流，该工作流将链接到目标的所有数据存储在临时表中，包括来自外部数据库中链接的表的数据。

此选项在执行个性化步骤时显着改进性能。

### 在工作流{#using-data-from-an-external-database-in-a-workflow}中使用外部数据库中的数据

在多个Adobe Campaign工作流活动中，您可以使用存储在外部数据库中的数据。

* **对外部数据进行筛选** -“查 [](../../workflow/using/targeting-data.md#selecting-data) 询活动”允许您添加外部数据，并在定义的筛选器配置中使用它。有关详细信息，请参见[此页面](../../workflow/using/targeting-data.md#selecting-data)。

* **创建子集** -“拆 [](../../workflow/using/split.md) 分”活动允许您创建子集。您可以使用外部数据来定义要使用的筛选条件。 有关详细信息，请参见[此页面](../../workflow/using/split.md)。

* **加载外部数据** -您可以在数据加载(RDBMS)活动 [中使用](../../workflow/using/data-loading--rdbms-.md) 外部数据。请阅读[本页](../../workflow/using/data-loading--rdbms-.md)了解更多信息。

* **添加信息和链接** -通过 [](../../workflow/using/enrichment.md) Enrichmentactivity，您可以向工作流的工作台添加其他数据，并链接到外部表。在此上下文中，它可以使用外部数据库中的数据。 请阅读[本页](../../workflow/using/enrichment.md)了解更多信息。
