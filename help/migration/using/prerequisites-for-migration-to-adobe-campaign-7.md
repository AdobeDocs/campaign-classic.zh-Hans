---
title: 迁移到 Adobe Campaign 7 的先决条件
seo-title: 迁移到 Adobe Campaign 7 的先决条件
description: 迁移到 Adobe Campaign 7 的先决条件
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 27%

---


# 迁移到 Adobe Campaign 7 的先决条件{#prerequisites-for-migration-to-adobe-campaign}

在运行任何迁移之前，请参 [阅开始迁移](../../migration/using/before-starting-migration.md)[和配置平台部分](../../migration/using/configuring-your-platform.md) 。

从v6.02迁移到Adobe Campaignv7时，某些预先交付的文件将无法交付。

如果出现客户端错误，您必须使用新的仪表板v7代码更新Adobe Campaign，或者手动将以下文件从v6.02实例复制到v7实例：

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
