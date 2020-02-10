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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 配置与Adobe Target的集成{#configuring-the-integration-with-adobe-target}

## 先决条件 {#prerequisites}

要使用Adobe Campaign与Adobe Target之间的集成，您必须：

* Adobe Experience cloud和Adobe Target组织
* 指定用于与Adobe Campaign建立连接的Adobe Target rawbox

## 配置Adobe Campaign {#configuring-adobe-campaign}

要配置Adobe Campaign，请执行以下操作：

1. 安装标 **[!UICONTROL Integration with the Adobe Experience Cloud]** 准包。 安装集成包与安装标准包相同，详见“包导入” [部分](../../platform/using/working-with-data-packages.md#importing-packages) 。 这使您能够通过数字资产管理器访问共享资产。
1. 通过IMS（Adobe ID连接服务）启用连接，以在您的电子邮件中使用通过Adobe Experience cloud共享的图像。 请查阅有关 [IMS的部分](../../integrations/using/about-adobe-id.md)。
1. 在中， **[!UICONTROL Administration > Platform > Options]**&#x200B;为Adobe Target配置服务器和组织（租户）选项：

   * **[!UICONTROL TNT_EdgeServer]** :用于集成的Adobe Target服务器。 默认情况下，此选项已被选中。 此值与Adobe Target对 **[!UICONTROL Domain Server]**&#x200B;应，后跟 **值/m2**。 例如： **tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** :Adobe target组织名称。 此值与Adobe Target的名称相对应 **[!UICONTROL Client]**。
   ![](assets/tar_options.png)

