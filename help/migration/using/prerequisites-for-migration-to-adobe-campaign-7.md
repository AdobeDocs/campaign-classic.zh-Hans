---
title: 迁移到Adobe Campaign 7的先决条件
seo-title: 迁移到Adobe Campaign 7的先决条件
description: 迁移到Adobe Campaign 7的先决条件
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# 迁移到Adobe Campaign 7的先决条件{#prerequisites-for-migration-to-adobe-campaign}

在运行任何迁移之前，请参阅 [开始迁移](../../migration/using/before-starting-migration.md) , [并配置平台部分](../../migration/using/configuring-your-platform.md) 。

从v6.02迁移到Adobe Campaign v7时，某些预先交付的文件不会交付。

如果出现客户端错误，您必须使用新的Adobe Campaign v7代码更新您的仪表板，或手动将以下文件从v6.02实例复制到v7实例：

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
