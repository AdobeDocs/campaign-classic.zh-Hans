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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# 配置平台{#configuring-your-platform}

Adobe Campaign v7中的某些重大更改需要配置以确保其有效运行。 迁移前后可能需要这些参数。 本节介绍了相关更改及其配置模式。

在迁移期间， **从架构定义重建NmsRecipient** 表。 在Adobe Campaign之外对此表的SQL结构所做的任何更改都将丢失。

要检查的元素示例：

* 如果已将列（或索引）添加到 **NmsRecipient** 表，但您尚未在架构中详细描述该列（或索引），则不会保存该列。
* 默认 **情况下** ，表空间属性会返回其值，即部署向导中定义的值。
* 如果已将引用视图添加到NmsRecipient表，则必须在迁移之前删除它。

此警告还与Oracle用户有关：如果在播放过程中 **添加了usetimestamptz:1** (请参阅时区 [](../../migration/using/general-configurations.md#time-zones))选项，则将重新构建包含至少一个date+time字段的 **** 所有表。

## 迁移前 {#before-the-migration}

迁移到Adobe Campaign v7时，必须配置以下元素。 必须先解决这些元素，然后才能开始 **操作**。

* 时区

   在从v5.11平台迁移期间，必须指定在配置过程中要使用的时区。

   如果要使用“多时区”模式，请参阅“时 [区”部分](../../migration/using/general-configurations.md#time-zones) 。

   如果将Oracle用作数据库，请检查Oracle时区文件是否已在应用程序服务器和数据库服务器之间正确同步。 For more on this, refer to the [Oracle](../../migration/using/general-configurations.md#oracle) section.

   此外，在从v.5.11平台迁移期间，在MySQL中，您必须执行其他配置。 有关详细信息，请参阅 [MySQL](../../migration/using/specific-configurations-in-v5-11.md#mysql) 部分。

* 安全区

   出于安全原因，Adobe Campaign平台在默认情况下不再可访问：您必须配置安全区域，这要求在迁移之前收集用户IP地址。

   有关详细信息，请参阅“安 [全](../../migration/using/general-configurations.md#security) ”部分。

* 语法

   由于使用了新的解释器，JavaScript中的某些语法可能在版本5.11和6.02中被接受，在v7版本中不再被接受。 有关详细信息，请参阅 [JavaScript](../../migration/using/general-configurations.md#javascript) 部分。

   同样，Adobe Campaign v7中引入了新的语法以替换基于SQLData的语法。 如果使用此语法使用代码元素，则必须调整它们。 有关详细信息，请参阅 [SQLData部分](../../migration/using/general-configurations.md#sqldata) 。

* 密码

   您必须配置“管 **理员** ”和“ **内部** ”密码。 有关详细信息，请参阅“用 [户密码](../../migration/using/before-starting-migration.md#user-passwords) ”部分。

* 树结构

   如果从v5.11平台迁移，则必须根据Adobe Campaign v6规范重新组织树结构文件夹。 有关详细信息，请参阅 [Adobe Campaign v7树结构部分](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) 。

* 交互

   如果使用 **交互**，则必须删除v7中不再存在的所有6.02架构引用。 有关详细信息，请参阅“交 [互](../../migration/using/general-configurations.md#interaction) ”部分。

## 迁移后 {#after-the-migration}

运行 **配置后**，必须考虑以下元素并执行相应的配置。

* 镜像页面

   镜像页面个性化块已随v6.x而更改。此新版本提高了访问这些页面时的安全性。

   如果您在消息中使用了v5个性化块，则镜像页面显示将失败。 Adobe强烈建议在消息中插入镜像页面时使用新的个性化块。

   但是，作为临时解决方案（由于镜像页面仍处于实时状态），您可以通过更改选项并将其设置为，返回旧的个性化块以避免 **[!UICONTROL XtkAcceptOldPasswords]** 出现此问题 **[!UICONTROL 1]**。 这不会影响新v6.x个性化块的使用。

* 语法

   如果遇到与语法相关的任何错误，在播放过程中，必须临时激活 **serverConf.xml文件中的** allowSQLInjeption **** 选项，因为这给您重写代码的时间。 修改代码后，请务必重新激活安全性。 For more on this, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* 冲突

   迁移通过配置程序执行，并且冲突可能会出现在报告、表单或Web应用程序中。 这些冲突可以从控制台中解决。

   请参阅 [冲突](../../migration/using/general-configurations.md#conflicts) 。

* Tomcat

   如果自定义了安装文件夹，请确保检查该文件夹在迁移后是否正确更新。 有关更多详细信息，请参阅 [Tomcat](../../migration/using/general-configurations.md#tomcat) 部分。

* 报告

   所有现成报告当前都使用v6.x渲染引擎。 如果已将JavaScript代码添加到报告中，某些元素可能会被更改。

   请参阅“ [报告](../../migration/using/general-configurations.md#reports) ”部分。

* Web应用程序

   配置升级后，如果连接到已识别的Web应用程序时遇到任何问题，则必须在 **serverConf.xml文件中激活** allowUserPassword **** 和sessionTokenOnly **** 选项。 记住，然后取消激活这两个选项。 有关详细信息，请参阅“已识 [别的Web应用程序](../../migration/using/general-configurations.md#identified-web-applications) ”部分。

   根据Web应用程序的类型及其配置，您必须执行其他操作以确保它们能够正常工作。

   请参阅 [Web应用程序部分](../../migration/using/general-configurations.md#web-applications) 。

   如果从v5.11平台迁移，则必须执行其他配置：有关详细信息，请参阅 [Web应用程序部分](../../migration/using/specific-configurations-in-v5-11.md#web-applications) 。

* 安全区。

   在启动服务器之前，必须配置安全区域。 有关详细信息，请参 [阅本节](../../installation/using/configuring-campaign-server.md#defining-security-zones) 和安 [全部](../../migration/using/general-configurations.md#security) 。

* 架构

   在Red hat中，编辑某些架构时可能会遇到错误。 For more on this, refer to the [Red-Hat](../../migration/using/general-configurations.md#red-hat) section.

* 工作流

   如果从v5.11平台迁移，则必须控制工作流运行时目录。 For more on this, refer to the [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) section.

* 跟踪

   如果从v5.11平台迁移，则必须配置跟踪模式。 For more on this, refer to the [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) section.

* 主页

   如果从v6.02平台迁移，您可以定义其他参数以保留旧主页从v6.02。有关详细信息，请参阅“用户友好 [性：主页和导航部分](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) 。

* 交互

   如果您使用 **Interaction**，则必须在迁移后调整任何参数。 For more on this, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

