---
solution: Campaign Classic
product: campaign
title: 配置联合数据访问连接器
description: 了解有关联合数据访问的配置步骤
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
translation-type: tm+mt
source-git-commit: 7ce5a01b57092043b8d9b52761b243f771cf74f2
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 5%

---

# 配置 FDA 连接器 {#specific-configurations-by-database-type}

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及安装驱动程序并声明属于Adobe Campaign服务器上每个RDBMS的环境变量。

通常，您需要在Adobe Campaign服务器上的外部数据库上安装相应的客户端层。

>[!NOTE]
>
>兼容版本列在[活动兼容性矩阵](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中。


## 配置步骤 {#fda-configuration-steps}

要使用联合数据访问设置对外部数据库的访问，配置步骤如下：

1. 安装驱动程序并设置与Adobe Campaign服务器上的数据库对应的外部帐户。 请参阅下面列出的特定于数据库的页面[](#fda-specific-configuration)
1. 测试外部帐户或在Adobe Campaign与外部数据库之间创建临时连接。 [了解详情](../../installation/using/connecting-to-database.md)
1. 在Adobe Campaign中创建外部数据库的模式。 这允许您标识外部数据库的数据结构。 [了解详情](../../installation/using/creating-data-schema.md)
1. 如果需要，从之前创建的目标映射创建新模式。 如果投放的收件人来自外部数据库，则这是必需的。 此实施存在与消息个性化相关的限制。 [了解详情](../../installation/using/defining-data-mapping.md)

创建模式后，可以在Adobe Campaign工作流中处理数据。 如需详细信息，请参阅[此部分](../../workflow/using/accessing-an-external-database--fda-.md)。

## 数据库特定配置{#fda-specific-configuration}

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及在Adobe Campaign服务器上安装驱动程序并声明属于每个RDBMS的环境变量，以及配置外部帐户。

请访问以下链接了解更多信息：

* 连接活动和[Azure synapse](../../installation/using/configure-fda-synapse.md)

* 连接活动和[Snowflake](../../installation/using/configure-fda-snowflake.md)

* 连接活动和[Hadoop](../../installation/using/configure-fda-hadoop.md)

* 连接活动和[Oracle](../../installation/using/configure-fda-oracle.md)

* 连接活动和[Netezza](../../installation/using/configure-fda-netezza.md)

* 连接活动和[Sybase IQ](../../installation/using/configure-fda-sybase.md)

* 连接活动和[Teradata](../../installation/using/configure-fda-teradata.md)

* 连接活动和[SAP HANA](../../installation/using/configure-fda-sap-hana.md)
