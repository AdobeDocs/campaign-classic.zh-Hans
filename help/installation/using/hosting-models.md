---
title: 托管模型
description: 发现活动托管模型
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
translation-type: tm+mt
source-git-commit: 24521f77d6d13f8469869fdd8445b46a8d215dad
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---


# 托管模型{#hosting-models}

Adobe Campaign优惠可选择三种托管模型，提供选择最佳模型的灵活性和自由性，或选择适合业务需求的模型。

>[!NOTE]
>
>对于Adobe托管环境，主要安装和配置步骤只能由Adobe执行，如配置服务器和自定义实例配置文件。 要进一步了解部署模式之间的主要差异，请参 [阅本页](../../installation/using/capability-matrix.md)。

* **Managed Services（托管）**

   Adobe Campaign可以部署为托管服务：adobe campaign的所有组件(包括用户界面、执行管理引擎和客户的活动数据库)都完全由Adobe托管，包括电子邮件执行、镜像页面、跟踪服务器以及面向外部的Web组件(如取消订阅页面／首选项中心和登陆页)。 Adobe在云中最多分配三个实例——开发、测试／阶段和生产。 本节介绍此托管模型的安装和 [配置步骤](../../installation/using/hosted-model.md)。

   ![](assets/deployment_hosted.png)

* **内部部署**

   Adobe Campaign可以内部部署：adobe campaign的所有组件（包括用户界面、执行管理引擎和数据库）都驻留在客户的数据中心内。 在此部署模型中，客户管理所有软件和硬件更新和升级，而专用的数据库管理员需要执行维护和优化任务以确保活动实例管理。 本节介绍了适用于预置型客户的 [部署指南](../../installation/using/before-starting.md)。

   ![](assets/deployment_onpremise.png)

* **混合**

   当部署为混合模型时，Adobe Campaign解决方案软件驻留在客户现场，执行管理通过Adobe作为云服务提供。 Adobe Campaign营销实例安装在客户的防火墙内，因此个人身份信息(PII)将保留在内部，并且只有个性化电子邮件所需的数据才会发送到云以执行电子邮件。 托管在云中的执行实例会接收来自内部部署实例的发送电子邮件的请求。 此实例个性化所有电子邮件并提供它们。 云中不会永久存储任何类型的数据。 本节介绍此托管模型的安装和 [配置步骤](../../installation/using/hybrid-model.md)。

   ![](assets/deployment_hybrid.png)

