---
product: campaign
title: Campaign FDA最佳实践和限制
description: 了解使用外部数据库(FDA)时的最佳实践和限制
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 7%

---

# 最佳实践和限制



## 使用外部数据优化电子邮件个性化 {#optimizing-email-personalization-with-external-data}

您可以在专用工作流中预处理消息个性化。 要执行此操作，请使用 **[!UICONTROL Prepare the personalization data with a workflow]** 选项，可在 **[!UICONTROL Analysis]** 投放属性的选项卡。

在投放分析期间，此选项会自动创建并执行一个工作流，该工作流会将链接到目标的所有数据（包括链接至外部数据库的表中的数据）存储在临时表中。

此选项可显着改进执行个性化步骤时的性能。

## 在工作流中使用来自外部数据库的数据 {#using-data-from-an-external-database-in-a-workflow}

在多个Adobe Campaign工作流活动中，您可以使用存储在外部数据库中的数据。

* **筛选外部数据** - [查询](../../workflow/using/targeting-data.md#selecting-data) 利用活动，可添加外部数据并将其用于定义的过滤器配置。 有关详细信息，请参见[此页面](../../workflow/using/targeting-data.md#selecting-data)。

* **创建子集** - [Split](../../workflow/using/split.md) 利用活动，可创建子集。 您可以使用外部数据来定义要使用的筛选条件。 有关详细信息，请参见[此页面](../../workflow/using/split.md)。

* **加载外部数据库**  — 您可以使用中的外部数据 [正在加载数据](../../workflow/using/data-loading--rdbms-.md) (RDBMS)活动。 请参阅[此页面](../../workflow/using/data-loading--rdbms-.md)以了解详情。

* **添加信息和链接** - [扩充](../../workflow/using/enrichment.md) 利用活动，可向工作流的工作表添加其他数据，以及指向外部表的链接。 在这种情况下，它可以使用来自外部数据库的数据。 请参阅[此页面](../../workflow/using/enrichment.md)以了解详情。

## FDA限制 {#limitations}

FDA选项可用于在工作流中以批处理模式处理外部数据库中的数据。 为了避免出现性能问题，建议不要在单一操作的上下文中使用FDA模块，例如：个性化、交互、实时消息传送等。

尽可能避免需要同时使用Adobe Campaign和外部数据库的操作。 为此，您可以：

* 将Adobe Campaign数据库导出到外部数据库，并仅在将结果重新导入Adobe Campaign之前从外部数据库执行操作。

* 从外部Adobe Campaign数据库中收集数据，并在本地执行操作。

如果要使用外部数据库中的数据在投放中进行个性化，请收集要在工作流中使用的数据，以使其在临时表中可用。 然后，使用临时表中的数据将投放个性化。

FDA选项受您使用的外部数据库系统的限制。
