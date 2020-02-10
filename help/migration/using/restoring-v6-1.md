---
title: 恢复v6.1
seo-title: 恢复v6.1
description: 恢复v6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# 恢复v6.1{#restoring-v}

以下是从v7恢复v6.1的过程。

1. 恢复数据库备份并恢复它。
1. 恢复 **Adobe Campaign v6.back** (**nl6.back** in Linux)文件夹，将其重命名为 **Adobe Campaign v6(****** nl6 in Linux)，并将其恢复到其原始位置。
1. 重新配置IIS，方法是重新分配监听端口，以重新建立IIS网站级别的Adobe Campaign v6.1集成。
1. 停止Adobe Campaign v7服务。
1. 重新启动IIS。
1. 重新启动Adobe Campaign v6.1服务。

