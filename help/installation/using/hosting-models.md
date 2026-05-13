---
product: campaign
title: 托管模型
description: 了解活动托管模型
feature: Installation, Architecture, Deployment
role: Developer
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
TQID: https://experienceleague.adobe.com/9pZQYt2gLVR94ZWsw21JCv7CL55KDRyiqocvuS54SbM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
  - id: fb2a841f-c522-491f-9901-a1b939d252df
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 637
ht-degree: 3%

---

# 托管模型{#hosting-models}



Adobe Campaign提供了三种托管模型供您选择，它们提供了灵活性和自由性来选择最佳模型，或者提供了多种模型以满足业务需求。

>[!NOTE]
>
>对于Adobe托管环境，主要安装和配置步骤只能由Adobe执行，例如配置服务器和自定义实例配置文件。 要了解有关部署模式之间主要差异的更多信息，请参阅[此页面](../../installation/using/capability-matrix.md)。

## Managed Services/托管

Adobe Campaign可部署到as a Managed Service：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和客户的Campaign数据库）都完全由Adobe托管，包括电子邮件执行、镜像页面、跟踪服务器和面向外部的Web组件（如取消订阅页面/首选项中心和登陆页面）。

![](assets/deployment_hosted.png)

作为托管客户，大部分安装和配置步骤都由Adobe执行。 您可以访问以下部分以自定义实施：

* 为每个品牌配置跟踪和镜像页面URL。 有关事务型消息，请参阅[此章节](../../message-center/using/additional-configurations.md#configuring-multibranding)。
* 安装客户端控制台：请参阅[本节内容](../../installation/using/installing-the-client-console.md)。
* 通过阅读[详细文档](../../delivery/using/about-deliverability.md)，了解有关可投放性工具和最佳实践的更多信息。
* 配置Campaign选项：请参阅[本节内容](../../installation/using/configuring-campaign-options.md)。
* 配置CRM连接器：请参阅[本节内容](../../platform/using/crm-connectors.md)。

## 内部部署

Adobe Campaign可以内部部署：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和数据库）都驻留在客户的数据中心内。 在此部署模型中，客户管理所有软件和硬件更新和升级，而专门的数据库管理员需要执行维护和优化任务，以确保Campaign实例管理。

![](assets/deployment_onpremise.png)

作为内部部署客户，在开始部署Campaign Classic之前，请注意以下先决条件和建议：

* 阅读[兼容性矩阵](../../rn/using/compatibility-matrix.md)，其中列出了Adobe Campaign支持的所有系统和组件版本。
* 根据您的环境，阅读Windows[&#128279;](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)的[先决条件和Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)的先决条件。
* 在此部分[&#128279;](../../installation/using/database.md)中了解与数据库引擎相关的建议。
* 检查服务器上是否安装了所需的数据库访问层，以及是否可从Adobe Campaign帐户访问。 [了解详情](../../installation/using/application-server.md)。
* 根据某些进程需要与其他进程通信或访问LAN和Internet来配置网络。 这意味着这些进程需要打开某些TCP端口。 [了解有关](../../installation/using/network-configuration.md)网络配置要求的更多信息。
* 阅读[Campaign安全和隐私检查清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。
* 请参阅本文[&#128279;](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html)中有关估算内部部署的硬件要求的一般准则。

## 混合

作为混合模型部署时，Adobe Campaign解决方案软件驻留在客户站点内，执行管理由Adobe以云服务的形式提供。 Adobe Campaign营销实例安装在客户的防火墙内，因此个人身份信息(PII)保留在公司内部，并且只有个性化电子邮件所需的数据才会发送到云以执行电子邮件。 在云中托管的执行实例接收来自内部部署实例的请求以投放电子邮件。 此实例可将所有电子邮件个性化并交付。 云中不会永久存储任何类型的数据。

![](assets/deployment_hybrid.png)

作为混合型客户，大部分安装和配置步骤都由Adobe执行。 您可以访问以下部分以自定义实施：

* 配置事务性消息：请参阅[本节内容](../../message-center/using/transactional-messaging-architecture.md)。
* 为每个品牌配置跟踪和镜像页面URL。 有关事务型消息，请参阅[此章节](../../message-center/using/additional-configurations.md#configuring-multibranding)。
* 安装客户端控制台：请参阅[本节内容](../../installation/using/installing-the-client-console.md)。
* 安装内置包：请参阅[本节内容](../../installation/using/installing-campaign-standard-packages.md)。
* 可投放性：配置[MX规则](../../installation/using/email-deliverability.md#mx-configuration)和[电子邮件格式](../../installation/using/email-deliverability.md#managing-email-formats)。 通过阅读[详细文档](../../delivery/using/about-deliverability.md)，了解有关可投放性工具和最佳实践的更多信息。
* 配置Campaign选项：请参阅[本节内容](../../installation/using/configuring-campaign-options.md)。
* 配置外部数据库（联合数据访问）：请参阅[本节内容](../../installation/using/about-fda.md)。
* 正在配置CRM连接器：请参阅[本节内容](../../platform/using/crm-connectors.md)。
* 要了解有关中间源部署原则的更多信息，请参阅[本节内容](../../installation/using/mid-sourcing-deployment.md)。
