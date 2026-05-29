---
product: campaign
title: 配置与Adobe Target的集成
description: 了解如何配置与Adobe Target的集成
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
TQID: https://experienceleague.adobe.com/k6TljRgymSefOITPaogJdR7HOrl1BnnZm9jbkemrcyg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 198
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

1. 安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;内置包。 [了解详情](../../platform/using/working-with-data-packages.md#importing-packages)

   通过此包，您可以通过Digital Asset Manager访问共享资产。

1. 启用通过IMS（Adobe ID连接服务）的连接，以在您的电子邮件中使用通过Adobe Experience Cloud共享的图像。 [了解详情](../../integrations/using/about-adobe-id.md)
1. 浏览到&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;以配置Adobe Target的服务器和组织（租户）选项：

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** ：用于集成的Adobe Target服务器。 默认情况下已选中此选项。 此值对应于Adobe Target **[!UICONTROL Domain Server]**，后跟值&#x200B;**/m2**。 例如： **tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** ：Adobe Target组织名称。 此值对应于Adobe Target **[!UICONTROL Client]**&#x200B;的名称。


>[!CAUTION]
>
>对于混合和托管架构，必须在所有服务器上设置这些选项，包括[中间源服务器](../../installation/using/mid-sourcing-server.md)和[执行实例](../../message-center/using/configuring-instances.md#execution-instance)。