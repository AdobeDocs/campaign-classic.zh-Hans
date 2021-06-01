---
solution: Campaign Classic
product: campaign
title: 托管模型
description: 探索Campaign托管模型
feature: 概述
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 54d503e97a4374927c4ebe3ba4e0ec05e51d47db
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 2%

---

# 托管模型{#hosting-models}

Adobe Campaign提供三种托管模型的选择，从而提供选择最佳模型或适合业务需求的模型的灵活性和自由。

>[!NOTE]
>
>对于Adobe托管环境，主要安装和配置步骤只能通过Adobe执行，例如配置服务器和自定义实例配置文件。 要详细了解部署模式之间的主要区别，请参阅[此页面](../../installation/using/capability-matrix.md)。

## Managed Services /托管

Adobe Campaign可以部署为托管服务：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和客户的Campaign数据库）都由Adobe完全托管，包括电子邮件执行、镜像页面、跟踪服务器以及面向外部的Web组件（如取消订阅页面/首选项中心和登陆页面）。

![](assets/deployment_hosted.png)

作为托管客户，大多数安装和配置步骤都由Adobe执行。 您可以访问以下部分以自定义您的实施：

* 按品牌配置跟踪和镜像页面URL。 有关事务型消息，请参阅此章节](../../message-center/using/additional-configurations.md#configuring-multibranding)。[
* 安装客户端控制台：请参阅[到此部分](../../installation/using/installing-the-client-console.md)。
* 阅读[详细文档](../../delivery/using/about-deliverability.md)，了解有关投放能力工具和最佳实践的更多信息。
* 配置Campaign选项：请参阅[到此部分](../../installation/using/configuring-campaign-options.md)。
* 配置CRM连接器：请参阅[到此部分](../../platform/using/crm-connectors.md)。

## 内部部署

Adobe Campaign可以内部部署：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和数据库）都驻留在客户的数据中心。 在此部署模型中，客户管理所有软件和硬件更新和升级，而专门的数据库管理员需要执行维护和优化任务以确保Campaign实例管理。

![](assets/deployment_onpremise.png)

作为内部部署客户，在开始部署Campaign Classic之前，请考虑以下先决条件和建议：

* 阅读[兼容性矩阵](../../rn/using/compatibility-matrix.md)，其中列出了支持Adobe Campaign的所有系统和组件版本。
* 根据您的环境，请阅读Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)的先决条件和Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)的[先决条件。[
* 在此部分](../../installation/using/database.md)中了解与数据库引擎[相关的建议。
* 检查所需的数据库访问层是否安装在服务器上，并可从Adobe Campaign帐户访问。 [了解详情](../../installation/using/application-server.md)。
* 将网络配置为某些进程需要与其他进程通信或访问LAN和Internet。 这意味着需要为这些进程打开一些TCP端口。 [了解](../../installation/using/network-configuration.md) 有关网络配置要求的更多信息。
* 请参阅[Campaign安全和隐私检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。
* 查看本文](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html)中有关估算内部部署[硬件需求的一般准则。

## 混合

作为混合模型部署时，Adobe Campaign解决方案软件驻留在客户站点的内部部署，并且执行管理通过Adobe作为云服务提供。 Adobe Campaign营销实例安装在客户的防火墙中，因此个人身份信息(PII)仍保留在内部，并且只有个性化电子邮件所需的数据才会发送到云以执行电子邮件。 在云中托管的执行实例接收来自内部部署实例的发送电子邮件请求。 此实例将个性化所有电子邮件并提交它们。 任何类型的数据都不会永久存储在云中。

![](assets/deployment_hybrid.png)

作为混合型客户，大多数安装和配置步骤都由Adobe执行。 您可以访问以下部分以自定义您的实施：

* 配置事务型消息：请参阅[到此部分](../../message-center/using/transactional-messaging-architecture.md)。
* 按品牌配置跟踪和镜像页面URL。 有关事务型消息，请参阅此章节](../../message-center/using/additional-configurations.md#configuring-multibranding)。[
* 安装客户端控制台：请参阅[到此部分](../../installation/using/installing-the-client-console.md)。
* 安装内置软件包：请参阅[到此部分](../../installation/using/installing-campaign-standard-packages.md)。
* 投放能力：配置[MX规则](../../installation/using/email-deliverability.md#mx-configuration)和[电子邮件格式](../../installation/using/email-deliverability.md#managing-email-formats)。 阅读[详细文档](../../delivery/using/about-deliverability.md)，了解有关投放能力工具和最佳实践的更多信息。
* 配置Campaign选项：请参阅[到此部分](../../installation/using/configuring-campaign-options.md)。
* 配置外部数据库（联合数据访问）：请参阅[到此部分](../../installation/using/about-fda.md)。
* 配置CRM连接器：请参阅[到此部分](../../platform/using/crm-connectors.md)。
* 要了解有关中间源部署原则的更多信息，请参阅此部分](../../installation/using/mid-sourcing-deployment.md)。[
