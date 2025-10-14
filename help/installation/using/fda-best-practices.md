---
product: campaign
title: Campaign FDA最佳实践和限制
description: 了解使用外部数据库(FDA)时的最佳实践和限制
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 1%

---

# 最佳实践和限制



## 使用外部数据优化电子邮件个性化 {#optimizing-email-personalization-with-external-data}

您可以在专用工作流中预处理消息个性化。 要执行此操作，请使用投放属性的&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;选项卡中提供的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项。

在投放分析期间，此选项会自动创建并执行一个工作流，该工作流会将链接到目标的所有数据（包括链接至外部数据库的表中的数据）存储在临时表中。

此选项可显着改进执行个性化步骤时的性能。

## 在工作流中使用来自外部数据库的数据 {#using-data-from-an-external-database-in-a-workflow}

在多个Adobe Campaign工作流活动中，您可以使用存储在外部数据库中的数据。

* **外部数据筛选** — 查询活动允许您添加外部数据，并在定义的筛选配置中使用它。 有关更多信息，请参阅[Campaign v8文档]https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}。

* **创建子集** — 拆分活动允许您创建子集。 您可以使用外部数据来定义要使用的筛选条件。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}。

* **加载外部数据库** — 您可以在数据加载(RDBMS)活动中使用外部数据。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-rdbms.html){target="_blank"}以了解详情。

* **添加信息和链接** — 扩充活动允许您向工作流的工作表添加其他数据，并链接到外部表。 在这种情况下，它可以使用来自外部数据库的数据。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}。

## 护栏和限制 {#fda-limitations}

FDA选项用于在工作流中以批处理模式处理外部数据库中的数据。 为了避免出现性能问题，建议不要在单一操作的上下文中使用FDA模块，例如：个性化、交互、实时消息传送等。

不支持定位一个数据库中的数据并使用属于另一个数据库的过滤维度过滤结果。 不能在一个查询中连接位于不同数据源上的表。 您可以使用其他工作流活动（如更改维度）来克服此限制。

尽可能避免需要同时使用Adobe Campaign和外部数据库的操作。 最佳实践是：

* 将Adobe Campaign数据库导出到外部数据库，并仅在将结果重新导入Adobe Campaign之前从外部数据库执行操作。

* 从外部Adobe Campaign数据库中收集数据，并在本地执行操作。

如果要使用外部数据库中的数据在投放中进行个性化，请收集要在工作流中使用的数据，以使其在临时表中可用。 然后，使用临时表中的数据将投放个性化。

FDA选项受您使用的外部数据库系统的限制。
