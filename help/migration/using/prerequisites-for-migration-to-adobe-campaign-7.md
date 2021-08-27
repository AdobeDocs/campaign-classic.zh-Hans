---
product: campaign
title: 迁移到 Adobe Campaign 7 的先决条件
description: 迁移到 Adobe Campaign 7 的先决条件
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# 迁移到 Adobe Campaign 7 的先决条件{#prerequisites-for-migration-to-adobe-campaign}

![](../../assets/v7-only.svg)

在运行任何迁移之前，请参阅[开始迁移之前](../../migration/using/before-starting-migration.md)和[配置平台](../../migration/using/configuring-your-platform.md)部分。

从v6.02迁移到Adobe Campaign v7时，某些事先交付的文件将不会交付。

如果出现客户端错误，您必须使用新的Adobe Campaign v7代码更新功能板，或手动将以下文件从v6.02实例复制到v7实例：

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
