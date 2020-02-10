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


# 使用默认的“收件人”表{#default-recipient-table}

Adobe Campaign中现成的“收件人”表为构建数据模型提供了良好的起点。 它有许多可轻松扩展的预定义字段和表链接。 当您主要针对收件人时，此功能尤其有用，因为它适合以收件人为中心的简单数据模型。

使用标准收件人表的好处如下：

* 利用订阅、种子列表、调查、社交等功能开箱即用。
* 使用以收件人为中心的数据模型提供营销数据库。
* 更快的实施。
* 由支持和合作伙伴轻松维护。

但是，可以扩展“收件人”表，但不能减少表中字段或链接的数量。

>[!IMPORTANT]
>
>建议不要删除收件人表中的字段（即使这些字段没有用处），因为这可能会导致内置模块中的错误。

此外，由于“收件人”表是产品的一部分，因此表及其关联表单随着产品的更改而发展。 因此，需要额外的维护来检查升级后是否仍然有效。
