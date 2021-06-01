---
product: campaign
title: Campaign FDA最佳实践和限制
description: 了解使用外部数据库(FDA)时的最佳实践和限制
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 6%

---

# 最佳实践和限制

## 创建临时架构{#create-temporary-schemas}

您可以通过高FDA管理对Greenplum外部数据库的多次访问。 利用专用选项，可在配置外部帐户时直接创建工作模式。

![](assets/fda_work_table.png)

>[!NOTE]
>
>此选项仅在PostgreSQL Greenplum中可用。

## 使用外部数据{#optimizing-email-personalization-with-external-data}优化电子邮件个性化

您可以在专用工作流中预处理消息个性化。 要执行此操作，请使用投放属性的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡中提供的&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;选项。

在投放分析期间，此选项会自动创建并执行一个工作流，该工作流将链接到目标的所有数据存储在临时表中，包括来自外部数据库中链接的表的数据。

此选项可显着提高执行个性化步骤时的性能。

## 在工作流{#using-data-from-an-external-database-in-a-workflow}中使用来自外部数据库的数据

在多个Adobe Campaign工作流活动中，您可以使用存储在外部数据库中的数据。

* **对外部数据进行过滤**  — 通过查 [](../../workflow/using/targeting-data.md#selecting-data) 询活动，可添加外部数据并在定义的过滤器配置中使用。有关详细信息，请参见[此页面](../../workflow/using/targeting-data.md#selecting-data)。

* **创建子集**  — 利用拆分 [](../../workflow/using/split.md) 活动可创建子集。您可以使用外部数据定义要使用的筛选条件。 有关详细信息，请参见[此页面](../../workflow/using/split.md)。

* **加载外部数据库**  — 您可以在数据加载 [](../../workflow/using/data-loading--rdbms-.md) (RDBMS)活动中使用外部数据。请参阅[此页面](../../workflow/using/data-loading--rdbms-.md)以了解详情。

* **添加信息和链接**  — 使用 [](../../workflow/using/enrichment.md) Enrichmentactivity可向工作流的工作台添加其他数据，以及链接到外部表。在此上下文中，它可以使用外部数据库中的数据。 请参阅[此页面](../../workflow/using/enrichment.md)以了解详情。

## FDA限制 {#limitations}

FDA选项用于在工作流中以批处理模式处理外部数据库中的数据。 为避免出现性能问题，不建议在统一操作的背景下使用FDA模块，例如：个性化、互动、实时消息传送等。

尽量避免同时使用Adobe Campaign和外部数据库所需的操作。 为此，您可以：

* 将Adobe Campaign数据库导出到外部数据库，并仅在从外部数据库执行操作后再将结果重新导入Adobe Campaign。

* 从外部Adobe Campaign数据库收集数据并在本地执行操作。

如果要使用外部数据库中的数据在投放中进行个性化，请收集要在工作流中使用的数据，以在临时表格中提供。 然后，使用临时表格中的数据对投放进行个性化。

FDA选项受您使用的外部数据库系统的限制。
