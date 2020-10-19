---
title: 访问外部数据库
description: 了解如何访问和处理外部数据库中的数据
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 15%

---


# 关于联合数据访问 {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>通过联合数据访问访问外部Snowflake库只能用于内部安装或混合安装，但连接器除外。 有关详细信息，请参见此 [ 页面](https://helpx.adobe.com/cn/campaign/kb/acc-on-prem-vs-hosted.html)。

## 工作原理 {#operating-principle}

联合数据访问选项允许您在第三方数据库中扩展数据模型。 它将自动检测目标表的结构并使用SQL源中的数据。

要使用此功能，您必须：

1. 具有与Adobe Campaign联合数据访问模块兼容的外部数据库。 兼容性矩阵中详细介绍了列表库系统和兼容 [版本的](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)。 用户在Adobe Campaign和 [外部](../../platform/using/remote-database-access-rights.md) ，也必须具有必要的权限。
1. [在Adobe Campaign服务器上](../../platform/using/specific-configuration-database.md) ，安装与您的数据库对应的驱动程序。
1. [创建并配置外部帐户](../../platform/using/connecting-to-database.md) ，它允许您在Adobe Campaign和外部数据库之间建立连接。 有关可用外部帐户的详细信息，请参阅 [本页](../../platform/using/external-accounts.md)。
1. [以模式](../../platform/using/creating-data-schema.md) ，创建外部数据库的Adobe Campaign。 这允许您识别外部数据库的数据结构。
1. 最终， [从先前创建的目标映射](../../platform/using/defining-data-mapping.md) (如果投放的收件人来自外部模式)创建新的。 这提出了一些限制，特别是在个性化投放方面。

创建模式后，可以在Adobe Campaign工作流中处理数据。 如需详细信息，请参阅[此部分](../../workflow/using/accessing-an-external-database--fda-.md)。

## 可用的外部数据库 {#external-database}

您可以在与Adobe Campaign列表模块兼容的每个外部数据库的联合数据访问下找到：

* Microsoft Azure突触分析。 有关更多信息，请参阅此](../../platform/using/specific-configuration-database.md#azure-external)章节[。
* Snowflake。 有关更多信息，请参阅此](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)章节[。
* Hadoop。 有关更多信息，请参阅此](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)章节[。
* 甲骨文。 有关更多信息，请参阅此](../../platform/using/specific-configuration-database.md#configure-access-to-oracle)章节[。
* 内泰扎。 有关更多信息，请参阅此](../../platform/using/specific-configuration-database.md#configure-access-to-netezza)章节[。
* Sybase IQ。 有关更多信息，请参阅此](../../platform/using/specific-configuration-database.md#configure-access-to-sybase-iq)章节[。
* Teradata。 有关更多信息，请参阅此](../../platform/using/specific-configuration-database.md#configure-access-to-teradata)章节[。
* SAP HANA。 有关更多信息，请参阅此](../../platform/using/specific-configuration-database.md)章节[。

## 最佳实践和建议 {#best-practices-and-recommendations}

联合数据访问选项用于以工作流的批处理模式处理外部数据库中的数据。 在另一个环境中使用联合数据访问，例如，对于统一操作，必须谨慎(个性化、交互、实时投放等)。

避免需要尽可能同时使用Adobe Campaign和外部数据库的操作。 为此，您可以：

* 将Adobe Campaign库导出到外部数据库，并在将结果重新导入Adobe Campaign之前仅从外部数据库执行操作。
* 从外部Adobe Campaign库收集数据并在本地执行操作。

如果您希望使用外部投放库的数据在中进行个性化，请收集要在工作流中使用的数据，以便在临时表中提供。 然后使用临时表中的数据个性化您的投放。

## 限制{#limitations}

联合数据访问选项在您使用的外部数据库系统中受到软限制。

出于性能原因，我们不建议使用此功能来执行统一操作(投放个性化、交互模块、实时)。
