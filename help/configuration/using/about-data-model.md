---
solution: Campaign Classic
product: campaign
title: 开始使用Campaign Classic数据模型
description: 了解如何扩展 Campaign 数据模型、编辑模式、使用 API 等
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 6%

---


# Campaign 数据模型快速入门{#about-data-model}

Adobe Campaign 数据库的概念数据模型由一组内置表及它们之间的交互组成。本页中列出了主表和概念。

## 概述 {#data-model-overview}

Adobe Campaign依赖于包含链接在一起的表的关系数据库。 Adobe Campaign数据模型的基本结构可以描述如下。

### 收件人表{#recipient-table}

数据模型依赖于主表，该主表默认为收件人表(**NmsRecipient**)。 此表可用于存储所有营销用户档案。

有关收件人表的详细信息，请参阅[此部分](#default-recipient-table)。

### 投放表{#delivery-table}

数据模型还包括专用于存储所有营销活动的部件。 通常是投放表(**NmsDelivery**)。 此表中的每个记录都表示投放操作或投放模板。 它包含执行投放(如目标、内容等)所需的所有参数。

### 记录表{#log-tables}

数据模型的另一部分能够临时存储与执行活动相关的所有日志。

投放日志是所有渠道中发送给收件人或设备的所有消息。 主投放日志表(**NmsBroadLog**)包含所有收件人的投放日志。
主跟踪日志表(**NmsTrackingLog**)存储所有收件人的跟踪日志。 跟踪日志指收件人的反应，如电子邮件的开头和点击。 每个反应对应一个跟踪日志。
投放日志和跟踪日志将在某个时间段后删除，该时间段在Adobe Campaign中指定并可以修改。 因此，强烈建议定期出口日志。

### 技术表{#technical-tables}

最后，部分数据模型包含用于应用程序过程的技术数据，包括操作符和用户权限(**NmsGroup**)、文件夹(**XtkFolder**)。

## 使用默认收件人表{#default-recipient-table}

Adobe Campaign中开箱即用的收件人表为构建数据模型提供了良好的起点。 它包含许多可轻松扩展的预定义字段和表链接。 当您主要针对收件人时，此功能特别有用，因为它适合以收件人为中心的简单数据模型。

使用标准收件人表的好处如下：

* 利用订阅、种子列表、调查、社交等功能开箱即用。
* 为营销数据库提供以收件人为中心的数据模型。
* 更快的实施。
* 由支持和合作伙伴轻松维护。

但是，可以扩展收件人表，但不能减少表中字段或链接的数量。

>[!IMPORTANT]
>
>建议不要删除收件人表中的字段（即使这些字段无用），因为这可能会导致内置模块中出现错误。

此外，由于收件人表是产品的一部分，因此表及其关联表单都随着产品的变化而发展。 因此，需要额外的维护来检查任何扩展在升级时是否仍然有效。

## 扩展数据模型{#extending-data-model}

从Adobe Campaign开始，您需要评估默认数据模型以检查最适合存储营销数据的表。

如果相关，您可以将默认收件人表与现成字段一起使用，如[此部分](#default-recipient-table)中所述。

如果需要，您可以使用两种机制扩展它：

* 用新字段扩展现有表。 例如，您可以向收件人表添加新的“忠诚度”字段。
* 创建一个新表(例如，一个“购买”表列出数据库每个用户档案所购买的所有数据，并将其链接到收件人表。

有关配置扩展模式以扩展概念数据模型的详细信息，请参阅[关于模式版本](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>扩展数据模型是为高级用户保留的。

## 使用自定义收件人表{#custom-recipient-table}

在设计Adobe Campaign收件人模型时，您可以使用[现成收件人表](#default-recipient-table)，或决定创建[自定义表](../../configuration/using/about-custom-recipient-table.md)表来存储您的营销用户档案。

事实上，如果您的数据模型不符合以收件人为中心的结构，您可以将其他表设置为Adobe Campaign中的定位维度。 例如，当您需要目标家庭、帐户（如手机）和公司/站点，而不是简单的收件人时，这可能是相关的。

>[!NOTE]
>
>在这种情况下，您需要创建新的[目标映射](../../configuration/using/target-mapping.md)。

[本节](../../configuration/using/about-custom-recipient-table.md)详细介绍了使用自定义收件人表时需要的所有原则和步骤。

使用自定义收件人表的好处如下：

* **灵活的收件人**  — 现成的收件人表是无用的，如果您不需要大多数表字段，或者数据模型不是以收件人为中心。

* **可伸缩** 性 — 大卷需要一个精简的表格，其中只有少量字段，才能实现高效设计。现成的收件人表将包含太多无用字段，这可能影响性能并且缺乏效率。

* **数据位置**  — 如果数据驻留在外部现有的营销数据库上，则使用现成的收件人表可能需要过多的工作。基于现有结构创建新结构更简单。

* **轻松迁移**  — 无需维护即可检查所有扩展在升级后是否仍然有效。

>[!IMPORTANT]
>
>使用自定义收件人表是为高级用户保留的，并受到某些限制。 有关更多信息，请参阅[此章节](../../configuration/using/about-custom-recipient-table.md)。

## 相关主题

在以下部分中进一步了解活动数据模型：

* **主表的说明**  — 有关默认Campaign Classic数据模型说明的详细信息，请参 [阅本节](../../configuration/using/data-model-description.md)。

* **每个表的完整说明**  — 要访问每个表的完整说明，请转到 **[!UICONTROL Admin > Configuration > Data schemas]**，从列表中选择一个资源，然后单击选 **[!UICONTROL Documentation]** 项卡。

   ![](assets/data-model_documentation-tab.png)


* **活动** 模式 — 应用程序中所承载数据的物理和逻辑结构用XML进行描述。它遵循 Adobe Campaign 特有的语法，称为模式。有关Adobe Campaign模式的详细信息，请阅读[本节](../../configuration/using/about-schema-reference.md)。

* **数据模型最佳实践**  — 在本节中学习活动数据模型体系结构和相关的最 [佳实践](../../configuration/using/data-model-best-practices.md#data-model-architecture)。
