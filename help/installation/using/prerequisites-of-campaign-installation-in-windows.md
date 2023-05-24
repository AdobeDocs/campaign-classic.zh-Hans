---
product: campaign
title: 在 Windows 中安装 Campaign 的先决条件
description: 在 Windows 中安装 Campaign 的先决条件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# 开始在Windows上安装Campaign {#prerequisites-of-campaign-installation-in-windows}



有关安装Adobe Campaign所需的技术配置和软件，请参见 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

多实例使用的Adobe Campaign服务器安装过程如下所述： [安装服务器](../../installation/using/installing-the-server.md).

主要步骤如下：

1. 安装应用程序服务器，请参阅 [执行安装程序](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. 与Web服务器集成（可选，具体取决于部署的组件），请参阅 [配置IIS Web服务器](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

完成安装步骤后，您需要配置实例、数据库和服务器。 有关更多信息，请参阅 [关于初始配置](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>将Adobe Campaign部署到Windows环境时，具有必要访问权限的用户可以在网络上的文件操作期间使用UNC语法(Universal.Uniform Naming Convention)访问路径。
