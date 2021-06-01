---
product: campaign
title: 迁移方法
description: 迁移方法
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: dd4d068b-f414-448f-8d9a-eedf44e7b6e6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---

# 迁移方法{#migration-method}

## 使您的环境现代化{#modernizing-your-environment}

执行迁移是更新环境（数据库引擎、操作系统）的机会。 Adobe Campaign强烈建议将生产环境升级到最新版本。

v7仍支持32位版本的数据库和操作系统，但将来版本的Adobe Campaign将不再支持32位版本的数据库和操作系统。 我们强烈建议您尽快将您的平台升级到64位。

在v6.02中，“多时区”模式仅适用于PostgreSQL数据库引擎。 现在，无论使用哪种类型的数据库引擎，都会提供该引擎。 我们强烈建议您将您的基础转换为“多时区”基础。 有关此内容的更多信息，请参阅[时区](../../migration/using/general-configurations.md#time-zones)部分。

>[!IMPORTANT]
>
>Adobe Campaign 5.11和6.02中支持的某些软件版本在Adobe Campaign v7中不再受支持。
>
>有关Adobe Campaign支持的版本的更多信息，请参阅[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

## 关键迁移步骤{#key-migration-steps}

[开始迁移之前](../../migration/using/before-starting-migration.md)部分中详细说明了迁移到Adobe Campaign v7的一般过程。

有关迁移到Adobe Campaign v7的实施步骤详情，请参阅[迁移到Adobe Campaign 7的先决条件](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)一节。

所需的配置取决于您的现有配置和平台的初始版本。 [常规配置](../../migration/using/general-configurations.md)部分中概述了这些配置。

## 特定配置{#specific-configurations}

Adobe Campaign v7带来的更改也意味着您必须调整在早期版本中开发的特定配置。 因此，在迁移之前，可能需要对您的所有配置执行审核：请联系Adobe Campaign以获取任何帮助。

例如，应特别注意Web应用程序的特定设置、使用SQLdata的模式扩展或即装即用模式克隆。 有关更多信息，请参阅[配置平台](../../migration/using/configuring-your-platform.md)一节。

同样，为了响应Adobe Campaign内加强的安全，一些内部机制也作了修改：您必须调整这些相应的配置。
