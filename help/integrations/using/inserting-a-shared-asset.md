---
product: campaign
title: 插入共享资源
description: 插入共享资源
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: d399c4800fe6c5b128a6ccb5fec15262cbef5ee8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 插入共享资源{#inserting-a-shared-asset}

从Adobe Experience Cloud共享的资产可在电子邮件和登陆页面中使用，如下所示：

1. 创建新电子邮件或新登陆页面。

   如果您使用Adobe Experience Manager资产库中的资产，请使用在 [配置集成](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   如果您没有此特定模板，请确保在投放中 **属性**, **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** 选项卡) **DCE** 并且已提供要用于访问AEM Assets资源库的AEM外部帐户。

1. 在编辑窗口中，选择用于添加图像的选项：

   * 如果您使用 [标准编辑模式](../../delivery/using/defining-the-email-content.md#adding-images)，选择 **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * 如果您使用 [高级编辑模式](../../web/using/about-campaign-html-editor.md) (DCE)，转到图像块，然后通过上下文菜单，选择 **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >不能在 [Web访问](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 使用DCE时。

1. 在打开的选择窗口中，选择图像，然后进行确认。

   可用图像可能来自Adobe Experience Cloud库或AEM Assets库，具体取决于Adobe Campaign实例的配置方式。 请参阅 [配置对资产的访问权限](../../integrations/using/configuring-access-to-assets.md) 中。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果您使用与Adobe Target的集成，则可以将共享图像用作默认图像。 请参见[此页面](../../integrations/using/integrating-with-adobe-target.md)。
