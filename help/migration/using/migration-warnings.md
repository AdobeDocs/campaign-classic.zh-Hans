---
product: campaign
title: 迁移警告
description: 迁移警告
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 46b46fc9-c7c9-4c74-b5f3-7935d5368520
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# 迁移警告{#migration-warnings}

![](../../assets/v7-only.svg)

* 迁移过程为专家用户保留。 您必须至少得到来自Adobe Campaign的数据库专家、系统管理员和应用程序开发人员的协助。
* 在开始迁移之前，请检查您使用的系统和系统组件是否实际与v7兼容。 请参阅[兼容性矩阵](../../rn/using/compatibility-matrix.md)。
* 如果您使用Adobe Campaign云消息传送（以前称为中间源），请先联系Adobe Campaign，然后再开始整个迁移过程。
* 在开始迁移过程之前，您&#x200B;**必须**&#x200B;备份数据。
* 迁移过程可能需要数天才能完成。
* Adobe Campaign v7在配置方面比5.11和6.02版本更严格。 这主要是为了避免数据损坏等问题，并在数据库中保留数据完整性。 因此，v5.11和v6.02中提供的某些功能在v7中可能不再工作，因此在迁移后可能需要进行调整。 在投入生产之前，我们建议您系统性地测试所有配置，特别是使用Adobe Campaign所必需的工作流。

>[!NOTE]
>
>您还必须查阅[开始迁移之前](../../migration/using/before-starting-migration.md)一节。
