---
title: 配置原理
seo-title: 配置原理
description: 配置原理
seo-description: null
page-status-flag: never-activated
uuid: 6315d526-b820-46ab-96c7-e64e101c6a7d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: d08ff769-da93-4f86-8802-f0fb5b051ece
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 5%

---


# 配置原理{#configuration-principle}

Adobe Campaign平台基于实例的概念，类似于Apache使用的虚拟主机。 此操作模式允许您通过为服务器分配多个实例来共享服务器。 实例完全相互独立，并使用它们自己的数据库和配置文件来操作。

对于给定服务器，有两个元素是所有Adobe Campaign实例通用的：

* 内部 **密码** :这是一般管理员密码。 它对特定应用程序服务器的所有实例都是通用的。

   >[!CAUTION]
   >
   >要使用内部标 **识** 符登录，您需要事先定义密码。 如需详细信息，请参阅[此部分](../../installation/using/campaign-server-configuration.md#internal-identifier)。

* 多种技术服务器配置：这些配置都可以在实例的特定配置中过载。

配置文件保存在安 **装目** 录的conf目录中。 配置分为三个文件：

* **serverConf.xml**:所有实例的整体配置。
* **config-**`<instance>`**.xml** (其中 **`<instance>`** 是实例名称):实例的特定配置。
* **serverConf.xml.diff**:在初始配置和当前配置之间进行增量。 此文件由应用程序自动生成，不得手动修改。 它用于在更新构建版本时自动传播用户修改。

实例配置按如下方式加载：

* 该模块加载 **serverConf.xml文件** ，以获取所有实例共享的参数。
* 然后加载 **config-**`<instance>`**.xml** 文件。 此文件中的值优先于serverConf.xml中 **包含的值**。

   这两个文件的格式相同。 serverConf.xml **中的任何值** ，都可以为config-xml文件中的 **给定实例`<instance>`重载** 。

此操作模式为配置提供了极大的灵活性。
