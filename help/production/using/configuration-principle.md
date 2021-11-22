---
product: campaign
title: 配置原则
description: 配置原则
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# 配置原则{#configuration-principle}

![](../../assets/v7-only.svg)

Adobe Campaign平台基于实例的概念，与Apache使用的虚拟主机的概念类似。 此操作模式允许您通过为服务器分配多个实例来共享服务器。 实例彼此完全分离，并使用它们自己的数据库和配置文件运行。

对于给定服务器，有两个元素对于所有Adobe Campaign实例都是通用的：

* 的 **内部** 密码：这是一般管理员密码。 它对特定应用程序服务器的所有实例都是通用的。

   >[!IMPORTANT]
   >
   >要使用 **内部** 标识符，您需要事先定义密码。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

* 多种技术服务器配置：这些配置在实例的特定配置中都可能会过载。

配置文件保存在 **conf** 安装目录的目录。 配置分为三个文件：

* **serverConf.xml**:所有实例的整体配置。
* **配置 —**`<instance>`**.xml** (其中 **`<instance>`** 是实例名称):实例的特定配置。
* **serverConf.xml.diff**:初始配置与当前配置之间的增量。 此文件由应用程序自动生成，不得手动修改。 它用于在更新内部版本时自动传播用户修改。

实例配置的加载方式如下：

* 模块加载 **serverConf.xml** 文件以获取所有实例共享的参数。
* 然后加载 **配置 —**`<instance>`**.xml** 文件。 与 **serverConf.xml**.

   这两个文件的格式相同。 中的任意值 **serverConf.xml** 对于中的给定实例，可能会过载 **配置 — `<instance>`.xml** 文件。

此操作模式为配置提供了极大的灵活性。
