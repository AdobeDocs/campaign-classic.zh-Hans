---
title: 关于Adobe Campaign Classic数据模型
description: 本文档介绍了Adobe Campaign Classic数据模型的基础知识。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# 使用自定义收件人表{#custom-recipient-table}

在设计Adobe Campaign数据模型时，您可以使用现成的“收件人” [表](../../configuration/using/default-recipient-table.md)，或者决定创建非标准的“收件人”表来存储您的营销档案。

事实上，如果您的数据模型不符合以收件人为中心的结构，您可以在Adobe Campaign中将其他表设置为定位维度。 例如，当您需要锁定家庭、帐户（如手机）和公司／站点，而不是单纯的接收者时，这可能是相关的。

>[!NOTE]
>
>在这种情况下，您需要创建新的目 [标映射](../../configuration/using/target-mapping.md)。

本节详细介绍了使用自定义收件人表时所需的所有原则和步 [骤](../../configuration/using/about-custom-recipient-table.md)。

使用自定义收件人表的好处如下：

## 灵活的数据模型 {#flexible-data-model}

如果您不需要大多数“收件人”表字段，或者如果数据模型不是以收件人为中心，现成的“收件人”表将毫无用处。

## 可伸缩性 {#scalability}

大型卷需要简化的表格，并且字段很少，这样才能实现高效设计。 现成的“收件人”表将包含太多无用的字段，这可能会影响性能并且缺乏效率。

## 数据位置 {#data-location}

如果数据驻留在外部现有营销数据库上，则使用开箱即用的“收件人”表可能需要太多的工作。 基于现有结构创建新结构更简单。

## 轻松迁移 {#easy-migration}

无需维护即可检查所有扩展在升级后是否仍然有效。

>[!IMPORTANT]
>
>使用自定义收件人表是为高级用户保留的，并受某些限制。 有关此方面的详细信息，请参阅此部分。
