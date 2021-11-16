---
product: campaign
title: 配置与Adobe Target的集成
description: 配置与Adobe Target的集成
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 2%

---

# 配置与Adobe Target的集成{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)


>[!CAUTION]
>
> 作为托管客户或混合客户，请联系您的Adobe代表以配置此集成。 以下步骤仅适用于内部部署客户。

## 先决条件 {#prerequisites}

要使用Adobe Campaign与Adobe Target之间的集成，您必须：

* Adobe Experience Cloud和Adobe Target组织
* 指定用于建立与Adobe Campaign的连接的Adobe Targetrawbox

## 配置Adobe Campaign {#configuring-adobe-campaign}

要配置Adobe Campaign，请执行以下操作：

1. 安装 **[!UICONTROL Integration with the Adobe Experience Cloud]** 内置包。 [了解详情](../../platform/using/working-with-data-packages.md#importing-packages)

   利用此资源包，可通过Digital Asset Manager访问共享资产。

1. 启用通过IMS(Adobe ID连接服务)的连接，以在电子邮件中使用通过Adobe Experience Cloud共享的图像。 [了解详情](../../integrations/using/about-adobe-id.md)
1. 浏览到 **[!UICONTROL Administration > Platform > Options]** 要为Adobe Target配置服务器和组织（租户）选项，请执行以下操作：

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** :用于集成的Adobe Target服务器。 默认情况下，此选项已被选中。 此值对应于Adobe Target **[!UICONTROL Domain Server]**，后跟值 **/m2**. 例如： **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** :Adobe Target组织名称。 此值对应于Adobe Target的名称 **[!UICONTROL Client]**.


>[!CAUTION]
>
>对于混合和托管架构，必须在所有服务器(包括 [中间源服务器](../../installation/using/mid-sourcing-server.md) 和 [执行实例](../../message-center/using/configuring-instances.md#execution-instance).