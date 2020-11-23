---
solution: Campaign Classic
product: campaign
title: v6.02 中的特定配置
description: v6.02 中的特定配置
audience: migration
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---


# v6.02 中的特定配置{#specific-configurations-in-v6-02}

以下部分详细介绍了从v6.02迁移时需要的其他配置。您还应配置“常规配置”部分中详 [细介绍的](../../migration/using/general-configurations.md) 设置。

## Web 应用程序 {#web-applications}

如果您是从v6.02迁移，则可能显示有关概述类型Web应用程序的错误日志。 错误消息示例：

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

这些Web应用程序使用SQLData，并且由于安全性的提高而与v7不兼容。 这些错误将导致迁移失败。

如果您未使用这些Web应用程序，请运行以下清理脚本并重新运行配置：

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

如果您修改了这些Web应用程序并希望在v7中继续使用它们，则必须在不同的安全 **区域中激活** allowSQLInjeption选项并重新开始配置。 有关此的 [详细信息](../../migration/using/general-configurations.md#sqldata) ，请参阅SQLData部分。

## 用户友好：主页和导航 {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>如果要继续使用v6.02概述类型的Web应用程序，则必须在播放前在不同 **安全区域中激活** allowSQLInjeption选项。 请参阅 [Web 应用程序](#web-applications)。

从版本6.02迁移后，Adobe Campaignv6.02主页不再显示，但仍可访问并与Adobe Campaignv7兼容。

要继续使用v6.02主页，迁移后必须安装“兼容”包。

为此，请导入兼容性包：

单 **[!UICONTROL Tools > Advanced > Import package]** 击并在 **中选择campaignMigration** .xml包 **`\nl\datakit\nms\[Your language]\package\optional`**。

要允许访问v6.02Web 应用程序类型接口，必须在 **serverConf.xml文件中激活** sessionTokenOnly服 **务器配置选项** :

```
sessionTokenOnly="true"
```

此选项可更改安全级别以确保接口兼容性。

安装包后，Adobe Campaignv7主页将替换为旧版v6.02主页，并配以v7(蓝色主页横幅)中的常规配置。

![](assets/dashboards.png)

此主页上的所有链接都链接到v7屏幕，列表&#x200B;**[!UICONTROL operation list]**( **[!UICONTROL delivery tracking in operations]**&#x200B;等)除外 链接到v6.02概述（web应用程序）。

![](assets/dashboards2.png)

如果要添加v6.02中配置的其他概述，您需要从仪表板将此概述添加到主页。(**[!UICONTROL Administration > Access management > Dashboard]**)。

>[!NOTE]
>
>请记住断开连接，然后重新连接控制台以注册修改。

## 消息中心 {#message-center}

在消息中心控制实例迁移后，必须重新发布事务性消息模板才能使其正常工作。

在v7中，执行实例的事务性消息模板名称已更改。 它们当前由与创建它们的控制实例对应的运算符名称前缀，例如 **control1_template1_rt** ( **其中control1** 是运算符的名称)。 如果您有大量模板，我们建议在控制实例上删除旧模板。
