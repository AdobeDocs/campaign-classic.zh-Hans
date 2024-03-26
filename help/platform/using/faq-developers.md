---
product: campaign
title: 开发人员常见问题解答
description: 开发人员常见问题解答
feature: Troubleshooting, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 92%

---

# 开发人员常见问题解答 {#dev-faq}



作为一个开放式解决方案，Adobe Campaign 可进行自定义，并进行高级应用程序开发。

## 什么是Campaign数据模型？ {#what-is-the-campaign-data-model}

Adobe Campaign 数据库的概念数据模型由一组内置表及它们之间的交互组成。应用中所承载数据的物理和逻辑结构以 XML 格式进行描述。它遵循 Adobe Campaign 特有的语法，称为模式。有关 Adobe Campaign 模式的详细信息，[请参阅本部分](../../configuration/using/about-schema-edition.md)。

[单击此处了解有关 Campaign 数据模型的更多信息](https://helpx.adobe.com/cn/campaign/kb/acc-datamodel.html)。

[本文列出了](../../configuration/using/data-model-best-practices.md)最佳实践。

## 如何使用 Campaign 模式？ {#how-to-work-with-campaign-schemas-}

在 Adobe Campaign 中，数据模式用于：

* 定义应用程序内的数据对象如何与底层数据库表的联系起来。
* 定义 Campaign 应用程序中不同数据对象之间的链接。
* 定义并描述每个对象中包含的个别字段。

阅读[表和模式入门](../../configuration/using/about-schema-edition.md)，了解如何使用数据模式、扩展和自定义 Campaign 来满足您的需求。

## 如何使用自定义收件人表？ {#how-to-use-a-custom-recipient-table-}

您可以在Campaign中创建并实施非内置的收件人表，以发送消息。

[单击此处了解更多信息](../../configuration/using/about-custom-recipient-table.md)

## 在 Campaign 中定义查询的最佳实践是什么？ {#what-are-the-best-practices-to-define-queries-in-campaign-}

Adobe Campaign 查询编辑器是一款功能强大的工具，可用于探索数据和创建分段。

您可在软件的多个级别上找到 Adobe Campaign 查询工具：创建目标群体、细分客户、提取和过滤跟踪日志、构建过滤器等。

您可以使用通用查询编辑器查询 Campaign 数据库。可通过 **Tools > Generic query editor...** 菜单访问查询编辑器。它可让您提取数据库中存储的信息，将其整理、分组、排序等。例如，用户可以找到在给定的期间内，在新闻稿的链接上点击超过 n 次的收件人。通过这个工具，您可根据自己的需求收集、排序和显示结果。此工具结合了 Adobe Campaign 所有可能的查询方式。例如，您可以创建和保存限制过滤器。这意味着在定位工作流等的 Query 框中可以使用在通用查询编辑器中创建的用户过滤器。

使用所选表的字段或使用公式可以创建查询。[此页面](../../platform/using/about-queries-in-campaign.md)介绍了在 Campaign 数据库上创建查询的主要原则。

[单击此处](../../workflow/using/query.md) ，了解 Campaign 查询编辑器。

## 如何导入数据包？ {#how-can-i-import-a-data-package-}

使用 Adobe Campaign，您可以通过数据包系统导出或导入平台配置和数据。数据包支持以 XML 格式文件的形式显示 Adobe Campaign 数据库的实体。数据包中包含的每个实体由其全部数据表示。

数据包的原理是导出数据配置，并将它集成到另一个 Adobe Campaign 系统中。

[单击此处](../../platform/using/working-with-data-packages.md)了解如何使用数据包导入和导出 Campaign 配置。

## 在哪里可以找到Campaign ClassicAPI的列表？ {#where-can-i-find-the-list-of-campaign-classic-apis}

所有 Campaign API（包括其完整说明）均在此[专用文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans)中提供。
