---
product: campaign
title: 配置FDA连接器
description: 了解FDA的配置步骤
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 6939307c0b33ff662fe4ef9ae0192ae7b500a95c
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 7%

---

# 配置 FDA 连接器 {#specific-configurations-by-database-type}



根据您希望能够从Adobe Campaign访问的外部数据库，您将需要执行某些特定配置。 这些配置实际上涉及在Adobe Campaign服务器上安装属于每个RDBMS的驱动程序和声明环境变量。

通常，您需要在Adobe Campaign服务器上的外部数据库上安装相应的客户端层。

>[!NOTE]
>
>中列出了兼容的版本 [Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
>

## 配置步骤 {#fda-configuration-steps}

要使用FDA设置对外部数据库的访问权限，配置步骤如下：

1. 安装驱动程序，并设置与Adobe Campaign服务器上的数据库对应的外部帐户。 请参阅特定于数据库的页面 [如下所列](#fda-specific-configuration)
1. 测试外部帐户或在Adobe Campaign与外部数据库之间创建临时连接。 [了解详情](../../installation/using/connecting-to-database.md)
1. 在Adobe Campaign中创建外部数据库的模式。 这允许您标识外部数据库的数据结构。 [了解详情](../../installation/using/creating-data-schema.md)
1. 如果需要，请从之前创建的模式创建新的目标映射。 如果投放的收件人来自外部数据库，则需要此字段。 此实施附带与消息个性化相关的限制。 [了解详情](../../installation/using/defining-data-mapping.md)

创建数据架构后，便可以在Adobe Campaign工作流中处理数据。 如需详细信息，请参阅[此小节](../../workflow/using/accessing-an-external-database--fda-.md)。

## 数据库特定配置 {#fda-specific-configuration}

根据您希望能够从Adobe Campaign访问的外部数据库，您将需要执行某些特定配置。 这些配置基本上涉及在Adobe Campaign服务器上安装属于每个RDBMS的驱动程序和声明环境变量，以及配置外部帐户。

请访问以下链接以了解更多信息：

* 连接Campaign和 [Amazon Redshift](../../installation/using/configure-fda-redshift.md)
* 连接Campaign和 [azure synapse](../../installation/using/configure-fda-synapse.md)
* 连接Campaign和 [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* 连接Campaign和 [hadoop](../../installation/using/configure-fda-hadoop.md)
* 连接Campaign和 [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* 连接Campaign和 [netezza](../../installation/using/configure-fda-netezza.md)
* 连接Campaign和 [oracle](../../installation/using/configure-fda-oracle.md)
* 连接Campaign和 [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* 连接Campaign和 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* 连接Campaign和 [Snowflake](../../installation/using/configure-fda-snowflake.md)
* 连接Campaign和 [sybase IQ](../../installation/using/configure-fda-sybase.md)
* 连接Campaign和 [teradata](../../installation/using/configure-fda-teradata.md)
* 连接Campaign和 [vertica analytics](../../installation/using/configure-fda-vertica.md)
