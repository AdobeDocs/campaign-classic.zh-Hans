---
product: campaign
title: 备份
description: 备份
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# 备份{#backup}

![](../../assets/v7-only.svg)

备份对于避免在计算机上出现问题（无论是物理问题还是系统问题）时丢失数据至关重要。

数据存储在两个不同的位置：

* 物理文件存储在Adobe Campaign目录中，
* 其他数据存储在数据库中。

大多数数据都在数据库中。 这表示要备份的信息的99%。

## 物理文件 {#physical-files}

文件分为几类：

* 配置文件，位于 **nl6/conf**

   这些功能可以让您快速重新配置Adobe Campaign。

* 重定向文件** nl6/var/`<instancename>`/redir**

   这些活动位于跟踪（通常称为“额面”）服务器上，并包含之前所有的促销活动重定向。 以前的营销活动仍使用这些量度。

* 日志文件： **nl6/var/`<instancename>`/log**

   这些值可用于跟踪问题。

因此，要备份的目录如下：

* nl6/conf

* nl6/var/`<instanceName>`/redir（对于每个实例）

* nl6/var/`<instanceName>`/log（可选）

* nl6/var/`<instanceName>`/relay（可选）

>[!IMPORTANT]
>
>必须备份数据库。

## 数据库 {#database}

数据库包含Adobe Campaign富客户端控制台中显示的所有信息以及所有业务线数据。

您的托管公司，特别是其数据库管理员，负责此操作。
