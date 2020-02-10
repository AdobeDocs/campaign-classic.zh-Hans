---
title: 托管模型
seo-title: 托管模型
description: 托管模型
seo-description: null
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 托管模型{#hosting-models}

Adobe Campaign提供三种托管模型的选择，提供了灵活性和自由性，可根据业务需求选择最佳模型或模型。

>[!NOTE]
>
>主要安装和配置步骤只能由Adobe为Adobe托管的部署执行。 例如，配置服务器和实例配置文件。 要进一步了解部署模式之间的主要差异，请参阅 [本文](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)。 如果您有托管或混合型号，请参阅此 [部分](../../installation/using/about-hybrid-and-hosted-models.md)。

* **托管服务（托管）**

   Adobe Campaign可以部署为托管服务：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和客户的Campaign数据库）都由Adobe完全托管，包括电子邮件执行、镜像页面、跟踪服务器以及面向外部的Web组件（如取消订阅页面／首选项中心和登录页面）。 Adobe在云中最多分配三个实例——开发、测试／阶段和生产。 本节介绍此托管模型的安装和配置步 [骤](../../installation/using/hosted-model.md)。

   ![](assets/deployment_hosted.png)

* **内部部署**

   Adobe Campaign可以部署在内部部署：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和数据库）都驻留在客户的数据中心内。 在此部署模型中，客户管理所有软件和硬件更新和升级，而专用数据库管理员需要执行维护和优化任务以确保Campaign实例管理。

   ![](assets/deployment_onpremise.png)

* **混合**

   作为混合模型部署时，Adobe Campaign解决方案软件驻留在客户站点的内部部署，执行管理由Adobe作为云服务提供。 Adobe Campaign营销实例安装在客户的防火墙内，因此个人可识别信息(PII)将保留在内部，并且只有个性化电子邮件所需的数据才会发送到Cloud以执行电子邮件。 托管在云中的执行实例接收来自内部部署实例的请求以发送电子邮件。 此实例个性化所有电子邮件并提供它们。 任何类型的数据都不会永久存储在云中。 本节介绍此托管模型的安装和配置步 [骤](../../installation/using/hybrid-model.md)。

   ![](assets/deployment_hybrid.png)

