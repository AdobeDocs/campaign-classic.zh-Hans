---
solution: Campaign Classic
product: campaign
title: 配置与Adobe Target的集成
description: 配置与Adobe Target的集成
audience: integrations
content-type: reference
topic-tags: adobe-target
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# 配置与Adobe Target{#configuring-the-integration-with-adobe-target}的集成

## 先决条件{#prerequisites}

要使用Adobe Campaign与Adobe Target之间的集成，您必须：

* Adobe Experience Cloud和Adobe Target组织
* 指定用于建立与Adobe Campaign的连接的Adobe Target rawbox

## 配置Adobe Campaign{#configuring-adobe-campaign}

配置Adobe Campaign:

1. 安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;标准包。 安装集成包与安装标准包相同，详见[包导入](../../platform/using/working-with-data-packages.md#importing-packages)部分。 这使您能够通过数字资产管理器访问共享资产。
1. 启用通过IMS(Adobe ID连接服务)的连接，以在电子邮件中使用通过Adobe Experience Cloud共享的图像。 请查阅有关[IMS](../../integrations/using/about-adobe-id.md)的部分。
1. 在&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;中，为Adobe Target配置服务器和组织（租户）选项：

   * **[!UICONTROL TNT_EdgeServer]** :用于集成的Adobe Target服务器。默认情况下，此选项已被选中。 此值与Adobe Target **[!UICONTROL Domain Server]**&#x200B;对应，后跟值&#x200B;**/m2**。 例如：**tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** :Adobe Target组织名称。此值与Adobe Target **[!UICONTROL Client]**&#x200B;的名称相对应。

   ![](assets/tar_options.png)

