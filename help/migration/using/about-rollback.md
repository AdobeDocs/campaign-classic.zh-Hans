---
product: campaign
title: 回滚到以前的版本
description: 了解如何回滚到以前的版本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# 回滚到以前的版本{#about-rollback}



迁移后，如果出现问题，您可能需要回退到Campaign的先前版本。

回滚过程取决于您的Campaign初始版本。

以下是从v7恢复v6.1的过程。

1. 恢复数据库的备份并恢复它。
1. 恢复 **Adobe Campaign v6.back** 文件夹(**nl6.back** 在Linux中)，将其重命名为 **Adobe Campaign v6** (**nl6** 在Linux中)并将其还原到其原始位置。
1. 通过重新分配侦听端口来重新配置IIS，以在IIS网站级别重新建立Adobe Campaign v6.1的集成。
1. 停止Adobe Campaign v7服务。
1. 重新启动IIS。
1. 重新启动Adobe Campaign v6.1服务。

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->