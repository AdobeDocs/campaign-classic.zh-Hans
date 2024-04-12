---
product: campaign
title: 配置与Adobe Target的集成
description: 了解如何配置与Adobe Target的集成
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# 配置与Adobe Target的集成{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> 作为托管或混合型客户，请联系您的Adobe代表以配置此集成。 以下步骤仅适用于内部部署客户。

此集成需要：

* Adobe Experience Cloud和Adobe Target组织
* 为与Adobe Campaign建立连接而指定的Adobe Target rawbox

要在Adobe Campaign中配置此集成，请执行以下步骤：

1. 安装 **[!UICONTROL Integration with the Adobe Experience Cloud]** 内置包。 [了解详情](../../platform/using/working-with-data-packages.md#importing-packages)

   通过此包，您可以通过Digital Asset Manager访问共享资产。

1. 启用通过IMS(Adobe ID连接服务)的连接，以在您的电子邮件中使用通过Adobe Experience Cloud共享的图像。 [了解详情](../../integrations/using/about-adobe-id.md)
1. 浏览至 **[!UICONTROL Administration > Platform > Options]** 要为Adobe Target配置服务器和组织（租户）选项，请执行以下操作：

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** ：用于集成的Adobe Target服务器。 默认情况下已选中此选项。 此值对应于Adobe Target **[!UICONTROL Domain Server]**，后跟值 **/m2**. 例如： **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** ：Adobe Target组织名称。 此值对应于Adobe Target的名称 **[!UICONTROL Client]**.


>[!CAUTION]
>
>对于混合和托管体系结构，必须在所有服务器上设置这些选项，包括 [中间源服务器](../../installation/using/mid-sourcing-server.md) 和 [执行实例](../../message-center/using/configuring-instances.md#execution-instance).