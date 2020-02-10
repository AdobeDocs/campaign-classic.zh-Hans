---
title: 用途
seo-title: 用途
description: 用途
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 用途{#purpose}

此用例旨在将电子邮件附件快速添加到出站派单。

在此方案中，我们将了解如何发送包含个人／个性化附件的交易电子邮件。 附件不会预先上传到Transactional Messaging服务器上，而是会立即生成。

捕获客户互动或详细信息时，您可能需要在流程结束时将这些信息发送回客户，例如，在电子邮件附加的PDF文件中。 以下是此方案的一般步骤。

1. 客户进入网站，查找要购买的产品。
1. 客户选择产品并自定义一些选项。
1. 客户完成交易。
1. 向客户发送确认交易的电子邮件。 我们不希望在电子邮件中发送PII（个人身份识别信息），因此我们生成一个安全的PDF并将其附加到电子邮件中。
1. 客户收到包含所有所需数据的电子邮件及其附件。

在此方案中，附件不是预先创建的，而是即时添加到出站电子邮件中。 这还允许您个性化附件的内容。 此外，如果附件与事务关联（如上例所示），则您可能需要附件包含在客户流程中生成的动态数据。 这样附加PDF也会优化安全性，因为您可以加密PDF并通过HTTPS发送它们。
