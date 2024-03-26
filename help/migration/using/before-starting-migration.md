---
product: campaign
title: 开始迁移前
description: 开始迁移前
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 4%

---

# 先决条件{#before-starting-migration}



本页列出了在开始迁移过程之前要执行的特定步骤。 您还必须参考 [此页面](about-migration.md) 以获取更多指导。

>[!NOTE]
>
>在本文档中，命令以示例形式提供。 具体情况可能因您的配置而异。

1. 检查您的Adobe Campaign版本：在迁移之前，请安装您当前使用版本的最新内部版本。
1. 备份您的数据。
1. 检查环境：无法更改数据库引擎系统(DBMS)。 例如，您无法从PostgreSQL引擎切换到Oracle引擎。 但是，您可以切换到数据库引擎的最新版本。 请注意，不能从非Unicode数据库转到Unicode数据库。

## 迁移步骤 {#migration-steps}

必须执行迁移过程于 **所有** 按特定顺序执行操作。

* 在a **独立平台** （单机模式），则整个应用程序都将迁移。
* 在a **标准平台** （企业），迁移步骤如下：

   1. 迁移营销服务器。
   1. 迁移邮件服务器(mta)。
   1. 迁移重定向和跟踪服务器(Apache / IIS)。

* 在a **云消息平台**，则执行服务器托管在Adobe Campaign上。 请联系Adobe Campaign以协调不同服务器之间的迁移。
* 在a **Power Booster或Power Cluster平台**，迁移步骤如下所示：

   1. 迁移重定向和跟踪服务器(Apache / IIS)。
   1. 迁移Power Booster/Cluster服务器
   1. 迁移营销服务器。

## 用户密码 {#user-passwords}

在v7中， **内部** 和 **管理员** 运算符连接必须使用密码进行保护。 我们强烈建议为这些帐户和所有操作员帐户分配密码， **迁移前**. 如果尚未指定密码 **内部**，您将无法连接。 要将密码分配给 **内部**，输入以下命令：

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>此 **内部** 所有跟踪服务器的密码必须相同。 欲了解更多信息，请参见 [内部标识符](../../installation/using/configuring-campaign-server.md#internal-identifier) 和 [权限](../../platform/using/access-management.md) 部分。
