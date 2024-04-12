---
product: campaign
title: 迁移到Campaign Classic
description: 了解如何从以前的Campaign版本迁移到Campaign Classic
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# 迁移入门{#about-migration}



本文档详细介绍迁移的先决条件，以及迁移到Adobe Campaign Classic v7的步骤。 步骤和可选设置取决于您的配置。

移徙进程必须谨慎进行，必须事先充分考虑其影响，必须严格执行这一程序。 必须仅由专家用户执行。 我们强烈建议您联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) ，然后再开始任何迁移过程。

必须预先在测试/暂存环境中测试迁移，以确保其顺利运行且无任何错误。 只有在迁移的测试环境经过完全验证后，才能迁移生产环境。

>[!NOTE]
>
>有关Adobe Campaign v7的新增功能和改进的详情，请参见 [发行说明](../../rn/using/latest-release.md).


## 先决条件

* 迁移过程必须由专家用户执行。 您必须至少获得Adobe Campaign的数据库专家、系统管理员和应用程序开发人员的协助。
* 在开始迁移之前，请检查您使用的系统和系统组件是否与v7兼容。 [了解详情](../../rn/using/compatibility-matrix.md)。
* 如果您使用Adobe Campaign Cloud Messaging（中间源部署），请在开始之前联系Adobe客户关怀部门。
* 在开始迁移过程之前，您 **必须** 备份您的数据。
* 迁移过程可能需要几天才能完成。
* Adobe Campaign v7比以前的版本更安全：这将影响配置准则，以避免数据损坏之类的问题并保持数据库中的数据完整性。 作为客户，您负责测试所有配置，包括工作流。

有关更多先决条件，请参阅 [此页面](../../migration/using/before-starting-migration.md).


## 现代化环境 {#modernizing-your-environment}

执行迁移可能是更新环境（数据库引擎、操作系统）的机会。 Adobe Campaign强烈建议将您的生产环境升级到最新版本。

>[!CAUTION]
>
>有关Adobe Campaign v7支持的版本的更多信息，请参阅 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

## 关键迁移步骤 {#key-migration-steps}

有关迁移到Adobe Campaign v7的详细过程，请参见 [此页面](../../migration/using/before-starting-migration.md).


## 特定配置 {#specific-configurations}

Adobe Campaign v7带来的更改可能还意味着您必须调整在早期版本中开发的特定配置。 因此，在迁移之前，可能必须对您的所有配置执行审核：如需任何帮助，请联系Adobe Campaign 。

例如，应特别注意Web应用程序、带有SQL数据的模式扩展或现成模式克隆的特定设置。 有关详细信息，请参见[此页面](../../migration/using/configuring-your-platform.md)。

同样，为了响应Adobe Campaign中增强的安全功能，我们修改了一些内部机制：您必须相应地调整这些配置。

