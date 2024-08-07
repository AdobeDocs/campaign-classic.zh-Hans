---
product: campaign
title: 在Windows中安装Campaign的先决条件
description: 在Windows中安装Campaign的先决条件
feature: Installation, Instance Settings
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

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
