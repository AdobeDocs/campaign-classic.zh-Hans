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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# 开始迁移前{#before-starting-migration}

>[!NOTE]
>
>在本文中，给出了链接到数据库的命令示例。 这些参数可能因配置而异。 与数据库管理员联系。

## 警告 {#warnings}

### 已安装版本 {#installed-version}

在迁移之前，您应安装当前使用的最新版本的最新版本。

使用nlserver pdump命令转到客户端控制 **[!UICONTROL Help> About]** 台上的菜单，检查服务器 **上的版本** 。

### 数据备份 {#data-backup}

在开始迁移过程之前， **您必** 须备份数据。

### 环境 {#environment}

* 无法更改数据库引擎类型(DBMS)。 例如，您无法从PostgreSQL引擎切换到Oracle引擎。 但是，您可以从Oracle 8引擎切换到Oracle 10引擎。
* 不能从非Unicode数据库转到Unicode数据库。

### 建议 {#recommendation}

由于迁移过程特别敏感，我们强烈建议在开始该过程之前彻底阅读本文档。

## 迁移步骤 {#migration-steps}

迁移过程必须在所有服务器上 **执行** ，并且按特定顺序执行。

* 对于独立平台 **** （单机器模式），将迁移整个应用程序。
* 对于标准平台 **** （企业），迁移步骤如下：

   1. 迁移营销服务器。
   1. 迁移邮件服务器(mta)。
   1. 迁移重定向和跟踪服务器(Apache / IIS)。

* 对于云消息 **平台**，执行服务器托管在Adobe Campaign。 请联系Adobe Campaign以协调不同服务器之间的迁移。
* 对于Power Booster或 **Power Cluster平台**，迁移步骤如下：

   1. 迁移重定向和跟踪服务器(Apache / IIS)。
   1. 迁移Power Booster/群集服务器。
   1. 迁移营销服务器。

>[!NOTE]
>
>v6.02营销服务器与v7云消息或Power Booster/Cluster服务器之间的通信是可能的。 但是，如果您决定保留v6.02营销服务器，则必须使用最新v6.02版本更新该版本，然后才能迁移到云消息或Power Booster/Cluster。

## 用户密码 {#user-passwords}

在v7中，内部 **和** admin运 **** 营商连接必须由密码保护。 我们强烈建议在迁移之前为这些帐户和所有操作员帐户分 **配密码**。 如果尚未为内部指定密 **码**，则将无法连接。 要为内部分配密 **码**，请输入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>对于 **所有跟踪服务器** ，内部密码必须相同。 有关详细信息，请参阅“内部标 [识符](../../installation/using/campaign-server-configuration.md#internal-identifier) ”和“ [关于权限](../../platform/using/access-management.md#about-permissions) ”部分。

