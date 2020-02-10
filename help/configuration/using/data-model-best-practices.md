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
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# 数据模型最佳实践{#data-model-best-practices}

以下是使用大表和复杂连接设计数据模型时应遵循的一些最佳实践。

* 使用其他自定义收件人表时，请确保每个传送映射都有一个专用的日志表。
* 减少列数，特别是通过识别未使用的列数。
* 通过避免复杂连接（例如在多个条件和／或多个列上的连接）来优化数据模型关系。
* 对于连接键，请始终使用数字数据而不是字符串。
* 尽可能减少日志保留深度。 如果需要更深入的历史记录，您可以聚合计算和／或处理自定义日志表以存储更大的历史记录。

有关如何为较大的卷优化数据库设计的更多详细信息，请参阅 [Campaign Classic数据模型最佳实践](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html)。
