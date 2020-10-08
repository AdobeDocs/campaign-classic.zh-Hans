---
title: 开始迁移前
seo-title: 开始迁移前
description: 开始迁移前
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 3%

---


# 开始迁移前{#before-starting-migration}

>[!NOTE]
>
>在此文档中，以链接到数据库的命令为例。 这些属性可能因配置而异。 与数据库管理员联系。

## 警告 {#warnings}

### 已安装版本 {#installed-version}

在迁移之前，您应安装当前使用的最新版本的最新版本。

使用nlserver pdump命令转到客户端控 **[!UICONTROL Help> About]** 制台上的菜单，检查服 **务器上的版本** 。

### 数据备份 {#data-backup}

在开始迁移过程之前， **您必** 须备份数据。

### 环境 {#environment}

* 无法更改数据库引擎类型(DBMS)。 例如，您无法从PostgreSQL引擎切换到Oracle引擎。 但是，您可以从Oracle 8引擎切换到Oracle 10引擎。
* 无法从非Unicode数据库转换到Unicode数据库。

### 建议 {#recommendation}

由于迁移过程特别敏感，我们强烈建议在开始该过程之前彻底阅读此文档。

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

>[!NOTE]
>
>v6.02营销服务器与v7云消息或Power Booster/Cluster服务器之间可进行通信。 但是，如果您决定保留v6.02营销服务器，则必须使用最新v6.02版本更新此版本，然后才能迁移到云消息或Power Booster/Cluster。

## 用户密码 {#user-passwords}

在v7中，内 **部** 和管 **理员** 连接必须由密码保护。 我们强烈建议在迁移之前为这些帐户和所有操作员帐户 **分配口令**。 如果您没有为内部指定 **口令**，您将无法连接。 要将密码指定给 **内部**，请输入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>内 **部密码** （对于所有跟踪服务器）必须相同。 有关详细信息，请参阅“内部 [标识符](../../installation/using/campaign-server-configuration.md#internal-identifier) ”和“ [关于权限](../../platform/using/access-management.md#about-permissions) ”部分。

