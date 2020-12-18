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
source-wordcount: '0'
ht-degree: 0%

---


# 迁移方法{#migration-method}

## 使环境现代化{#modernizing-your-environment}

执行迁移是更新环境（数据库引擎、操作系统）的机会。 Adobe Campaign强烈建议将生产环境升级到最新版本。

v7中仍支持32位版本的Adobe Campaign库和操作系统，但将来版本的数据库将不再支持。 我们强烈建议您尽快将平台升级到64位。

在v6.02中，“多时区”模式仅对PostgreSQL数据库引擎可用。 现在，无论使用哪种类型的数据库引擎，都可提供该引擎。 我们强烈建议您将您的基础转换为“多时区”基础。 有关此信息，请参见[时区](../../migration/using/general-configurations.md#time-zones)部分。

>[!IMPORTANT]
>
>Adobe Campaign5.11和6.02中支持的某些软件版本在Adobe Campaignv7中不再受支持。
>
>有关Adobe Campaign支持的版本的详细信息，请查阅[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

## 关键迁移步骤{#key-migration-steps}

迁移到Adobe Campaignv7的一般过程详见[开始迁移之前](../../migration/using/before-starting-migration.md)一节。

[迁移到Adobe Campaign7的先决条件部分中详细介绍了迁移到Adobe Campaign7的实施步骤。](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)

所需的配置取决于您的现有配置和平台的初始版本。 这些配置在[常规配置](../../migration/using/general-configurations.md)部分中概述。

## 特定配置{#specific-configurations}

v7Adobe Campaign带来的更改可能还意味着您必须调整在早期版本中开发的特定配置。 因此，在迁移之前，可能需要对您的所有配置执行审核：联系Adobe Campaign获取任何帮助。

例如，应特别注意Web 应用程序的特定设置、使用SQLdata模式扩展或开箱即用模式克隆。 有关详细信息，请参阅[配置平台](../../migration/using/configuring-your-platform.md)部分。

同样，为了响应Adobe Campaign内加强的安全，一些内部机制也进行了修改：您必须调整这些相应的配置。
