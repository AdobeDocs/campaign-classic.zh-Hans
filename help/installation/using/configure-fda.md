---
title: 配置联合数据访问连接器
description: 了解联合数据访问的配置步骤
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 3d6515ca291715e5e02f9b5404803e9087555284
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---


# 配置 FDA 连接器 {#specific-configurations-by-database-type}

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及安装驱动程序并声明属于环境服务器上每个RDBMS的Adobe Campaign变量。

通常，您需要在Adobe Campaign服务器上的外部数据库上安装相应的客户端层。

>[!NOTE]
>
>兼容版本列在 [活动兼容性表中](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)。


## 配置步骤 {#fda-configuration-steps}

要使用联合数据访问设置对外部数据库的访问，配置步骤包括：

1. 在Adobe Campaign服务器上安装与数据库对应的驱动程序。 驱动程序列在以下列出的数据库特定 [页面中](#fda-specific-configuration)。
1. [创建并配置外部帐户](../../installation/using/connecting-to-database.md) ，它允许您在Adobe Campaign和外部数据库之间建立连接。 有关活动中外部帐户的详细信息，请参 [阅本页](../../installation/using/external-accounts.md)。
1. [以模式](../../installation/using/creating-data-schema.md) ，创建外部数据库的Adobe Campaign。 这允许您识别外部数据库的数据结构。
1. 如果需要， [从先前创建的目标映射](../../installation/using/defining-data-mapping.md) 创建新模式。 如果收件人的投放来自外部数据库，则这是必需的。 此实施具有与消息个性化相关的限制。

创建模式后，可以在Adobe Campaign工作流中处理数据。 如需详细信息，请参阅[此部分](../../workflow/using/accessing-an-external-database--fda-.md)。

## 数据库特定配置 {#fda-specific-configuration}

根据您希望能够从Adobe Campaign访问的外部数据库，您需要执行特定配置。 这些配置实质上涉及安装驱动程序并声明属于环境服务器上每个RDBMS的Adobe Campaign变量。

请访问以下链接了解更多信息：

* [Azure突触](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [内泰扎](../../installation/using/configure-fda-netezza.md)

* [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
