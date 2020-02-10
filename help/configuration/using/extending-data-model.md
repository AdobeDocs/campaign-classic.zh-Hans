---
title: 使用Adobe Campaign Classic收件人表
description: 了解如何在设计数据模型时使用Adobe Campaign Classic中开箱即用的收件人表。
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


# 扩展数据模型{#extending-data-model}

从Adobe Campaign开始，您需要评估默认数据模型以检查哪个表最适合存储您的营销数据。

如果相关，您可以将默认的“收件人”表与现成字段一起使用，如本节中所述 [](../../configuration/using/default-recipient-table.md)。

如果需要，您可以使用两种机制扩展它：

* 使用新字段扩展现有表。 例如，您可以向“收件人”表添加新的“忠诚度”字段。
* 创建一个新表（例如，“购买”表），列出数据库每个配置文件所购买的所有数据，并将其链接到“收件人”表。

有关配置扩展架构以扩展概念数据模型的详细信息，请参 [阅关于架构版](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>扩展数据模型是为高级用户保留的。
