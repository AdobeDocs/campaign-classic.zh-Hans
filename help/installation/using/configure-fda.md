---
product: campaign
title: 配置FDA连接器
description: 了解FDA配置步骤
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 5%

---

# 配置 FDA 连接器 {#specific-configurations-by-database-type}

![](../../assets/v7-only.svg)

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及在Adobe Campaign服务器上安装驱动程序并声明属于每个RDBMS的环境变量。

通常，您需要在Adobe Campaign服务器上的外部数据库上安装相应的客户端层。

>[!NOTE]
>
>兼容版本列在 [Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

## 配置步骤 {#fda-configuration-steps}

要使用FDA设置对外部数据库的访问，配置步骤如下：

1. 安装驱动程序并设置与Adobe Campaign服务器上的数据库对应的外部帐户。 请参阅特定于数据库的页 [下面列出](#fda-specific-configuration)
1. 测试外部帐户或在Adobe Campaign与外部数据库之间创建临时连接。 [了解详情](../../installation/using/connecting-to-database.md)
1. 在Adobe Campaign中创建外部数据库的模式。 这允许您标识外部数据库的数据结构。 [了解详情](../../installation/using/creating-data-schema.md)
1. 如果需要，从之前创建的架构创建新的目标映射。 如果投放的收件人来自外部数据库，则需要此参数。 此实施具有与消息个性化相关的限制。 [了解详情](../../installation/using/defining-data-mapping.md)

创建数据架构后，即可在Adobe Campaign工作流中处理数据。 如需详细信息，请参阅[此部分](../../workflow/using/accessing-an-external-database--fda-.md)。

## 数据库特定配置 {#fda-specific-configuration}

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及在Adobe Campaign服务器上安装驱动程序并声明属于每个RDBMS的环境变量，以及配置外部帐户。

请访问以下链接以了解更多信息：

* 连接Campaign和 [韦尔蒂察](../../installation/using/configure-fda-vertica.md)

* 连接Campaign和 [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)

* 连接Campaign和 [azure synapse](../../installation/using/configure-fda-synapse.md)

* 连接Campaign和 [Snowflake](../../installation/using/configure-fda-snowflake.md)

* 连接Campaign和 [Hadoop](../../installation/using/configure-fda-hadoop.md)

* 连接Campaign和 [Oracle](../../installation/using/configure-fda-oracle.md)

* 连接Campaign和 [Netezza](../../installation/using/configure-fda-netezza.md)

* 连接Campaign和 [sybase IQ](../../installation/using/configure-fda-sybase.md)

* 连接Campaign和 [Teradata](../../installation/using/configure-fda-teradata.md)

* 连接Campaign和 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

* 连接Campaign和 [PostgreSQL](../../installation/using/configure-fda-postgresql.md)

* 连接Campaign和 [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)

* 连接Campaign和 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

