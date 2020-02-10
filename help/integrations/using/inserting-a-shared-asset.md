---
title: 插入共享资源
seo-title: 插入共享资源
description: 插入共享资源
seo-description: null
page-status-flag: never-activated
uuid: ab661bfd-d0a3-4b5c-ba52-4c76c834d584
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: 3d01cc7e-5685-4101-bf4b-ef5f6e52b3c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 插入共享资源{#inserting-a-shared-asset}

从Adobe Experience Cloud共享的资产可在您的电子邮件和登录页面中使用，如下所示：

1. 创建新电子邮件或新登录页面。

   如果您使用Adobe Experience Manager资产库中的资产，请使用配置集成时创建 [的交付模板](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets)。

   如果您没有此特定模板，请确保在交付属性 **（选项卡）中，将**（选项卡）设置为 **[!UICONTROL Content editing mode]** DCE **[!UICONTROL Advanced]****** ，并且提供了要用于访问AEM资产资源库的AEM外部帐户。

1. 在编辑窗口中，选择添加图像的选项：

   * 如果您使用标准编 [辑模式](../../delivery/using/defining-the-email-content.md#adding-images)，请选择 **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**。

      ![](assets/dam_insert_image_standard.png)

   * 如果您使用高 [级编辑模式](../../web/using/about-campaign-html-editor.md) (DCE)，请转至图像块，然后通过上下文菜单选择 **[!UICONTROL Select a shared asset]**。

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >使用DCE时，无法在Web访问中 [插入](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) Adobe Campaign中的共享图像。

1. 在打开的选择窗口中，选择一个图像，然后进行确认。

   可用图像可能来自您的Adobe Experience cloud库或AEM资产库，具体取决于您的Adobe Campaign实例的配置方式。 请参阅配置 [对资产的访问权限](../../integrations/using/configuring-access-to-assets.md) 。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果您使用与Adobe target的集成，则可以将共享图像用作默认图像。 请参见[此页面](../../integrations/using/integrating-with-adobe-target.md)。

