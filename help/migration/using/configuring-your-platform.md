---
product: campaign
title: 配置平台
description: 配置平台
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---

# 配置平台{#configuring-your-platform}

Adobe Campaign v7中的某些主要更改需要配置以确保其有效运行。 在迁移之前或之后，可能需要使用这些参数。 本节将介绍相关更改及其配置模式。

在迁移期间，将根据模式定义重建&#x200B;**NmsRecipient**&#x200B;表。 对此表的SQL结构在Adobe Campaign外所做的任何更改都将丢失。

要检查的元素示例：

* 如果您在&#x200B;**NmsRecipient**&#x200B;表中添加了列（或索引），但您尚未在架构中详细说明该列，则不会保存该列。
* 默认情况下， **表空间**&#x200B;属性会返回其值，即部署向导中定义的值。
* 如果已向NmsRecipient表添加了引用视图，则必须在迁移前将其删除。

此警告还涉及Oracle用户：如果您在后期升级期间添加了&#x200B;**usetimestamptz:1**&#x200B;选项（请参阅[时区](../../migration/using/general-configurations.md#time-zones)），则将重建至少包含一个&#x200B;**date+time**&#x200B;字段的所有表。

## 迁移{#before-the-migration}之前

迁移到Adobe Campaign v7时，必须配置以下元素。 必须先解决这些元素，然后才能启动&#x200B;**postupgrade**。

* 时区

   从v5.11平台迁移期间，您必须指定在升级后期间使用的时区。

   如果要使用“多时区”模式，请参阅[时区](../../migration/using/general-configurations.md#time-zones)一节。

   如果将Oracle用作数据库，请检查Oracle时区文件是否已在应用程序服务器和数据库服务器之间正确同步。 有关更多信息，请参阅[Oracle](../../migration/using/general-configurations.md#oracle)一节。

* 安全区

   出于安全考虑，Adobe Campaign平台默认不再可访问：您必须配置安全区，这要求在迁移之前收集用户IP地址。

   有关更多信息，请参阅[Security](../../migration/using/general-configurations.md#security)一节。

* 语法

   由于使用了新的解释器，JavaScript中的某些语法可能会在版本5.11和6.02中接受，而在v7版本中则不再接受。 有关更多信息，请参阅[JavaScript](../../migration/using/general-configurations.md#javascript)一节。

   同样，Adobe Campaign v7中引入了新语法来替换基于SQLData的语法。 如果将代码元素与此语法一起使用，则必须调整它们。 有关更多信息，请参阅[SQLData](../../migration/using/general-configurations.md#sqldata)一节。

* 密码

   必须配置&#x200B;**Admin**&#x200B;和&#x200B;**内部**&#x200B;密码。 有关更多信息，请参阅[用户密码](../../migration/using/before-starting-migration.md#user-passwords)一节。

* 树结构

   如果从v5.11平台迁移，则必须根据Adobe Campaign v6规范重新组织树结构文件夹。 有关更多信息，请参阅[Adobe Campaign v7树结构](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure)一节。

* 互动

   如果您使用&#x200B;**Interaction**，则必须删除v7中不再存在的所有6.02架构引用。 有关更多信息，请参阅[Interaction](../../migration/using/general-configurations.md#interaction)一节。

## 迁移{#after-the-migration}后

运行&#x200B;**postupgrade**&#x200B;后，必须考虑以下元素并执行相应的配置。

* 镜像页面

   镜像页面个性化块已随v6.x发生更改。此新版本可提高访问这些页面时的安全性。

   如果在消息中使用v5个性化块，则镜像页面显示将失败。 Adobe强烈建议在消息中插入镜像页面时使用新的个性化块。

   但是，作为临时解决方案（以及由于镜像页面仍处于实时状态），您可以返回到旧的个性化块，通过更改选项&#x200B;**[!UICONTROL XtkAcceptOldPasswords]**&#x200B;并将其设置为&#x200B;**[!UICONTROL 1]**&#x200B;来避免此问题。 这不会影响新v6.x个性化块的使用。

* 语法

   如果遇到与语法相关的任何错误，在升级后期间，必须临时激活&#x200B;**serverConf.xml**&#x200B;文件中的&#x200B;**allowSQLIncompent**&#x200B;选项，因为这样您就有时间重写代码。 修改代码后，请务必重新激活安全性。 有关更多信息，请参阅[SQLData](../../migration/using/general-configurations.md#sqldata)一节。

* 冲突

   迁移是通过升级后执行的，冲突可能会显示在报表、表单或Web应用程序中。 这些冲突可以从控制台中解决。

   请参阅[Conflicts](../../migration/using/general-configurations.md#conflicts)部分。

* Tomcat

   如果您自定义了安装文件夹，请确保检查迁移后文件夹是否正确更新。 有关更多详细信息，请参阅[Tomcat](../../migration/using/general-configurations.md#tomcat)一节。

* 报告

   当前所有现成的报表都使用v6.x渲染引擎。 如果已将JavaScript代码添加到报表中，则某些元素可能会发生更改。

   请参阅[Reports](../../migration/using/general-configurations.md#reports)一节。

* Web应用程序

   在升级后，如果在连接到已识别的Web应用程序时遇到任何问题，则必须激活&#x200B;**serverConf.xml**&#x200B;文件中的&#x200B;**allowUserPassword**&#x200B;和&#x200B;**sessionTokenOnly**&#x200B;选项。 请记住，然后取消激活这两个选项。 有关更多信息，请参阅[已识别的Web应用程序](../../migration/using/general-configurations.md#identified-web-applications)一节。

   根据Web应用程序的类型及其配置，必须执行其他操作以确保它们正常工作。

   请参阅[Web应用程序](../../migration/using/general-configurations.md#web-applications)部分。

   如果从v5.11平台迁移，则必须执行其他配置：有关更多信息，请参阅[Web应用程序](../../migration/using/specific-configurations-in-v5-11.md#web-applications)一节。

* 安全区。

   启动服务器之前，必须配置安全区。 有关更多信息，请参阅[此部分](../../installation/using/security-zones.md)和[安全](../../migration/using/general-configurations.md#security)部分。

* 模式

   在Red Hat中，您在编辑某些架构时可能会遇到错误。 有关更多信息，请参阅[Red-Hat](../../migration/using/general-configurations.md#red-hat)一节。

* 工作流

   如果从v5.11平台迁移，则必须控制工作流运行时目录。 有关更多信息，请参阅[工作流](../../migration/using/specific-configurations-in-v5-11.md#workflows)一节。

* 跟踪

   如果从v5.11平台迁移，则必须配置跟踪模式。 有关更多信息，请参阅[跟踪](../../migration/using/specific-configurations-in-v5-11.md#tracking)一节。

* 主页

   如果从v6.02平台迁移，您可以定义其他参数以保留旧主页从v6.02。有关更多信息，请参阅[用户友好：主页和导航](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation)部分。

* 互动

   如果您使用&#x200B;**Interaction**，则必须在迁移后调整任何参数。 有关更多信息，请参阅[Interaction](../../migration/using/general-configurations.md#interaction)一节。
