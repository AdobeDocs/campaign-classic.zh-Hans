---
solution: Campaign Classic
product: campaign
title: 插入共享资源
description: 插入共享资源
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---


# 插入共享资源{#inserting-a-shared-asset}

从Adobe Experience Cloud共享的资源可在您的电子邮件和登陆页中使用，具体如下：

1. 创建新电子邮件或新登陆页。

   如果您使用Adobe Experience Manager资源库中的资源，请使用配置集成时 [创建的投放模板](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets)。

   如果您没有此特定模板，请确保在“投放属 **性**”中 **[!UICONTROL Content editing mode]** ,(选&#x200B;**[!UICONTROL Advanced]** 项卡)设置为 **“数字内容编辑器** ”，并提供您要用于访问AEM Assets资源库的AEM外部帐户。

1. 在编辑窗口中，选择添加图像的选项：

   * 如果您使用标准编 [辑模式](../../delivery/using/defining-the-email-content.md#adding-images)，请选择 **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**。

      ![](assets/dam_insert_image_standard.png)

   * 如果您使用高级 [编辑模式](../../web/using/about-campaign-html-editor.md) (数字内容编辑器)，请转到图像块，然后通过上下文菜单选择 **[!UICONTROL Select a shared asset]**。

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >使用Adobe Campaign时，无法在Web访 [问中插入](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) “数字内容编辑器”中的共享图像。

1. 在打开的选择窗口中，选择一个图像，然后进行确认。

   可用图像可能来自您的Adobe Experience Cloud图书馆或AEM Assets图书馆，具体取决于Adobe Campaign实例的配置方式。 请参阅配置 [对资产的访问](../../integrations/using/configuring-access-to-assets.md) 。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果您使用与Adobe Target的集成，则可以使用共享图像作为默认图像。 请参见[此页面](../../integrations/using/integrating-with-adobe-target.md)。

