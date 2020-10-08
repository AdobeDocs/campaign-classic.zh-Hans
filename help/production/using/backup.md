---
title: 备份
seo-title: 备份
description: 备份
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---


# 备份{#backup}

备份是避免在计算机上出现问题（无论是物理问题还是与系统相关）的事件中丢失数据的关键。

数据存储在两个不同的位置：

* 物理文件存储在Adobe Campaign目录中，
* 其他数据存储在数据库中。

大多数数据都在数据库中。 这表示要备份的信息的99%。

## 物理文件 {#physical-files}

文件分为几个类别:

* 配置文件，位 **于nl6/conf中**

   这使您能够快速地重新配置Adobe Campaign。

* 重定向文件** nl6/var/`<instancename>`/redir**

   这些服务器位于跟踪（通常称为“额面”）服务器上，并包含所有以前的活动重定向。 它们仍然被以前的活动使用。

* 日志文件： **nl6/var/`<instancename>`log**

   这些可用于跟踪问题。

因此，要备份的目录有：

* nl6/conf

* nl6/var/`<instanceName>`/redir（对于每个实例）

* nl6/var/`<instanceName>`/log（可选）

* nl6/var/`<instanceName>`/relay（可选）

>[!CAUTION]
>
>备份数据库至关重要。

## 数据库 {#database}

Adobe Campaign库包含在富客户端控制台中显示的所有信息以及所有业务线数据。

您的托管公司，特别是其数据库管理员，负责此操作。
