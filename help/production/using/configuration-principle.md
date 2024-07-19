---
product: campaign
title: 配置原则
description: 配置原则
feature: Monitoring, Configuration
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 5%

---

# 配置原则{#configuration-principle}



Adobe Campaign平台基于实例的概念，与Apache使用的虚拟主机概念类似。 这种操作模式允许您通过为服务器分配多个实例来共享服务器。 实例彼此完全独立，并使用自己的数据库和配置文件进行操作。

对于给定的服务器，有两个元素是所有Adobe Campaign实例所共有的：

* **内部**&#x200B;密码：这是常规管理员密码。 它对于特定应用程序服务器的所有实例都是通用的。

  >[!IMPORTANT]
  >
  >要使用&#x200B;**内部**&#x200B;标识符登录，您需要预先定义密码。 如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#internal-identifier)。

* 多个技术服务器配置：在实例的特定配置中，这些配置都可以过载。

配置文件保存在安装目录的&#x200B;**conf**&#x200B;目录中。 该配置分为三个文件：

* **serverConf.xml**：所有实例的整体配置。
* **config-**`<instance>`**.xml** （其中&#x200B;**`<instance>`**&#x200B;是实例名称）：实例的特定配置。
* **serverConf.xml.diff**：初始配置与当前配置之间的增量。 此文件由应用程序自动生成，不得手动修改。 它用于在更新内部版本时自动传播用户修改。

按如下方式加载实例配置：

* 模块加载&#x200B;**serverConf.xml**&#x200B;文件以获取所有实例共享的参数。
* 然后加载&#x200B;**config-**`<instance>`**.xml**&#x200B;文件。 在此文件中找到的值的优先级高于&#x200B;**serverConf.xml**&#x200B;中包含的值。

  这两个文件的格式相同。 可以为&#x200B;**config-`<instance>`.xml**&#x200B;文件中的给定实例重载&#x200B;**serverConf.xml**&#x200B;中的任何值。

此操作模式为配置提供了极大的灵活性。
