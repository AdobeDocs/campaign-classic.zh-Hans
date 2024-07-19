---
product: campaign
title: 开始迁移前
description: 开始迁移前
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# 先决条件{#before-starting-migration}



本页列出了在开始迁移过程之前要执行的特定步骤。 有关更多指导，您还必须参考[此页面](about-migration.md)。

>[!NOTE]
>
>在本文档中，命令以示例形式提供。 具体情况可能因您的配置而异。

1. 检查您的Adobe Campaign版本：在迁移之前，请安装您当前使用版本的最新内部版本。
1. 备份您的数据。
1. 检查环境：无法更改数据库引擎系统(DBMS)。 例如，您无法从PostgreSQL引擎切换到Oracle引擎。 但是，您可以切换到数据库引擎的最新版本。 请注意，不能从非Unicode数据库转到Unicode数据库。

## 迁移步骤 {#migration-steps}

迁移过程必须在&#x200B;**所有**&#x200B;服务器上按特定顺序执行。

* 在&#x200B;**独立平台**（单机模式）的情况下，将迁移整个应用程序。
* 对于&#x200B;**标准平台** （企业），迁移步骤如下：

   1. 迁移营销服务器。
   1. 迁移邮件服务器(mta)。
   1. 迁移重定向和跟踪服务器(Apache / IIS)。

* 在&#x200B;**Cloud Messaging平台**&#x200B;中，执行服务器托管在Adobe Campaign。 请联系Adobe Campaign以协调不同服务器之间的迁移。
* 对于&#x200B;**Power Booster或Power Cluster平台**，迁移步骤如下：

   1. 迁移重定向和跟踪服务器(Apache / IIS)。
   1. 迁移Power Booster/Cluster服务器
   1. 迁移营销服务器。

## 用户密码 {#user-passwords}

在v7中，**内部**&#x200B;和&#x200B;**管理员**&#x200B;操作员连接必须使用密码进行保护。 强烈建议在迁移&#x200B;**前，为这些帐户和所有操作员帐户分配密码**。 如果您没有为&#x200B;**内部**&#x200B;指定密码，您将无法连接。 要为&#x200B;**internal**&#x200B;分配密码，请输入以下命令：

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>对于所有跟踪服务器，**内部**&#x200B;密码必须相同。 有关详细信息，请参阅[内部标识符](../../installation/using/configuring-campaign-server.md#internal-identifier)和[权限](../../platform/using/access-management.md)部分。
