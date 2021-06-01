---
product: campaign
title: 回滚到以前的版本
description: 了解如何回滚到以前的版本
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# 回滚到以前的版本{#about-rollback}

迁移后，如果出现问题，您可能需要回退到Campaign的先前版本。

回滚过程取决于您的Campaign初始版本。

## 恢复 v6.1

以下是从v7恢复v6.1的过程。

1. 恢复数据库的备份并恢复它。
1. 恢复&#x200B;**Adobe Campaign v6.back**&#x200B;文件夹（在Linux中为&#x200B;**nl6.back**），将其重命名为&#x200B;**Adobe Campaign v6**（在Linux中为&#x200B;**nl6**），然后将其还原到其原始位置。
1. 通过重新分配侦听端口来重新配置IIS，以在IIS网站级别重新建立Adobe Campaign v6.1的集成。
1. 停止Adobe Campaign v7服务。
1. 重新启动IIS。
1. 重新启动Adobe Campaign v6.1服务。

## 恢复到Campaign v6.02

以下是从v7恢复v6.02的过程。

1. 恢复数据库的备份并恢复它。
1. 恢复&#x200B;**Neolane v6.back**&#x200B;文件夹（在Linux中为&#x200B;**nl6.back**），将其重命名为&#x200B;**Neolane v6**（在Linux中为&#x200B;**nl6**），然后将其还原到其原始位置。
1. 通过重新分配侦听端口来重新配置IIS，以在IIS网站级别重新建立Adobe Campaign v6.02的集成。
1. 停止Adobe Campaign v6.1服务。
1. 重新启动IIS。
1. 重新启动Adobe Campaign v6.02服务。

## 恢复到Campaign v5.11

以下是从v7恢复v5.11的步骤。

1. 恢复数据库的备份并恢复它。
1. 恢复&#x200B;**Neolane v5.back**&#x200B;文件夹（在Linux中为&#x200B;**nl5.back**），将其重命名为&#x200B;**Neolane v5**（在Linux中为&#x200B;**nl5**），然后将其还原到其原始位置。
1. 通过重新分配侦听端口来重新配置IIS，以在IIS网站级别重新建立Neolane v5的集成。
1. 停止Adobe Campaign v7服务。
1. 重新启动IIS。
1. 重新启动Adobe Campaign v5服务。
