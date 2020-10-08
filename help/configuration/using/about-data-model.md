---
title: 关于Adobe Campaign Classic数据模型
description: 了解如何扩展活动数据模型、编辑模式、使用API等。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 5%

---


# About the Campaign data model{#about-data-model}

本节介绍Adobe Campaign Classic数据模型的基础知识，以更好地了解活动内置表及其交互。

Adobe Campaign 数据库的概念数据模型由一组内置表及它们之间的交互组成。

要访问每个表的说明，请转 **[!UICONTROL Admin > Configuration > Data schemas]**&#x200B;到，从列表中选择资源，然后单击选 **[!UICONTROL Documentation]** 项卡。

![](assets/data-model_documentation-tab.png)

有关默认Campaign Classic数据模型描述的详细信息，请参 [阅本节](../../configuration/using/data-model-description.md)。

应用中所承载数据的物理和逻辑结构以 XML 格式进行描述。它遵循 Adobe Campaign 特有的语法，称为模式。For more on Adobe Campaign schemas, read out [this section](../../configuration/using/about-schema-reference.md).

## 概述 {#data-model-overview}

Adobe Campaign依赖于包含链接在一起的表的关系数据库。 Adobe Campaign数据模型的基本结构可以描述如下。

>[!NOTE]
>
>有关活动数据模型体系结构和相关最佳实践的详细信息，请参 [阅本节](../../configuration/using/data-model-best-practices.md#data-model-architecture)。

### 收件人表 {#recipient-table}

数据模型依赖于主表，该主表默认为收件人表(**NmsRecipient**)。 此表可用于存储所有营销用户档案。

有关收件人表的详细信息，请参 [阅此部分](#default-recipient-table)。

### 投放表 {#delivery-table}

数据模型还包括专用于存储所有营销活动的部件。 通常它是投放表(**NmsDelivery**)。 此表中的每个记录都表示投放操作或投放模板。 它包含执行投放(如目标、内容等)所需的所有参数。

### 日志表 {#log-tables}

数据模型的另一部分允许临时存储与执行活动相关的所有日志。

投放日志是所有渠道发送给收件人或设备的所有消息。 主投放日志表(**NmsBroadLog**)包含所有收件人的投放日志。
主跟踪日志表(**NmsTrackingLog**)存储所有收件人的跟踪日志。 跟踪日志是指收件人的反应，如电子邮件的打开和点击。 每个反应都对应一个跟踪日志。
投放日志和跟踪日志在特定时间段后被删除，该时间段在Adobe Campaign中指定并可以修改。 因此，强烈建议定期出口日志。

### 技术表 {#technical-tables}

最后，部分数据模型包含用于应用程序过程的技术数据，包括操作符和用户权&#x200B;**限(NmsGroup**)、文件夹(**XtkFolder**)。

## 使用默认收件人表 {#default-recipient-table}

Adobe Campaign中开箱即用的收件人表为构建数据模型提供了良好的起点。 它有许多可轻松扩展的预定义字段和表链接。 当您主要针对收件人时，此功能特别有用，因为它适合以收件人为中心的简单数据模型。

使用标准收件人表的好处如下：

* 利用订阅、种子列表、调查、社交等功能开箱即用。
* 为营销数据库提供以收件人为中心的数据模型。
* 更快的实施。
* 由支持和合作伙伴轻松维护。

但是，可以扩展收件人表，但不能减少表中的字段或链接数。

>[!IMPORTANT]
>
>建议不要删除收件人表中的字段（即使这些字段无用），因为这可能会导致内置模块中出现错误。

此外，由于收件人表是产品的一部分，因此表及其关联表单随着产品的变化而发展。 因此，需要进行额外的维护，以检查升级后是否仍有任何扩展有效。

## 扩展数据模型 {#extending-data-model}

从Adobe Campaign开始，您需要评估默认数据模型，以检查哪个表最适合存储您的营销数据。

如果相关，您可以将默认收件人表与现成的字段一起使用，如本 [节所述](#default-recipient-table)。

如果需要，可以使用两种机制扩展它：

* 使用新字段扩展现有表。 例如，您可以向收件人表添加新的“Loyalty”字段。
* 创建一个新表（例如，“购买”表），列出数据库每个用户档案所购买的所有数据，并将其链接到收件人表。

有关配置扩展模式以扩展概念数据模型的详细信息，请参 [阅关于模式版](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>扩展数据模型是为高级用户保留的。

## Using a custom recipient table {#custom-recipient-table}

在设计Adobe Campaign数据模型时，您可 [以使用现成的收件人表](#default-recipient-table)，或者决定创建非标准收件人表来存储您的营销用户档案。

事实上，如果您的数据模型不符合以收件人为中心的结构，您可以设置其他表作为Adobe Campaign中的定位维度。 例如，当您需要目标家庭、帐户（如手机）和公司/站点，而不是简单的收件人时，这可能是相关的。

>[!NOTE]
>
>在这种情况下，您需要创建新 [目标映射](../../configuration/using/target-mapping.md)。

本节详细介绍使用自定义收件人表时需要的所有原 [则和步骤](../../configuration/using/about-custom-recipient-table.md)。

使用自定义收件人表的好处如下：

### 灵活的数据模型 {#flexible-data-model}

如果您不需要大多数收件人表字段，或者数据模型不是以收件人为中心，现成的收件人表将毫无用处。

### 可伸缩性 {#scalability}

大型卷需要简化表格，并且字段少，这样才能进行高效设计。 现成的收件人表中有太多无用的字段，这可能影响性能并且缺乏效率。

### 数据位置 {#data-location}

如果数据驻留在外部现有的营销收件人库上，则使用现成的营销表可能需要过多的精力。 基于现有结构创建新结构更简单。

### 轻松迁移 {#easy-migration}

无需维护即可检查所有扩展在升级后是否仍然有效。

>[!IMPORTANT]
>
>使用自定义收件人表是为高级用户保留的，并受某些限制。 有关更多信息，请参阅[此章节](../../configuration/using/about-custom-recipient-table.md)。
