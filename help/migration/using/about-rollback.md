---
solution: Campaign Classic
product: campaign
title: 回滚到先前版本
description: 了解如何回滚到先前版本
audience: migration
content-type: reference
topic-tags: rollback
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# 回滚到先前版本{#about-rollback}

迁移后，在出现问题时，可能需要回滚到以前版本的活动。

回滚过程取决于初始版本的活动。

## 恢复 v6.1

以下是从v7恢复v6.1的过程。

1. 恢复数据库备份并恢复它。
1. 恢复&#x200B;**Adobe Campaignv6.back**&#x200B;文件夹（Linux中为&#x200B;**nl6.back**），将其重命名为&#x200B;**Adobe Campaignv6**（Linux中为&#x200B;**nl6**），并将其恢复到原始位置。
1. 重新配置IIS，方法是重新分配侦听端口，以重新建立IIS网站级别Adobe Campaignv6.1的集成。
1. 停止Adobe Campaignv7服务。
1. 重新开始IIS。
1. 重新启动Adobe Campaignv6.1服务。

## 恢复到活动v6.02

以下是从v7恢复v6.02的过程。

1. 恢复数据库备份并恢复它。
1. 恢复&#x200B;**Neolane v6.back**&#x200B;文件夹（Linux中为&#x200B;**nl6.back**），将其重命名为&#x200B;**Neolane v6**（Linux中为&#x200B;**nl6**），并将其恢复到其原始位置。
1. 重新配置IIS，方法是重新分配侦听端口，以重新建立IIS网站级别Adobe Campaignv6.02的集成。
1. 停止Adobe Campaignv6.1服务。
1. 重新开始IIS。
1. 重新启动Adobe Campaignv6.02服务。

## 恢复到活动v5.11

以下是从v7恢复v5.11的过程。

1. 恢复数据库备份并恢复它。
1. 恢复&#x200B;**Neolane v5.back**&#x200B;文件夹（Linux中为&#x200B;**nl5.back**），将其重命名为&#x200B;**Neolane v5**（Linux中为&#x200B;**nl5**），并将其恢复到其原始位置。
1. 重新配置IIS，方法是重新分配侦听端口，以重新建立Neolane v5在IIS网站级别的集成。
1. 停止Adobe Campaignv7服务。
1. 重新开始IIS。
1. 重新开始Adobe Campaignv5服务。
