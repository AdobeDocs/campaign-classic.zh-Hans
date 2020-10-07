---
title: 恢复 v6.1
seo-title: 恢复 v6.1
description: 恢复 v6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 9%

---


# 恢复 v6.1{#restoring-v}

以下是从v7恢复v6.1的过程。

1. 恢复数据库备份并恢复它。
1. 恢复 **Adobe Campaignv6.back文件夹** (**Linux中为nl6.back** )，将其重命名为 **Adobe Campaignv6** (Linux中为&#x200B;**** nl6)，并将其恢复到原始位置。
1. 重新配置IIS，方法是重新分配侦听端口，以重新建立IIS网站级别Adobe Campaignv6.1的集成。
1. 停止Adobe Campaignv7服务。
1. 重新开始IIS。
1. 重新启动Adobe Campaignv6.1服务。

