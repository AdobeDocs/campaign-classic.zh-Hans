---
product: campaign
title: 托管模型
description: 探索Campaign托管模型
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 2%

---

# 托管模型{#hosting-models}



Adobe Campaign提供三种托管模式供您选择，让您能够灵活自由地选择最佳模式，也可以选择多种模式以满足业务需求。

>[!NOTE]
>
>对于Adobe托管的环境，主要安装和配置步骤只能由Adobe执行，例如配置服务器和自定义实例配置文件。 要详细了解部署模式之间的主要差异，请参阅 [此页面](../../installation/using/capability-matrix.md).

## Managed Services/托管

Adobe Campaign可以as a Managed Service部署：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和客户的Campaign数据库）都完全由Adobe托管，包括电子邮件执行、镜像页面、跟踪服务器和面向外部的Web组件（例如取消订阅页面/首选项中心和登陆页面）。

![](assets/deployment_hosted.png)

作为托管客户，大多数安装和配置步骤都由Adobe执行。 您可以访问以下部分以自定义实施：

* 按品牌配置跟踪和镜像页面URL。 有关事务型消息，请参阅 [至此部分](../../message-center/using/additional-configurations.md#configuring-multibranding).
* 安装客户端控制台：请参阅 [至此部分](../../installation/using/installing-the-client-console.md).
* 通过阅读 [详细文档](../../delivery/using/about-deliverability.md).
* 配置Campaign选项：请参阅 [至此部分](../../installation/using/configuring-campaign-options.md).
* 配置CRM连接器：请参阅 [至此部分](../../platform/using/crm-connectors.md).

## 内部部署

Adobe Campaign可以内部部署：Adobe Campaign的所有组件（包括用户界面、执行管理引擎和数据库）都驻留在客户的数据中心内。 在此部署模型中，客户管理所有软件和硬件更新和升级，而专门的数据库管理员需要执行维护和优化任务，以确保Campaign实例管理。

![](assets/deployment_onpremise.png)

作为内部部署客户，在开始部署Campaign Classic之前，请注意以下先决条件和建议：

* 阅读 [兼容性矩阵](../../rn/using/compatibility-matrix.md) 其中列出了Adobe Campaign支持的所有系统和组件版本。
* 根据您的环境，阅读 [Windows先决条件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) 和 [Linux先决条件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* 了解与数据库引擎相关的建议 [在此部分中](../../installation/using/database.md).
* 检查服务器上是否安装了所需的数据库访问层，以及是否可从Adobe Campaign帐户访问。 [了解详情](../../installation/using/application-server.md)。
* 根据某些进程需要与其他进程通信或访问LAN和Internet来配置网络。 这意味着需要为这些进程打开一些TCP端口。 [了解详情](../../installation/using/network-configuration.md) 关于网络配置要求。
* 已阅读 [Campaign安全和隐私检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html).
* 查看评估内部部署硬件需求的一般准则 [本文章节](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html).

## 混合

作为混合模型部署时，Adobe Campaign解决方案软件将驻留在客户站点内，并以Adobe云服务的形式提供执行管理。 Adobe Campaign营销实例安装在客户的防火墙内，因此个人身份信息(PII)保留在公司内部，并且只有个性化电子邮件所需的数据才会发送到云以执行电子邮件。 在云中托管的执行实例接收来自内部部署实例的请求，以投放电子邮件。 此实例可个性化所有电子邮件并发送它们。 云中不会永久存储任何类型的数据。

![](assets/deployment_hybrid.png)

作为混合型客户，大多数安装和配置步骤都由Adobe执行。 您可以访问以下部分以自定义实施：

* 配置事务型消息：请参阅 [至此部分](../../message-center/using/transactional-messaging-architecture.md).
* 按品牌配置跟踪和镜像页面URL。 有关事务型消息，请参阅 [至此部分](../../message-center/using/additional-configurations.md#configuring-multibranding).
* 安装客户端控制台：请参阅 [至此部分](../../installation/using/installing-the-client-console.md).
* 安装内置包：请参阅 [至此部分](../../installation/using/installing-campaign-standard-packages.md).
* 可交付性：配置 [MX规则](../../installation/using/email-deliverability.md#mx-configuration) 和 [电子邮件格式](../../installation/using/email-deliverability.md#managing-email-formats). 通过阅读 [详细文档](../../delivery/using/about-deliverability.md).
* 配置Campaign选项：请参阅 [至此部分](../../installation/using/configuring-campaign-options.md).
* 配置外部数据库（联合数据访问）：请参阅 [至此部分](../../installation/using/about-fda.md).
* 配置CRM连接器：请参阅 [至此部分](../../platform/using/crm-connectors.md).
* 要了解有关中间源部署原则的更多信息，请参阅 [至此部分](../../installation/using/mid-sourcing-deployment.md).
