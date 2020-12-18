---
solution: Campaign Classic
product: campaign
title: 迁移到 Adobe Campaign 7 的先决条件
description: 迁移到 Adobe Campaign 7 的先决条件
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 迁移到 Adobe Campaign 7 的先决条件{#prerequisites-for-migration-to-adobe-campaign}

运行任何迁移之前，请参阅[开始迁移之前的](../../migration/using/before-starting-migration.md)和[配置平台](../../migration/using/configuring-your-platform.md)部分。

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
