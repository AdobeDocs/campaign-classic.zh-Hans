---
solution: Campaign Classic
product: campaign
title: 迁移方法
description: 迁移方法
audience: migration
content-type: reference
topic-tags: migration-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---


# 迁移方法{#migration-method}

## 使您的环境现代化{#modernizing-your-environment}

执行迁移是更新环境（数据库引擎、操作系统）的机会。 Adobe Campaign强烈建议将生产环境升级到最新版本。

v7中仍支持32位版本的数据库和操作系统，但将来版本的Adobe Campaign将不再支持。 我们强烈建议您尽快将您的平台升级到64位。

在v6.02中，“多时区”模式仅对PostgreSQL数据库引擎可用。 现在，无论使用哪种类型的数据库引擎，都可提供此功能。 我们强烈建议您将您的基础转换为“多时区”基础。 有关此信息的详细信息，请参阅[时区](../../migration/using/general-configurations.md#time-zones)部分。

>[!IMPORTANT]
>
>Adobe Campaign 5.11和6.02中支持的某些软件版本在Adobe Campaign v7中不再受支持。
>
>有关Adobe Campaign支持的版本的详细信息，请查阅[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

## 关键迁移步骤{#key-migration-steps}

[开始迁移之前](../../migration/using/before-starting-migration.md)部分详细介绍了迁移到Adobe Campaign v7的一般过程。

[迁移到Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)部分的先决条件中详细介绍了迁移到Adobe Campaign v7的实施步骤。

所需的配置取决于您的现有配置和平台的初始版本。 这些配置在[常规配置](../../migration/using/general-configurations.md)部分中概述。

## 特定配置{#specific-configurations}

Adobe Campaign v7带来的更改可能还意味着您必须调整在早期版本中开发的特定配置。 因此，在迁移之前，可能需要对您的所有配置执行审核：联系Adobe Campaign获取任何帮助。

例如，应特别注意Web 应用程序的特定设置、使用SQLdata模式扩展或开箱即用的模式克隆。 有关详细信息，请参阅[配置平台](../../migration/using/configuring-your-platform.md)部分。

同样，为了响应Adobe Campaign内加强的安全，一些内部机制也作了修改：您必须调整这些相应的配置。
