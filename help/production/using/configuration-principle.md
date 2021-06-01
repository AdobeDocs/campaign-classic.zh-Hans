---
product: campaign
title: 配置原则
description: 配置原则
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# 配置原则{#configuration-principle}

Adobe Campaign平台基于实例的概念，与Apache使用的虚拟主机的概念类似。 此操作模式允许您通过为服务器分配多个实例来共享服务器。 实例彼此完全分离，并使用它们自己的数据库和配置文件运行。

对于给定服务器，有两个元素对于所有Adobe Campaign实例都是通用的：

* **internal**&#x200B;密码：这是一般管理员密码。 它对特定应用程序服务器的所有实例都是通用的。

   >[!IMPORTANT]
   >
   >要使用&#x200B;**Internal**&#x200B;标识符登录，您需要事先定义密码。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

* 多种技术服务器配置：这些配置在实例的特定配置中都可能会过载。

配置文件保存在安装目录的&#x200B;**conf**&#x200B;目录中。 配置分为三个文件：

* **serverConf.xml**:所有实例的整体配置。
* **config-**`<instance>`**.xml** (其中 **`<instance>`** 是实例名称):实例的特定配置。
* **serverConf.xml.diff**:初始配置与当前配置之间的增量。此文件由应用程序自动生成，不得手动修改。 它用于在更新内部版本时自动传播用户修改。

实例配置的加载方式如下：

* 模块加载&#x200B;**serverConf.xml**&#x200B;文件，以获取所有实例共享的参数。
* 然后，它会加载&#x200B;**config-**`<instance>`**.xml**&#x200B;文件。 与&#x200B;**serverConf.xml**&#x200B;中包含的值相比，此文件中的值具有优先级。

   这两个文件的格式相同。 **serverConf.xml**&#x200B;中的任何值都可以为&#x200B;**config-`<instance>`.xml**&#x200B;文件中的给定实例进行重载。

此操作模式为配置提供了极大的灵活性。
