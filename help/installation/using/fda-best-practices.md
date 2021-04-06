---
solution: Campaign Classic
product: campaign
title: 活动 联合数据访问最佳做法和限制
description: 了解使用外部数据库时的最佳实践和限制(联合数据访问)
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 0a92ebd6c9400f8caf43da8f633c7755a3fb77ce
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 4%

---


# 最佳实践和限制

## 创建临时模式{#create-temporary-schemas}

可以通过高联合数据访问管理对Greenplum外部数据库的多次访问。 专用选项可让您在配置模式时直接创建工作外部帐户。

![](assets/fda_work_table.png)

>[!NOTE]
>
>此选项仅对PostgreSQL Greenplum可用。

## 使用外部数据{#optimizing-email-personalization-with-external-data}优化电子邮件个性化

您可以在专用工作流中预处理消息个性化。 要执行此操作，请使用&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;选项，该选项位于投放属性的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡中。

在投放分析期间，此选项自动创建并执行一个工作流，该工作流将链接到目标的所有数据存储在临时表中，包括来自外部数据库中链接的表的数据。

此选项可显着提高执行个性化步骤时的性能。

## 在工作流{#using-data-from-an-external-database-in-a-workflow}中使用外部数据库中的数据

在多个Adobe Campaign工作流活动中，您可以使用存储在外部数据库中的数据。

* **对外部数据进行筛选**  — “查 [](../../workflow/using/targeting-data.md#selecting-data) 询活动”允许您添加外部数据并在定义的筛选器配置中使用它。有关详细信息，请参见[此页面](../../workflow/using/targeting-data.md#selecting-data)。

* **创建子集**  — “拆 [](../../workflow/using/split.md) 分”活动允许您创建子集。您可以使用外部数据来定义要使用的筛选条件。 有关详细信息，请参见[此页面](../../workflow/using/split.md)。

* **加载外部数据**  — 您可以在数据加载(RDBMS)活动 [中使用](../../workflow/using/data-loading--rdbms-.md) 外部数据。请阅读[本页](../../workflow/using/data-loading--rdbms-.md)了解更多信息。

* **添加信息和链接** - Enrichment [](../../workflow/using/enrichment.md) 活动允许您向工作流的工作表添加其他数据，并链接到外部表。在此上下文中，它可以使用外部数据库中的数据。 请阅读[本页](../../workflow/using/enrichment.md)了解更多信息。

## 联合数据访问限制{#limitations}

使用联合数据访问选项，以批处理模式在工作流中处理外部数据库中的数据。 为避免性能问题，不建议在统一操作的上下文中使用联合数据访问模块，例如：个性化、交互、实时消息等。

避免需要尽可能使用Adobe Campaign和外部数据库的操作。 为此，您可以：

* 将Adobe Campaign数据库导出到外部数据库，并在将结果重新导入Adobe Campaign之前仅从外部数据库执行操作。

* 从外部Adobe Campaign数据库收集数据并在本地执行操作。

如果您希望使用外部投放库中的数据在您的应用程序中进行个性化，请收集要在工作流中使用的数据，以便在临时表中提供。 然后使用临时表中的数据个性化您的投放。

“联合数据访问”选项受您使用的外部数据库系统的限制。

