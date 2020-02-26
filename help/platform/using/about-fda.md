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
source-git-commit: 47fd157e369ddf6c67f0b2b467799cecc6e5a822

---


# 关于联合数据访问 {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>通过FDA访问外部数据库仅可用于内部或混合安装，雪花连接器除外。 For more on this, refer to this [page](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## 工作原理 {#operating-principle}

FDA选项允许您在第三方数据库中扩展您的数据模型。 它将自动检测目标表的结构并使用SQL源中的数据。


要使用此功能，您必须：

1. 拥有一个与Adobe Campaign FDA模块兼容的外部数据库。 兼容性矩阵中详细列出了数据库系统和兼容 [版本](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。 用户还必须在Adobe Campaign [中](../../platform/using/remote-database-access-rights.md) ，以及外部数据库上具有必要的权限。
1. [在Adobe Campaign服务器上](../../platform/using/specific-configuration-database.md) ，安装与您的数据库相对应的驱动程序。
1. [创建和配置一个外部帐户](../../platform/using/connecting-to-database.md) ，该帐户允许您在Adobe Campaign和外部数据库之间建立连接。 有关可用外部帐户的详细信息，请参阅此 [页](../../platform/using/external-accounts.md)。
1. [在Adobe Campaign中创建外部数据库的架构](../../platform/using/creating-data-schema.md) 。 这允许您识别外部数据库的数据结构。
1. 最终， [从先前创建的架构创建新的目标映射](../../platform/using/defining-data-mapping.md) ，如果您的分发的收件人来自外部数据库，则此映射为新目标映射。 这就存在某些限制，特别是在个性化交付方面。

创建数据架构后，即可在Adobe Campaign工作流程中处理数据。 如需详细信息，请参阅[此部分](../../workflow/using/executing-a-workflow.md#architecture)。

## 最佳实践和建议 {#best-practices-and-recommendations}

FDA选项用于在工作流中以批处理模式处理外部数据库中的数据。 在另一个环境中使用FDA，例如，对于单一业务，必须采取预防措施（个性化、交互、实时交付等）。

避免需要尽可能使用Adobe Campaign和外部数据库的操作。 为此，您可以：

* 将Adobe Campaign数据库导出到外部数据库，并仅在将结果重新导入Adobe Campaign之前从外部数据库执行操作。
* 从外部Adobe Campaign数据库收集数据并在本地执行操作。

如果您希望使用外部数据库中的数据在提交中实现个性化，请收集要在工作流中使用的数据，以便在临时表中提供。 然后使用临时表中的数据个性化您的交付。

## 限制 {#limitations}

FDA选项对您使用的外部数据库系统具有软限制。

出于性能原因，我们不建议使用此功能来执行统一操作（交付个性化、交互模块、实时）。
