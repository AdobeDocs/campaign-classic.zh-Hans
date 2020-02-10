---
title: 恢复v6.02
seo-title: 恢复v6.02
description: 恢复v6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# 恢复v6.02{#restoring-v}

以下是从v7恢复v6.02的过程。

1. 恢复数据库备份并恢复它。
1. 恢复 **Neolane v6.back** 文件夹(**nl6.back** in Linux)，将其重命名为 **Neolane v6(****** nl6 in Linux)并将其恢复到其原始位置。
1. 重新配置IIS，方法是重新分配监听端口，以重新建立Adobe Campaign v6.02在IIS网站级别的集成。
1. 停止Adobe Campaign v6.1服务。
1. 重新启动IIS。
1. 重新启动Adobe Campaign v6.02服务。

