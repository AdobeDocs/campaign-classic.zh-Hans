---
product: campaign
title: Campaign Classic数据模型快速入门
description: 了解如何扩展 Campaign 数据模型、编辑模式、使用 API 等
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# Campaign 数据模型快速入门{#about-data-model}

![](../../assets/v7-only.svg)

Adobe Campaign 数据库的概念数据模型由一组内置表及它们之间的交互组成。本页列出了主表和概念。

## 概述 {#data-model-overview}

Adobe Campaign依赖于包含已链接在一起的表的关系数据库。 Adobe Campaign数据模型的基本结构可描述如下。

### 收件人表 {#recipient-table}

数据模型依赖于主表，该主表默认为收件人表(**NmsRecipient**)。 此表用于存储所有营销用户档案。

有关收件人表的更多信息，请参阅[此部分](#default-recipient-table)。

### 投放表 {#delivery-table}

数据模型还包括专用于存储所有营销活动的部分。 通常为投放表(**NmsDelivery**)。 此表中的每个记录都表示投放操作或投放模板。 它包含执行投放所需的所有参数，如目标、内容等。

### 日志表 {#log-tables}

数据模型的另一个部分允许临时存储与执行营销活动相关的所有日志。

投放日志是所有渠道中发送给收件人或设备的所有消息。 主投放日志表(**NmsBroadLog**)包含所有收件人的投放日志。
主跟踪日志表(**NmsTrackingLog**)存储所有收件人的跟踪日志。 跟踪日志是指收件人的反应，如电子邮件的打开次数和点击次数。 每个反应都对应一个跟踪日志。
投放日志和跟踪日志将在特定时间段后删除(在Adobe Campaign中指定并可修改)。 因此，强烈建议定期导出日志。

### 技术表 {#technical-tables}

最后，部分数据模型包含用于应用程序的技术数据，包括运算符和用户权限(**NmsGroup**)、文件夹(**XtkFolder**)。

## 使用内置的Recipient表 {#default-recipient-table}

Adobe Campaign中内置的“收件人”表为构建数据模型提供了一个良好的起点。 它有许多预定义的字段和表链接，可轻松扩展。 当您主要定向收件人时，这种方法特别有用，因为它适合以收件人为中心的简单数据模型。

使用内置Recipient表的好处如下：

* 使用内置功能（如订阅、种子列表等）。
* 通过以收件人为中心的数据模型提供营销数据库。
* 更快的实施。
* 由支持人员和合作伙伴轻松维护。

但是，可以扩展“收件人”表，但不能减少表中字段或链接的数量。

>[!IMPORTANT]
>
>建议不要删除收件人表中的字段（即使这些字段无用），因为这可能会导致内置模块中出现错误。

此外，由于收件人表是产品的一部分，因此表及其关联形式都会随着产品的更改而发生变化。 因此，需要额外的维护才能检查升级时是否仍有任何扩展有效。

## 扩展数据模型 {#extending-data-model}

从Adobe Campaign开始，您需要评估默认数据模型，以检查哪个表最适合存储营销数据。

如果相关，您可以将默认的Recipient表与现成字段一起使用，如[此部分](#default-recipient-table)中所述。

如果需要，可以使用两种机制扩展该扩展：

* 使用新字段扩展现有表。 例如，您可以向收件人表中添加新的“忠诚度”字段。
* 创建一个新表（例如，列出数据库每个用户档案进行的所有购买的“购买”表），并将其链接到收件人表。

有关配置扩展架构以扩展概念数据模型的更多信息，请参阅[关于架构版本](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>扩展数据模型是为高级用户保留的。

## 使用自定义收件人表 {#custom-recipient-table}

在设计Adobe Campaign数据模型时，您可以使用[现成的收件人表](#default-recipient-table)，或决定创建[自定义收件人表](../../configuration/using/about-custom-recipient-table.md)表来存储营销用户档案。

事实上，如果您的数据模型不适合以收件人为中心的结构，则可以设置其他表作为Adobe Campaign中的定向维度。 例如，当您需要定位家庭、帐户（如手机）和公司/网站，而不是简单的收件人时，这可能会相关。

>[!NOTE]
>
>在这种情况下，您需要创建新的[目标映射](../../configuration/using/target-mapping.md)。

[此部分](../../configuration/using/about-custom-recipient-table.md)中详细介绍了使用自定义收件人表时需要遵循的所有原则和步骤。

使用自定义Recipient表的好处如下：

* **灵活的数据模型**  — 如果您不需要大多数收件人表字段，或者数据模型不以收件人为中心，则开箱即用的收件人表将毫无用处。

* **可扩展性**  — 大型卷需要一个精简的表格，其中很少有字段，才能进行高效的设计。现成的“收件人”表将包含太多无用的字段，这可能会影响性能并且缺乏效率。

* **数据位置**  — 如果数据位于外部现有营销数据库上，则使用现成的“收件人”表可能会花费太多的精力。基于现有结构创建新结构更简单。

* **轻松迁移**  — 无需维护，即可检查所有扩展在升级时是否仍然有效。

>[!IMPORTANT]
>
>使用自定义收件人表是为高级用户保留的，并受某些限制。 有关更多信息，请参阅[此章节](../../configuration/using/about-custom-recipient-table.md)。

## 相关主题

在以下章节中了解有关Campaign数据模型的更多信息：

* **主表的描述**  — 有关默认Campaign Classic数据模型描述的更多信息，请参阅 [此章节](../../configuration/using/data-model-description.md)。

* **每个表的完整说明**  — 要访问每个表的完整说明，请转到，从列 **[!UICONTROL Admin > Configuration > Data schemas]**&#x200B;表中选择资源，然后单击选 **[!UICONTROL Documentation]** 项卡。

   ![](assets/data-model_documentation-tab.png)


* **营销活动模式**  — 应用程序中承载数据的物理和逻辑结构以XML进行描述。它遵循 Adobe Campaign 特有的语法，称为模式。有关Adobe Campaign模式的更多信息，请阅读[此部分](../../configuration/using/about-schema-reference.md)。

* **数据模型最佳实践**  — 在此部分中了解Campaign数据模型架构和相关最 [佳实践](../../configuration/using/data-model-best-practices.md#data-model-architecture)。
