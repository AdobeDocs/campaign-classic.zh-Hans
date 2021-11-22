---
product: campaign
title: 开始迁移前
description: 开始迁移前
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---

# 开始迁移前{#before-starting-migration}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>在本文档中，以链接到数据库的命令为例。 这些值可能因其配置而异。 与数据库管理员联系。

## 警告 {#warnings}

* 迁移过程必须仅由专家用户执行。 您必须至少得到来自Adobe Campaign的数据库专家、系统管理员和应用程序开发人员的协助。
* 在开始迁移之前，请检查您使用的系统和系统组件是否实际与v7兼容。 请查阅 [兼容性矩阵](../../rn/using/compatibility-matrix.md).
* 如果您使用Adobe Campaign Cloud Messaging（中间源），请在开始整个迁移过程之前联系Adobe。
* 在开始迁移过程之前，您 **必须** 备份数据。
* 迁移过程可能需要数天才能完成。
* Adobe Campaign v7在配置方面比5.11和6.02版本更严格。 这主要是为了避免数据损坏等问题，并在数据库中保留数据完整性。 因此，v5.11和v6.02中提供的某些功能在v7中可能不再工作，因此在迁移后可能需要进行调整。 在投入生产之前，我们建议您系统性地测试所有配置，特别是使用Adobe Campaign所必需的工作流。

### 已安装版本 {#installed-version}

在迁移之前，您应安装当前所用版本的最新版本。

转到 **[!UICONTROL Help> About]** 菜单(使用 **nlserver pdump** 命令。

### 数据备份 {#data-backup}

在开始迁移过程之前，您 **必须** 备份数据。

### 环境 {#environment}

* 无法更改数据库引擎类型(DBMS)。 例如，您无法从PostgreSQL引擎切换到Oracle引擎。 但是，您可以从Oracle8引擎切换到Oracle10引擎。
* 无法从非Unicode数据库转到Unicode数据库。

### 推荐 {#recommendation}

由于迁移过程是敏感的，因此我们强烈建议在开始该过程之前彻底阅读此文档。

## 迁移步骤 {#migration-steps}

必须执行迁移程序 **全部** 按特定顺序排列。

* 对于 **独立平台** （单机模式），则应用程序将完全迁移。
* 对于 **标准平台** （企业），迁移步骤如下：

   1. 迁移营销服务器。
   1. 迁移邮件服务器(mta)。
   1. 迁移重定向和跟踪服务器(Apache/IIS)。

* 对于 **云消息平台**，则执行服务器托管在Adobe Campaign。 请联系Adobe Campaign以协调不同服务器之间的迁移。
* 对于 **Power Booster或Power Cluster平台**，则迁移步骤如下：

   1. 迁移重定向和跟踪服务器(Apache/IIS)。
   1. 迁移Power Booster/群集服务器。
   1. 迁移营销服务器。

## 用户密码 {#user-passwords}

在v7中， **内部** 和 **管理员** 操作员连接必须用密码保护。 我们强烈建议为这些帐户和所有操作员帐户分配密码， **迁移前**. 如果尚未为 **内部**，您将无法连接。 要将密码分配给 **内部**，输入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>的 **内部** 所有跟踪服务器的密码必须相同。 有关更多信息，请参阅 [内部标识符](../../installation/using/configuring-campaign-server.md#internal-identifier) 和 [权限](../../platform/using/access-management.md) 中。
