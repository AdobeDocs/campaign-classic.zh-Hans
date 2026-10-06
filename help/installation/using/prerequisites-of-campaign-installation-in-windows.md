---
product: campaign
title: 在Windows中安装Campaign的先决条件
description: 在Windows中安装Campaign的先决条件
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
TQID: 'https://experienceleague.adobe.com/vECxz7-bt6DMteRM-N4BtD6Uo5qonHrkgQQeEOkTSt0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 11%
---
# 开始在Windows上安装Campaign {#prerequisites-of-campaign-installation-in-windows}



[兼容性矩阵](../../rn/using/compatibility-matrix.md)中列出了安装Adobe Campaign所需的技术配置和软件。

下面的[安装服务器](../../installation/using/installing-the-server.md)中介绍了用于多实例的Adobe Campaign服务器安装过程。

主要步骤如下：

1. 安装应用程序服务器，请参阅[正在执行安装程序](../../installation/using/installing-the-server.md#executing-the-installation-program)。
1. 与Web服务器集成（可选，具体取决于部署的组件），请参阅[配置IIS Web服务器](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server)。

完成安装步骤后，您需要配置实例、数据库和服务器。 有关详细信息，请参阅[关于初始配置](../../installation/using/about-initial-configuration.md)。

>[!NOTE]
>
>将Adobe Campaign部署到Windows环境时，在网络上处理文件期间，具有必要访问权限的用户可以使用UNC语法(Universal.Uniform Naming Convention)访问路径。
