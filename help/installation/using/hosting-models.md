---
solution: Campaign Classic
product: campaign
title: 托管模型
description: 发现活动托管模型
feature: 概述
role: 架构师
level: 初学者
translation-type: tm+mt
source-git-commit: 09bd634142f643206c38ac5f881302a5d489ecaf
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 2%

---


# 托管模型{#hosting-models}

Adobe Campaign优惠可选择三种托管模型，从而提供选择最佳模型的灵活性和自由度，或选择适合业务需求的模型。

>[!NOTE]
>
>对于Adobe托管环境，主要安装和配置步骤只能由Adobe执行，如配置服务器和自定义实例配置文件。 要进一步了解部署模式之间的主要差异，请参阅[此页](../../installation/using/capability-matrix.md)。

## Managed Services/托管

Adobe Campaign可以部署为托管服务：Adobe Campaign的所有组件(包括用户界面、执行管理引擎和客户的活动数据库)都完全由Adobe托管，包括电子邮件执行、镜像页面、跟踪服务器以及面向外部的Web组件(如取消订阅页面/首选项中心和登陆页)。

![](assets/deployment_hosted.png)

作为托管客户，大多数安装和配置步骤由Adobe执行。 您可以访问以下部分来自定义您的实施：

* 根据品牌配置跟踪和镜像页面URL。 有关事务性消息，请参阅[以了解本节](../../message-center/using/configuring-multibranding.md)。
* 安装客户端控制台：请参阅本节](../../installation/using/installing-the-client-console.md)。[
* 阅读详细文档[](../../delivery/using/about-deliverability.md)，进一步了解可交付性工具和最佳实践。
* 配置活动选项：请参阅本节](../../installation/using/configuring-campaign-options.md)。[
* 配置CRM连接器：请参阅本节](../../platform/using/crm-connectors.md)。[

## 内部部署

Adobe Campaign可以内部部署：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和数据库）都驻留在客户的数据中心内。 在此部署模型中，客户管理所有软件和硬件更新和升级，而专用数据库管理员需要执行维护和优化任务以确保活动实例管理。

![](assets/deployment_onpremise.png)

作为预置型客户，在开始部署Campaign Classic之前，请考虑以下先决条件和建议：

* 请阅读[兼容性矩阵](../../rn/using/compatibility-matrix.md)，其中列表了支持Adobe Campaign的所有系统和组件版本。
* 根据您的环境，请阅读Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)的[先决条件和Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)的[先决条件。
* 了解本节](../../installation/using/database.md)中与数据库引擎[相关的建议。
* 检查所需的Adobe Campaign库访问层是否安装在服务器上，并可从数据库帐户访问。 [了解详情](../../installation/using/application-server.md)。
* 将网络配置为某些进程需要与他人通信或访问局域网和因特网。 这意味着需要为这些进程打开某些TCP端口。 [了解](../../installation/using/network-configuration.md) 有关网络配置要求的更多信息。
* 请阅读[活动安全和隐私清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。
* 请查阅本文](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html)中有关估计内部部署[的硬件需求的一般准则。

## 混合

当部署为混合模型时，Adobe Campaign解决方案软件驻留在客户现场，执行管理通过Adobe作为云服务提供。 Adobe Campaign营销实例安装在客户的防火墙内，因此个人身份信息(PII)仍在内部，并且只会将个性化电子邮件所需的数据发送到云以执行电子邮件。 托管在云中的执行实例会接收来自内部部署实例的发送电子邮件的请求。 此实例个性化所有电子邮件并提供它们。 云中不会永久存储任何类型的数据。

![](assets/deployment_hybrid.png)

作为混合型客户，大多数安装和配置步骤由Adobe执行。 您可以访问以下部分来自定义您的实施：

* 配置事务性消息:请参阅本节](../../message-center/using/transactional-messaging-architecture.md)。[
* 根据品牌配置跟踪和镜像页面URL。 有关事务性消息，请参阅[以了解本节](../../message-center/using/configuring-multibranding.md)。
* 安装客户端控制台：请参阅本节](../../installation/using/installing-the-client-console.md)。[
* 安装内置包：请参阅本节](../../installation/using/installing-campaign-standard-packages.md)。[
* 可交付性：配置[MX规则](../../installation/using/email-deliverability.md#mx-configuration)和[电子邮件格式](../../installation/using/email-deliverability.md#managing-email-formats)。 阅读详细文档[](../../delivery/using/about-deliverability.md)，进一步了解可交付性工具和最佳实践。
* 配置活动选项：请参阅本节](../../installation/using/configuring-campaign-options.md)。[
* 配置外部数据库(联合数据访问):请参阅本节](../../installation/using/about-fda.md)。[
* 配置CRM连接器：请参阅本节](../../platform/using/crm-connectors.md)。[
* 要了解有关中间源部署原则的更多信息，请参阅本节](../../installation/using/mid-sourcing-deployment.md)。[
