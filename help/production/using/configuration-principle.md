---
solution: Campaign Classic
product: campaign
title: 配置原理
description: 配置原理
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 配置原理{#configuration-principle}

Adobe Campaign平台基于实例的概念，类似于Apache使用的虚拟主机。 此操作模式允许您通过为服务器分配多个实例来共享服务器。 实例完全相互独立，并使用它们自己的数据库和配置文件来操作。

对于给定服务器，有两个元素是所有Adobe Campaign实例通用的：

* **internal**&#x200B;密码：这是一般管理员密码。 它对特定应用程序服务器的所有实例都是通用的。

   >[!IMPORTANT]
   >
   >要使用&#x200B;**Internal**&#x200B;标识符登录，您需要事先定义口令。 如需详细信息，请参阅[此部分](../../installation/using/campaign-server-configuration.md#internal-identifier)。

* 多种技术服务器配置：这些配置都可以在实例的特定配置中过载。

配置文件保存在安装目录的&#x200B;**conf**&#x200B;目录中。 配置分为三个文件：

* **serverConf.xml**:所有实例的整体配置。
* **config-**`<instance>`**.xml** ( **`<instance>`** 其中为实例名):实例的特定配置。
* **serverConf.xml.diff**:在初始配置和当前配置之间进行增量。此文件由应用程序自动生成，不得手动修改。 它用于在更新构建版本时自动传播用户修改。

实例配置按如下方式加载：

* 该模块加载&#x200B;**serverConf.xml**&#x200B;文件以获取所有实例共享的参数。
* 然后，它加载&#x200B;**config-**`<instance>`**.xml**&#x200B;文件。 此文件中找到的值比&#x200B;**serverConf.xml**&#x200B;中包含的值具有优先级。

   这两个文件的格式相同。 对于&#x200B;**config-`<instance>`.xml**&#x200B;文件中的给定实例，**serverConf.xml**&#x200B;中的任何值都可以重载。

此操作模式为配置提供了极大的灵活性。
