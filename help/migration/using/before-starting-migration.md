---
solution: Campaign Classic
product: campaign
title: 开始迁移前
description: 开始迁移前
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 1%

---


# 开始迁移前{#before-starting-migration}

>[!NOTE]
>
>在此文档中，以链接到数据库的命令为例。 这些属性可能因配置而异。 与数据库管理员联系。

## 警告 {#warnings}

* 迁移过程必须由专家用户执行。 您必须至少得到Adobe Campaign库专家、系统管理员和应用程序开发人员的协助。
* 开始迁移之前，请检查您使用的系统和系统组件是否与v7实际兼容。 请查阅兼 [容性矩阵](../../rn/using/compatibility-matrix.md)。
* 如果您使用Adobe Campaign云消息(中间源)，请在开始整个迁移过程之前与Adobe联系。
* 在开始迁移过程之前， **您必** 须备份数据。
* 迁移过程可能需要数天才能完成。
* Adobe Campaignv7在配置方面比5.11和6.02版本更严格。 这主要是为了避免数据损坏等问题，并在数据库中保持数据完整性。 因此，v5.11和v6.02中提供的某些功能在v7中可能不再工作，因此在迁移后可能需要调整。 在投入生产之前，我们建议您系统地测试所有配置，特别是使用工作流所必需的Adobe Campaign。

### 已安装版本 {#installed-version}

在迁移之前，您应安装当前使用的最新版本的最新版本。

使用nlserver pdump命令转到客户端控 **[!UICONTROL Help> About]** 制台上的菜单，检查服 **务器上的版本** 。

### 数据备份 {#data-backup}

在开始迁移过程之前， **您必** 须备份数据。

### 环境 {#environment}

* 无法更改数据库引擎类型(DBMS)。 例如，您无法从PostgreSQL引擎切换到Oracle引擎。 但是，您可以从Oracle8引擎切换到Oracle10引擎。
* 无法从非Unicode数据库转换到Unicode数据库。

### 建议 {#recommendation}

由于迁移过程是敏感的，我们强烈建议在开始该过程之前彻底阅读此文档。

## 迁移步骤 {#migration-steps}

迁移过程必须在所有服 **务器上** ，并且按特定顺序执行。

* 对于独立平台 **(单机** 模式)，将完整迁移应用程序。
* 对于标准平 **台** （企业），迁移步骤如下：

   1. 迁移营销服务器。
   1. 迁移邮件服务器(mta)。
   1. 迁移重定向和跟踪服务器(Apache / IIS)。

* 对于云消息 **平台**，执行服务器托管在Adobe Campaign。 请与Adobe Campaign联系以协调不同服务器之间的迁移。
* 在Power Booster或 **Power Cluster平台中**，迁移步骤如下：

   1. 迁移重定向和跟踪服务器(Apache / IIS)。
   1. 迁移Power Booster/群集服务器。
   1. 迁移营销服务器。

## 用户密码 {#user-passwords}

在v7中，内 **部** 和管 **理员** 连接必须由密码保护。 我们强烈建议在迁移之前为这些帐户和所有操作员帐户 **分配口令**。 如果您没有为内部指定 **口令**，您将无法连接。 要将密码指定给 **内部**，请输入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>内 **部密码** （对于所有跟踪服务器）必须相同。 有关详细信息，请参阅“内部 [标识符](../../installation/using/campaign-server-configuration.md#internal-identifier) ”和“ [关于权限](../../platform/using/access-management.md#about-permissions) ”部分。

