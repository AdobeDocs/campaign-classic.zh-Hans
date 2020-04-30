---
title: 访问外部数据库
seo-title: 访问外部数据库
description: 访问外部数据库
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9d22af2a2e25cb0dd83759096139996372f60c33

---


# 关于联合数据访问 {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>通过联合数据访问访问外部数据库仅可用于内部安装或混合安装，雪花连接器除外。 For more on this, refer to this [page](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## 工作原理 {#operating-principle}

联合数据访问选项允许您在第三方数据库中扩展数据模型。 它将自动检测目标表的结构并使用SQL源中的数据。

要使用此功能，您必须：

1. 具有与Adobe Campaign联合数据访问模块兼容的外部数据库。 兼容性矩阵详细介绍了数据库系统和兼容版本 [的列表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。 用户还必须在Adobe Campaign [中和在外部数据库](../../platform/using/remote-database-access-rights.md) 上拥有必要的权限。
1. [在Adobe Campaign服务器上安装](../../platform/using/specific-configuration-database.md) ，与您的数据库相对应的驱动程序。
1. [创建和配置外部帐户](../../platform/using/connecting-to-database.md) ，该Adobe Campaign允许您在与外部数据库之间建立连接。 有关可用外部帐户的详细信息，请参阅此 [页](../../platform/using/external-accounts.md)。
1. [创建外部数据库的模式](../../platform/using/creating-data-schema.md) (在Adobe Campaign中)。 这允许您识别外部数据库的数据结构。
1. 最终， [从先前创建的目标映射](../../platform/using/defining-data-mapping.md) (如果投放的收件人来自外部数据库)创建新的模式。 这提出了一些限制，特别是在个性化投放方面。

创建数据模式后，可以在Adobe Campaign工作流中处理数据。 如需详细信息，请参阅[此部分](../../workflow/using/accessing-an-external-database--fda-.md)。

## 最佳实践和建议 {#best-practices-and-recommendations}

联合数据访问选项用于在工作流中以批处理模式处理外部数据库中的数据。 在另一个环境中使用联合数据访问，例如，对于统一操作，必须谨慎地执行(个性化、交互、实时投放等)。

避免需要尽可能使用Adobe Campaign和外部数据库的操作。 为此，您可以：

* 将Adobe Campaign数据库导出到外部数据库，并在将结果重新导入Adobe Campaign之前仅从外部数据库执行操作。
* 从外部Adobe Campaign数据库收集数据并在本地执行操作。

如果您希望使用外部数据库中的数据在投放中进行个性化，请收集要在工作流中使用的数据，以便在临时表中提供。 然后使用临时表中的数据个性化您的投放。

## 限制 {#limitations}

联合数据访问选项在您使用的外部数据库系统中受到软限制。

出于性能原因，我们不建议使用此功能来执行统一操作(投放个性化、交互模块、实时)。
