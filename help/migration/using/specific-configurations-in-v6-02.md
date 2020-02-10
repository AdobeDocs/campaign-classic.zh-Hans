---
title: v6.02中的特定配置
seo-title: v6.02中的特定配置
description: v6.02中的特定配置
seo-description: null
page-status-flag: never-activated
uuid: ea072af3-fdc1-4828-ad13-d4327de1eaf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: 87a6cbda-54a6-4dae-8224-e06dc217f4fc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# v6.02中的特定配置{#specific-configurations-in-v6-02}

下节详细介绍了从v6.02迁移时需要的其他配置。您还应配置“常规配置”部分中详细 [的设置](../../migration/using/general-configurations.md) 。

## Web应用程序 {#web-applications}

如果您是从v6.02迁移的，则可能会显示有关概述类型Web应用程序的错误日志。 错误消息示例：

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

这些Web应用程序使用SQLData，并且由于安全性增强而与v7不兼容。 这些错误将导致迁移失败。

如果未使用这些Web应用程序，请运行以下清理脚本并重新运行该配置：

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

如果您修改了这些Web应用程序并希望在v7中继续使用它们，则必须在不同的安全区域中激活 **allowSQLInjeption** 选项并重新启动配置。 有关详细 [信息](../../migration/using/general-configurations.md#sqldata) ，请参阅SQLData部分。

## 用户友好：主页和导航 {#user-friendliness--home-page-and-navigation}

>[!CAUTION]
>
>如果要继续使用v6.02概述类型的Web应用程序，则必须在播放升级之前，在不同的安全区域中激活 **allowSQLInjeption** 选项。 请参阅 [Web应用程序](#web-applications)。

从版本6.02迁移后，Adobe Campaign v6.02主页不再显示，但仍可访问，并且与Adobe Campaign v7兼容。

要继续使用v6.02主页，必须在迁移后安装“兼容性”包。

为此，请导入兼容性包：

单 **[!UICONTROL Tools > Advanced > Import package]** 击并在 **中选择campaignMigration.xml** 包 **`\nl\datakit\nms\[Your language]\package\optional`**。

要允许访问v6.02 web应用程序类型接口，必须在serverConf.xml文件中激活 **sessionTokenOnly** **** server配置选项：

```
sessionTokenOnly="true"
```

此选项可更改安全级别，以确保界面兼容性。

安装包后，Adobe Campaign v7主页将替换为旧版v6.02主页，该主页包含v7（蓝色主页横幅）中的常规配置。

![](assets/dashboards.png)

此主页上的所有链接都链接到v7屏幕，但列表(**[!UICONTROL operation list]**、 **[!UICONTROL delivery tracking in operations]**&#x200B;等)除外链接到v6.02概述（Web应用程序）。

![](assets/dashboards2.png)

如果要添加v6.02中配置的其他概述，您需要从功能板将其添加到主页。(**[!UICONTROL Administration > Access management > Dashboard]**)。

>[!NOTE]
>
>请记住断开连接，然后重新连接控制台以注册修改。

## 消息中心 {#message-center}

在消息中心控制实例迁移后，您必须重新发布交易消息模板以使其正常工作。

在v7中，执行实例上的事务消息模板的名称已更改。 它们当前由操作符名前缀，该名称对应于创建它们的控件实例，例如 **control1_template1_rt** (其中 **control1** 是操作符的名称)。 如果您有大量模板，我们建议在控件实例上删除旧模板。
