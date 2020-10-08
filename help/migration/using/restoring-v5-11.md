---
title: 恢复 v5.11
seo-title: 恢复 v5.11
description: 恢复 v5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 9%

---


# 恢复 v5.11{#restoring-v}

以下是从v7恢复v5.11的过程。

1. 恢复数据库备份并恢复它。
1. 恢复 **Neolane v5.back文件夹** (**Linux中为nl5.back** )，将其重命名为 **Neolane v5** (Linux中为&#x200B;**** nl5)，并将其恢复到其原始位置。
1. 重新配置IIS，方法是重新分配侦听端口，以重新建立Neolane v5在IIS网站级别的集成。
1. 停止Adobe Campaignv7服务。
1. 重新开始IIS。
1. 重新开始Adobe Campaignv5服务。

