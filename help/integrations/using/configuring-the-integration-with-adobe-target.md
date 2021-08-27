---
product: campaign
title: 配置与Adobe Target的集成
description: 配置与Adobe Target的集成
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# 配置与Adobe Target的集成{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)

## 先决条件 {#prerequisites}

要使用Adobe Campaign与Adobe Target之间的集成，您必须：

* Adobe Experience Cloud和Adobe Target组织
* 指定用于建立与Adobe Campaign的连接的Adobe Targetrawbox

## 配置Adobe Campaign {#configuring-adobe-campaign}

要配置Adobe Campaign，请执行以下操作：

1. 安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;标准包。 安装集成包与安装标准包相同，有关详细信息，请参阅[包导入](../../platform/using/working-with-data-packages.md#importing-packages)一节。 这允许您通过数字资产管理器访问共享的资产。
1. 启用通过IMS(Adobe ID连接服务)的连接，以在电子邮件中使用通过Adobe Experience Cloud共享的图像。 请参阅关于[IMS](../../integrations/using/about-adobe-id.md)的章节。
1. 在&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;中，为Adobe Target配置服务器和组织（租户）选项：

   * **[!UICONTROL TNT_EdgeServer]** :用于集成的Adobe Target服务器。默认情况下，此选项已被选中。 此值对应于Adobe Target **[!UICONTROL Domain Server]**，后跟值&#x200B;**/m2**。 例如：**tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** :Adobe Target组织名称。此值对应于Adobe Target **[!UICONTROL Client]**&#x200B;的名称。

   ![](assets/tar_options.png)

>[!CAUTION]
>
>对于混合和托管架构，必须在所有服务器上设置这些选项，包括[中间源服务器](../../installation/using/mid-sourcing-server.md)和[执行实例](../../message-center/using/configuring-instances.md#execution-instance)。