---
product: campaign
title: 开始使用Campaign Classic数据模型
description: 了解如何扩展 Campaign 数据模型、编辑模式、使用 API 等
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Data Model
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# Campaign 数据模型快速入门{#about-data-model}

Adobe Campaign 数据库的概念数据模型由一组内置表及它们之间的交互组成。本页中列出了主要表格和概念。

## 概述 {#data-model-overview}

Adobe Campaign依赖于包含链接在一起的表的关系数据库。 Adobe Campaign数据模型的基本结构描述如下。

### 收件人表 {#recipient-table}

数据模型依赖于主表，该主表默认为收件人表(**NmsRecipient**)。 此表允许存储所有营销配置文件。

有关“收件人”表的详细信息，请参阅 [本节](#default-recipient-table).

### 投放表 {#delivery-table}

数据模型还包括用于存储所有营销活动的专用部分。 通常为投放表(**NmsDelivery**)。 此表中的每条记录都表示一个投放操作或投放模板。 它包含执行投放所需的所有参数，如目标、内容等。

### 日志表 {#log-tables}

数据模型的另一部分允许临时存储与活动执行关联的所有日志。

投放日志是跨所有渠道发送给收件人或设备的所有消息。 主投放日志表(**NmsBroadLog**)包含所有收件人的投放日志。
主跟踪日志表(**NmsTrackingLog**)存储所有收件人的跟踪日志。 跟踪日志是指收件人的反应，例如电子邮件打开次数和点击次数。 每个反应都与一个跟踪日志相对应。
投放日志和跟踪日志会在特定时段后删除，该特定时段在Adobe Campaign中指定并可修改。 因此，强烈建议定期导出日志。

### 技术表 {#technical-tables}

最后，部分数据模型包含用于应用流程的技术数据，包括操作员和用户权限(**NmsGroup**)，文件夹(**XtkFolder**)。

## 使用内置的收件人表 {#default-recipient-table}

Adobe Campaign中内置的收件人表为构建数据模型提供了一个良好的起点。 它具有许多可以轻松扩展的预定义字段和表链接。 当您主要定位收件人时，这项功能尤其有用，因为它适合以收件人为中心的简单数据模型。

使用内置收件人表的好处如下：

* 使用内置（如订阅、种子列表等）功能。
* 为营销数据库提供以收件人为中心的数据模型。
* 更快的实施。
* 支持人员和合作伙伴可轻松维护。

但是，可以扩展Recipient表，但不能减少表中的字段或链接数。

>[!IMPORTANT]
>
>建议不要删除收件人表中的字段（即使它们毫无用处），因为这样可能会导致内置模块中出现错误。

此外，由于收件人表是产品的一部分，因此该表及其关联形式都会随着产品的变化而改变。 因此，需要进行额外维护，以检查在升级时任何扩展是否仍然有效。

## 扩展数据模型 {#extending-data-model}

开始使用Adobe Campaign时，您需要评估默认数据模型，以检查哪个表最适合存储营销数据。

如果相关，您可以使用带有现成字段的默认“收件人”表，如中所述 [本节](#default-recipient-table).

如果需要，可以使用以下两种机制来扩展它：

* 使用新字段扩展现有表。 例如，您可以向收件人表添加新的“忠诚度”字段。
* 创建一个新表，例如“购买”表，列出数据库的每个用户档案进行的所有购买，并将其链接到收件人表。

有关配置扩展模式以扩展概念数据模型的更多信息，请参阅 [关于模式版本](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>数据模型扩展是为高级用户保留的。

## 使用自定义收件人表 {#custom-recipient-table}

在设计Adobe Campaign数据模型时，您可以使用 [内置收件人表](#default-recipient-table)，或决定创建 [自定义收件人表](../../configuration/using/about-custom-recipient-table.md) 用于存储营销用户档案的表。

事实上，如果您的数据模型不符合以收件人为中心的结构，您可以在Adobe Campaign中将其他表设置为定向维度。 例如，当您需要定位家庭、帐户（如手机）和公司/网站（而不仅仅是收件人）时，这可能具有相关性。

>[!NOTE]
>
>在这种情况下，您需要创建一个 [目标映射](../../configuration/using/target-mapping.md).

有关使用自定义收件人表所需的所有原则和步骤的详情，请参阅 [本节](../../configuration/using/about-custom-recipient-table.md).

使用自定义收件人表的好处如下：

* **灵活的数据模型**  — 如果您不需要大多数收件人表字段，或者数据模型不是以收件人为中心，则内置的收件人表将毫无用处。

* **可扩展性**  — 大型卷需要简化的表，且表几乎没有字段以实现高效设计。 内置的收件人表将有太多无用的字段，这可能会影响性能并缺乏效率。

* **数据位置**  — 如果数据驻留在外部现有的营销数据库中，则使用内置的收件人表可能需要花费太多时间。 基于现有结构创建新结构比较简单。

* **轻松迁移**  — 无需维护，即可检查升级时所有扩展是否仍然有效。

>[!IMPORTANT]
>
>自定义收件人表是为高级用户保留的，并受某些限制。 有关更多信息，请参阅[此章节](../../configuration/using/about-custom-recipient-table.md)。

## 相关主题

要了解有关Campaign数据模型的更多信息，请参阅以下部分：

* **主表的说明**  — 有关默认Campaign Classic数据模型说明的更多信息，请参阅 [本节](../../configuration/using/data-model-description.md).

* **每个表的完整说明**  — 要访问每个表的完整说明，请转到 **[!UICONTROL Admin > Configuration > Data schemas]**，从列表中选择资源并单击 **[!UICONTROL Documentation]** 选项卡。

   ![](assets/data-model_documentation-tab.png)


* **营销活动模式**  — 以XML描述应用程序中承载数据的物理和逻辑结构。 它遵循 Adobe Campaign 特有的语法，称为模式。有关Adobe Campaign架构的更多信息，请阅读 [本节](../../configuration/using/about-schema-reference.md).

* **数据模型最佳实践**  — 在以下位置了解Campaign数据模型架构和相关最佳实践： [本节](../../configuration/using/data-model-best-practices.md#data-model-architecture).
