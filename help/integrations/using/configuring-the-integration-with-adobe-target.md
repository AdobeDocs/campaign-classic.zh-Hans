---
title: 配置与Adobe Target的集成
seo-title: 配置与Adobe Target的集成
description: 配置与Adobe Target的集成
seo-description: null
page-status-flag: never-activated
uuid: b9337e92-e4e5-4cba-a559-75db7460d5c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 378d5ff9-88c0-43f1-beb8-454701e9f1d1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Configuring the integration with Adobe Target{#configuring-the-integration-with-adobe-target}

## 先决条件{#prerequisites}

要使用Adobe Campaign与Adobe Target之间的集成，您必须：

* Adobe Experience Cloud和Adobe Target组织
* 为建立与Adobe Campaign的连接而指定的Adobe Target罗博克斯

## 配置Adobe Campaign {#configuring-adobe-campaign}

配置Adobe Campaign:

1. 安装标 **[!UICONTROL Integration with the Adobe Experience Cloud]** 准包。 安装集成包与安装标准包相同，详见包导入 [部分](../../platform/using/working-with-data-packages.md#importing-packages) 。 这使您能够通过数字资产管理器访问共享资产。
1. 启用通过IMS(Adobe ID连接服务)的连接，以在您的电子邮件中使用通过Adobe Experience Cloud共享的图像。 请查阅有关IMS [的部分](../../integrations/using/about-adobe-id.md)。
1. 在中 **[!UICONTROL Administration > Platform > Options]**，为Adobe Target配置服务器和组织（租户）选项：

   * **[!UICONTROL TNT_EdgeServer]** :Adobe Target服务器用于集成。 默认情况下，此选项已被选中。 此值与Adobe Target **[!UICONTROL Domain Server]**&#x200B;对应，后跟 **值/m2**。 例如： **tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** :Adobe Target组织名称。 此值与Adobe Target的名称相对应 **[!UICONTROL Client]**。

   ![](assets/tar_options.png)

