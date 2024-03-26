---
product: campaign
title: 关于初始配置
description: 关于初始配置
feature: Installation, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 8%

---

# 配置和部署实例的关键步骤{#about-initial-configuration}



Adobe Campaign安装完成后，您需要对其进行配置，以确保它在您的限制和技术架构下有效运行。 本章将按照以下顺序详细介绍配置Adobe Campaign实例的步骤：

1. 创建实例和相关连接，请参阅 [创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md).
1. 创建和配置数据库，请参见 [创建和配置数据库](../../installation/using/creating-and-configuring-the-database.md).
1. 配置Adobe Campaign服务器，请参阅 [Campaign服务器配置](../../installation/using/configuring-campaign-server.md).
1. 部署实例，请参阅 [部署实例](../../installation/using/deploying-an-instance.md).

配置实例意味着启用进程（web、mta、wfserver等） ，并为发送电子邮件、跟踪等配置模块。 对于每个实例，都会在服务器上激活Adobe Campaign进程。 如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#enabling-processes)。

可能需要为每个实例进行其他配置以优化Adobe Campaign操作（具体取决于使用的模块、您的架构和需求）。
