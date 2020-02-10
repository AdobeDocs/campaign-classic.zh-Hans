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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# 备份{#backup}

备份是避免在计算机上出现问题（无论是物理问题还是系统问题）时丢失数据的必备工具。

数据存储在两个不同的位置：

* 物理文件存储在Adobe Campaign目录中，
* 其他数据存储在数据库中。

大多数数据都在数据库中。 这表示要备份的信息的99%。

## 物理文件 {#physical-files}

文件分为几类：

* 配置文件，位 **于nl6/conf中**

   这些组件使您能够快速重新配置Adobe Campaign。

* 重定向文件** nl6/var/`<instancename>`/redir**

   这些服务器位于跟踪（通常称为“额面”）服务器上，并包含所有以前的营销活动重定向。 以前的营销活动仍使用它们。

* 日志文件： **nl6/var/`<instancename>`/log**

   这些可用于跟踪问题。

因此，要备份的目录包括：

* nl6/conf

* nl6/var/`<instanceName>`/redir（对于每个实例）

* nl6/var/`<instanceName>`/log（可选）

* nl6/var/`<instanceName>`/relay（可选）

>[!CAUTION]
>
>备份数据库至关重要。

## 数据库 {#database}

数据库包含Adobe Campaign富客户端控制台中显示的所有信息以及所有业务线数据。

您的托管公司及其数据库管理员负责此操作。
