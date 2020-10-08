---
title: 恢复 v6.02
seo-title: 恢复 v6.02
description: 恢复 v6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 9%

---


# 恢复 v6.02{#restoring-v}

以下是从v7恢复v6.02的过程。

1. 恢复数据库备份并恢复它。
1. 恢复 **Neolane v6.back文件夹** (**Linux中为nl6.back** )，将其重命名为Neolane v6 **（Linux中为nl6）,****** 并将其恢复到其原始位置。
1. 重新配置IIS，方法是重新分配侦听端口，以重新建立IIS网站级别Adobe Campaignv6.02的集成。
1. 停止Adobe Campaignv6.1服务。
1. 重新开始IIS。
1. 重新启动Adobe Campaignv6.02服务。

