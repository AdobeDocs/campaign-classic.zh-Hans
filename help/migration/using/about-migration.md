---
product: campaign
title: 迁移到Campaign Classic
description: 了解如何从以前的Campaign版本迁移到Campaign Classic
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# 迁移入门{#about-migration}

![](../../assets/v7-only.svg)

本文档详细介绍迁移的先决条件以及迁移到Adobe Campaign Classic v7的步骤。 步骤和可选设置取决于您的配置。

移民进程必须谨慎进行，其影响必须事先充分考虑，并且必须严格执行。 它只能由专家用户执行。 我们强烈建议您联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 开始任何迁移过程之前。

必须事先在测试/暂存环境中测试迁移，以确保迁移顺利运行且不发生任何错误。 只有在已迁移的测试环境完全验证后才能执行生产环境的迁移。

>[!NOTE]
>
>有关Adobe Campaign v7随附的新增功能和改进的详情，请参阅 [发行说明](../../rn/using/latest-release.md).


## 先决条件

* 迁移过程必须由专家用户执行。 您必须至少得到来自Adobe Campaign的数据库专家、系统管理员和应用程序开发人员的协助。
* 在开始迁移之前，请检查您使用的系统和系统组件是否与v7兼容。 [了解详情](../../rn/using/compatibility-matrix.md)。
* 如果您使用Adobe Campaign Cloud Messaging（中间源部署），请先联系Adobe客户关怀团队，然后再开始。
* 在开始迁移过程之前，您 **必须** 备份数据。
* 迁移过程可能需要数天才能完成。
* Adobe Campaign v7是比以前版本更安全的版本：这会影响配置准则，以避免数据损坏等问题，并保留数据库中的数据完整性。 作为客户，您有责任测试所有配置，包括工作流。

中提供了更多先决条件 [本页](../../migration/using/before-starting-migration.md).


## 现代化环境 {#modernizing-your-environment}

执行迁移是更新环境（数据库引擎、操作系统）的机会。 Adobe Campaign强烈建议将生产环境升级到最新版本。

>[!CAUTION]
>
>有关Adobe Campaign v7支持的版本的更多信息，请参阅 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

## 关键迁移步骤 {#key-migration-steps}

有关迁移到Adobe Campaign v7的一般过程，请参见 [本页](../../migration/using/before-starting-migration.md).


## 特定配置 {#specific-configurations}

Adobe Campaign v7带来的更改也意味着您必须调整在早期版本中开发的特定配置。 因此，在迁移之前，可能需要对您的所有配置执行审核：请联系Adobe Campaign以获取任何帮助。

例如，应特别注意Web应用程序的特定设置、使用SQLdata的模式扩展或即装即用模式克隆。 有关详细信息，请参见[此页面](../../migration/using/configuring-your-platform.md)。

同样，为了响应Adobe Campaign内加强的安全，一些内部机制也作了修改：您必须相应地调整这些配置。

