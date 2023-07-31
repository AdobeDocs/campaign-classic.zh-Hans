---
product: campaign
title: 插入共享资源
description: 插入共享资源
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 插入共享资源{#inserting-a-shared-asset}

从Adobe Experience Cloud共享的资源可用于您的电子邮件和登陆页，如下所示：

1. 创建新电子邮件或新登陆页面。

   如果您使用Adobe Experience Manager资源库中的资源，请使用在以下情况下创建的投放模板： [配置集成](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   如果您没有此特定模板，请确保在投放中执行以下操作 **属性**， **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** 选项卡)设置为 **DCE** 并且提供了要用于访问AEM Assets资源库的AEM外部帐户。

1. 在编辑窗口中，选择要添加图像的选项：

   * 如果您使用 [标准编辑模式](../../delivery/using/defining-the-email-content.md#adding-images)，选择 **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_standard.png)

   * 如果您使用 [高级编辑模式](../../web/using/about-campaign-html-editor.md) (DCE)，转到图像块，然后通过上下文菜单选择 **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >您无法在中插入来自Adobe Campaign的共享图像 [Web访问](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 使用DCE时。

1. 在打开的选择窗口中，选择一个图像，然后进行确认。

   可用的图像来自您的Adobe Experience Cloud库或AEM Assets库，具体取决于Adobe Campaign实例的配置方式。 请参阅 [配置对资产的访问权限](../../integrations/using/configuring-access-to-assets.md) 部分。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果与Adobe Target集成，则可以将共享图像用作默认图像。 请参见[此页面](../../integrations/using/integrating-with-adobe-target.md)。
