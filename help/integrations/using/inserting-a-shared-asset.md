---
product: campaign
title: 插入共享资源
description: 插入共享资源
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
TQID: https://experienceleague.adobe.com/5SrvIw1sYSNd4Hw1we554AfxDj3VgeTeqIOOzTTrWuY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 233
ht-degree: 1%

---

# 插入共享资源{#inserting-a-shared-asset}

从Adobe Experience Cloud共享的Assets可用于您的电子邮件和登陆页，如下所示：

1. 创建新电子邮件或新登陆页面。

   如果使用Adobe Experience Manager资源库中的资源，请使用在[配置集成](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets)时创建的投放模板。

   如果您没有此特定模板，请确保在投放&#x200B;**Properties**&#x200B;中将&#x200B;**[!UICONTROL Content editing mode]** （**[!UICONTROL Advanced]**&#x200B;选项卡）设置为&#x200B;**DCE**，并且提供了要用于访问AEM Assets资源库的AEM外部帐户。

1. 在编辑窗口中，选择要添加图像的选项：

   * 如果您使用[标准编辑模式](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html#adding-images){target="_blank"}，请选择&#x200B;**[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**。

     ![](assets/dam_insert_image_standard.png)

   * 如果您使用[高级编辑模式](../../web/using/about-campaign-html-editor.md) (DCE)，请转到图像块，然后通过上下文菜单选择&#x200B;**[!UICONTROL Select a shared asset]**。

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >使用DCE时，无法在[Web访问](../../platform/using/adobe-campaign-workspace.md#console-and-web-access)中插入来自Adobe Campaign的共享图像。

1. 在打开的选择窗口中，选择一个图像，然后进行确认。

   可用的图像来自您的Adobe Experience Cloud库或AEM Assets库，具体取决于Adobe Campaign实例的配置方式。 请参阅[配置对Assets的访问权限](../../integrations/using/configuring-access-to-assets.md)部分。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果与Adobe Target集成，则可以将共享图像用作默认图像。 请参见[此页面](../../integrations/using/integrating-with-adobe-target.md)。
