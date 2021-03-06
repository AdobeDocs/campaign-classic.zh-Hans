---
product: campaign
title: 开始迁移前
description: 开始迁移前
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# 先决条件{#before-starting-migration}

![](../../assets/v7-only.svg)

此页面列出了在开始迁移过程之前要执行的特定步骤。 您还必须引用 [本页](about-migration.md) 以获取更多指导。

>[!NOTE]
>
>在本文档中，提供了命令作为示例。 这些值可能因您的配置而异。

1. 查看您的Adobe Campaign版本：在迁移之前，请安装您当前使用的最新版本。
1. 备份数据。
1. 检查您的环境：不能更改数据库引擎系统(DBMS)。 例如，您无法从PostgreSQL引擎切换到Oracle引擎。 但是，您可以切换到数据库引擎的最新版本。 请注意，不能从非Unicode数据库转到Unicode数据库。

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

>[!CAUTION]
>
>的 **内部** 所有跟踪服务器的密码必须相同。 有关更多信息，请参阅 [内部标识符](../../installation/using/configuring-campaign-server.md#internal-identifier) 和 [权限](../../platform/using/access-management.md) 中。
