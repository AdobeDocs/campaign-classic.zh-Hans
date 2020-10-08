---
title: 配置平台
seo-title: 配置平台
description: 配置平台
seo-description: null
page-status-flag: never-activated
uuid: e6255e4b-c9c8-4ac9-9ee3-aaa4dc9e5ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 4d2e765b-750b-457f-ad55-8bd6faaa86af
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 2%

---


# 配置平台{#configuring-your-platform}

Adobe Campaignv7中的某些重大更改需要配置以确保其有效运行。 迁移前后可能需要这些参数。 本节介绍相关更改及其配置模式。

在迁移期间， **从模式** 定义重建NmsRecipient表。 在Adobe Campaign之外对此表的SQL结构所做的任何更改都将丢失。

要检查的元素示例：

* 如果已将列（或索引）添加到 **NmsRecipient** 表中，但您尚未在模式中详细说明，则不会保存该列。
* 默认 **情况下** ，表空间属性会返回其值，即部署向导中定义的值。
* 如果已将引用视图添加到NmsRecipient表，则必须在迁移之前删除它。

此警告还与Oracle用户有关：如果在postupgrade中添 **加了usetimestamptz:1** 选项(请参阅时区 [)](../../migration/using/general-configurations.md#time-zones)，则将重新构建至少包含一个date+ **time字段的所有表** 。

## 迁移前 {#before-the-migration}

迁移到Adobe Campaignv7时，必须配置以下元素。 在开始播放之前，必须解决这 **些元素**。

* 时区

   在从v5.11平台迁移期间，必须指定在配置升级期间要使用的时区。

   如果要使用“多时区”模式，请参阅“时 [区”部分](../../migration/using/general-configurations.md#time-zones) 。

   如果将Oracle用作数据库，请检查Oracle时区文件是否已在应用程序服务器和数据库服务器之间正确同步。 For more on this, refer to the [Oracle](../../migration/using/general-configurations.md#oracle) section.

* 安全区

   出于安全原因，Adobe Campaign平台在默认情况下不再可访问：您必须配置安全区域，这要求在迁移之前收集用户IP地址。

   For more information, refer to the [Security](../../migration/using/general-configurations.md#security) section.

* 语法

   由于使用了新的解释器，JavaScript中的某些语法可能在版本5.11和6.02中被接受，在v7版本中不再被接受。 For more information, refer to the [JavaScript](../../migration/using/general-configurations.md#javascript) section.

   同样，在Adobe Campaignv7中引入了新语法以替换基于SQLData的语法。 如果将此语法使用代码元素，则必须调整它们。 For more information, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* 密码

   您必须配置管 **理员** 和 **内部** 密码。 For more information, refer to the [User passwords](../../migration/using/before-starting-migration.md#user-passwords) section.

* 树结构

   如果从v5.11平台迁移，则必须根据v6规范重新组织树结构文件夹Adobe Campaign。 有关详细信息，请参 [阅Adobe Campaignv7树结构部分](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) 。

* 互动

   如果您使 **用Interaction**，则必须删除v7中不再存在的所有6.02模式引用。 For more information, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

## 迁移后 {#after-the-migration}

运行 **Postupgrade**&#x200B;后，必须考虑以下元素并执行相应的配置。

* 镜像页面

   镜像页面个性化块已随v6.x而更改。此新版本可在访问这些页面时提高安全性。

   如果您在邮件中使用v5个性化块，镜像页面显示将失败。 Adobe强烈建议在消息中插入镜像页面时使用新的个性化块。

   但是，作为临时解决方案(并且镜像页面仍然有效)，您可以返回旧的个性化块，通过更改选项并将其设置为来避免 **[!UICONTROL XtkAcceptOldPasswords]** 此问题 **[!UICONTROL 1]**。 这不会影响新v6.x个性化块的使用。

* 语法

   如果遇到任何与语法相关的错误，在播放过程中，必须临时激 **活serverConf.xml文** 件中的allowSQLInjeption **** 选项，因为这给您重写代码的时间。 修改代码后，请务必重新激活安全性。 For more on this, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* 冲突

   迁移是通过程序升级执行的，冲突可能会在报表、表单或Web应用程序中出现。 这些冲突可以通过控制台解决。

   请参阅 [冲突](../../migration/using/general-configurations.md#conflicts) 部分。

* Tomcat

   如果自定义了安装文件夹，请确保在迁移后检查它是否正确更新。 有关更多详细信息，请参 [阅Tomcat](../../migration/using/general-configurations.md#tomcat) 部分。

* 报告

   现成的所有报告当前都使用v6.x渲染引擎。 如果已将JavaScript代码添加到报表中，某些元素可能会被更改。

   请参阅 [报告](../../migration/using/general-configurations.md#reports) 部分。

* Web 应用程序

   配置升级后，如果连接到已识别的Web 应用程序时出现任何问题，则必须在 **serverConf.xml文件中激活****allowUserPassword****和sessionTokenOnly** 选项。 请记住，然后取消激活这两个选项。 有关详细信息，请参阅“已识 [别的Web应用程序](../../migration/using/general-configurations.md#identified-web-applications) ”部分。

   根据Web 应用程序的类型及其配置，您必须执行其他操作以确保它们正常工作。

   请参阅 [Web 应用程序](../../migration/using/general-configurations.md#web-applications) 部分。

   如果从v5.11平台迁移，则必须执行其他配置：有关详细信息，请参阅 [Web 应用程序](../../migration/using/specific-configurations-in-v5-11.md#web-applications) 部分。

* 安全区。

   启动服务器之前，必须配置安全区域。 有关详细信息，请参 [阅此部分](../../installation/using/configuring-campaign-server.md#defining-security-zones) ，以及 [安全性](../../migration/using/general-configurations.md#security) 部分。

* 模式

   在Red Hat中，编辑某些模式时可能会遇到错误。 For more on this, refer to the [Red-Hat](../../migration/using/general-configurations.md#red-hat) section.

* 工作流

   如果从v5.11平台迁移，则必须控制工作流运行时目录。 For more on this, refer to the [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) section.

* 跟踪

   如果从v5.11平台迁移，则必须配置跟踪模式。 For more on this, refer to the [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) section.

* 主页

   如果从v6.02平台迁移，您可以定义其他参数以将旧主页从v6.02迁移。有关详细信息，请参阅“用户友好 [性：主页和导航](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) 部分。

* 互动

   如果您使 **用Interaction**，则必须在迁移后调整任何参数。 For more on this, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

