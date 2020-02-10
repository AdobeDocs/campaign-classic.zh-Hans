---
title: 恢复v5.11
seo-title: 恢复v5.11
description: 恢复v5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# 恢复v5.11{#restoring-v}

以下是从v7恢复v5.11的过程。

1. 恢复数据库备份并恢复它。
1. 恢复 **Neolane v5.back** (**nl5.back** in Linux)文件夹，将其重命名为 **Neolane v5** (**** nl5 in Linux)，并将其恢复到其原始位置。
1. 重新配置IIS，方法是重新分配监听端口，以重新建立Neolane v5在IIS网站级别的集成。
1. 停止Adobe Campaign v7服务。
1. 重新启动IIS。
1. 重新启动Adobe Campaign v5服务。

