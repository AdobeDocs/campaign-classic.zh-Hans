---
solution: Campaign Classic
product: campaign
title: 配置平台
description: 配置平台
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---


# 配置平台{#configuring-your-platform}

Adobe Campaign v7中的某些重大更改需要配置以确保其有效运行。 迁移之前或之后可能需要这些参数。 本节介绍有关的更改及其配置模式。

在迁移期间，将根据模式定义重建&#x200B;**NmsRecipient**&#x200B;表。 在Adobe Campaign之外对此表的SQL结构所做的任何更改都将丢失。

要检查的元素示例：

* 如果您已在&#x200B;**NmsRecipient**&#x200B;表中添加了列（或索引），但您尚未在模式中详细说明，则不会保存该列。
* 默认情况下，**表空间**&#x200B;属性会返回其值，即部署向导中定义的值。
* 如果已将引用视图添加到NmsRecipient表，则必须在迁移之前删除它。

此警告还涉及Oracle用户：如果您在postupgrade期间添加了&#x200B;**usetimestamptz:1**&#x200B;选项（请参阅[时区](../../migration/using/general-configurations.md#time-zones)），则将重建包含至少一个&#x200B;**date+time**&#x200B;字段的所有表。

## 迁移前{#before-the-migration}

迁移到Adobe Campaign v7时，必须配置以下元素。 在启动&#x200B;**postupgrade**&#x200B;之前，必须解决这些元素。

* 时区

   在从v5.11平台迁移期间，必须指定在配置升级期间使用的时区。

   如果要使用“多时区”模式，请参阅[时区](../../migration/using/general-configurations.md#time-zones)部分。

   如果将Oracle用作数据库，请检查Oracle时区文件是否已在应用程序服务器和数据库服务器之间正确同步。 有关详细信息，请参阅[Oracle](../../migration/using/general-configurations.md#oracle)部分。

* 安全区

   出于安全原因，默认情况下不再可访问Adobe Campaign平台：您必须配置安全区域，这要求在迁移前收集用户IP地址。

   有关详细信息，请参阅[Security](../../migration/using/general-configurations.md#security)部分。

* 语法

   由于使用了新的解释器，JavaScript中的某些语法可能在版本5.11和6.02中被接受，在v7版本中不再被接受。 有关详细信息，请参阅[JavaScript](../../migration/using/general-configurations.md#javascript)部分。

   同样，Adobe Campaign v7中引入了新语法以替换基于SQLData的语法。 如果使用此语法使用代码元素，则必须调整它们。 有关详细信息，请参阅[SQLData](../../migration/using/general-configurations.md#sqldata)部分。

* 密码

   必须配置&#x200B;**Admin**&#x200B;和&#x200B;**Internal**&#x200B;密码。 有关详细信息，请参阅[用户密码](../../migration/using/before-starting-migration.md#user-passwords)部分。

* 树结构

   如果从v5.11平台迁移，则必须根据Adobe Campaign v6规范重新组织树结构文件夹。 有关详细信息，请参阅[Adobe Campaignv7树结构](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure)部分。

* 互动

   如果使用&#x200B;**Interaction**，则必须删除v7中不再存在的所有6.02模式引用。 有关详细信息，请参阅[Interaction](../../migration/using/general-configurations.md#interaction)部分。

## 迁移{#after-the-migration}后

运行&#x200B;**postupgrade**&#x200B;后，必须考虑以下元素并执行相应的配置。

* 镜像页面

   镜像页面个性化基块已随v6.x而更改。此新版本提高了访问这些页面时的安全性。

   如果您在消息中使用了v5个性化基块，镜像页面显示将失败。 Adobe强烈建议在消息中插入镜像页面时使用新的个性化块。

   但是，作为临时解决方案(并且镜像页面仍处于实时状态)，您可以通过更改选项&#x200B;**[!UICONTROL XtkAcceptOldPasswords]**&#x200B;并将其设置为&#x200B;**[!UICONTROL 1]**&#x200B;来返回旧的个性化块以避免此问题。 这不会影响新v6.x个性化基块的使用。

* 语法

   如果遇到任何与语法相关的错误，在播放过程中，必须临时激活&#x200B;**serverConf.xml**&#x200B;文件中的&#x200B;**allowSQLInjeption**&#x200B;选项，因为这给您重写代码的时间。 修改代码后，请务必重新激活安全性。 有关详细信息，请参阅[SQLData](../../migration/using/general-configurations.md#sqldata)部分。

* 冲突

   迁移是通过程序执行的，冲突可能会在报表、表单或Web应用程序中显示。 这些冲突可以从控制台中解决。

   请参阅[冲突](../../migration/using/general-configurations.md#conflicts)部分。

* Tomcat

   如果您自定义了安装文件夹，请确保在迁移后检查其是否正确更新。 有关更多详细信息，请参阅[Tomcat](../../migration/using/general-configurations.md#tomcat)部分。

* 报告

   现成的所有报表当前都使用v6.x渲染引擎。 如果已将JavaScript代码添加到报表中，某些元素可能会被更改。

   请参阅[报告](../../migration/using/general-configurations.md#reports)部分。

* Web 应用程序

   在配置升级之后，如果在连接到已识别的Web 应用程序时遇到任何问题，必须激活&#x200B;**serverConf.xml**&#x200B;文件中的&#x200B;**allowUserPassword**&#x200B;和&#x200B;**sessionTokenOnly**&#x200B;选项。 记住，然后取消激活这两个选项。 有关详细信息，请参阅[已识别的Web应用程序](../../migration/using/general-configurations.md#identified-web-applications)部分。

   根据Web 应用程序的类型及其配置，您必须执行其他操作以确保它们正常工作。

   请参阅[Web 应用程序](../../migration/using/general-configurations.md#web-applications)部分。

   如果从v5.11平台迁移，则必须执行其他配置：有关详细信息，请参阅[Web 应用程序](../../migration/using/specific-configurations-in-v5-11.md#web-applications)部分。

* 安全区。

   在启动服务器之前，必须配置安全区域。 有关详细信息，请参阅[此部分](../../installation/using/security-zones.md)和[安全](../../migration/using/general-configurations.md#security)部分。

* 模式

   在Red Hat中，编辑某些模式时可能会遇到错误。 有关详细信息，请参阅[Red-Hat](../../migration/using/general-configurations.md#red-hat)部分。

* 工作流

   如果从v5.11平台迁移，则必须控制工作流运行时目录。 有关详细信息，请参阅[工作流](../../migration/using/specific-configurations-in-v5-11.md#workflows)部分。

* 跟踪

   如果从v5.11平台迁移，则必须配置跟踪模式。 有关详细信息，请参阅[跟踪](../../migration/using/specific-configurations-in-v5-11.md#tracking)部分。

* 主页

   如果从v6.02平台迁移，您可以定义其他参数以将旧主页从v6.02保留下来。有关详细信息，请参阅[用户友好：主页和导航](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation)部分。

* 互动

   如果使用&#x200B;**Interaction**，则必须在迁移后调整任何参数。 有关详细信息，请参阅[Interaction](../../migration/using/general-configurations.md#interaction)部分。

