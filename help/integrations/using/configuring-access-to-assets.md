---
title: 配置对资产的访问
seo-title: 配置对资产的访问
description: 配置对资产的访问
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 配置对资产的访问{#configuring-access-to-assets}

本节详细介绍了Adobe Campaign中使用与Assets核心服务或Adobe Experience Manager资产库集成功能所需的配置步骤。

>[!CAUTION]
>
>这些集成是并发的。 进行任何配置前，请仔细阅读以下信息。

* 与 **Experience Cloud Assets集成**:此集成允许您插入Adobe Experience cloud库中的图像。 根据您的配置和许可模式，此库可以是资产核心服务或资产（按需）。 必须通过在Adobe Campaign中安装 **[!UICONTROL Integration with the Adobe Experience Cloud]** 内置包来设置此集成。
* 与 **AEM资产集成**:此集成允许您从Adobe Experience Manager资产库插入图像。 必须通过在Adobe Campaign中安装 **[!UICONTROL AEM Integration]** 内置包来设置此集成。

>[!NOTE]
>
>如果安装了两个包(**[!UICONTROL AEM Integration]** 和 **[!UICONTROL Integration with the Adobe Experience Cloud]** )，则只能使用Adobe Experience cloud库中的可用资源。 要同时访问AEM资产库中的资产，您必须同步AEM资产和Adobe Experience Cloud。 随后，AEM资产中的资产也将显示在Adobe Experience cloud库中。 有关同步AEM资产和Adobe Experience cloud的更多信息，请参阅详细 [文档](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

## 与Experience Cloud Assets集成 {#integrating-with-experience-cloud-assets}

要使用Adobe Campaign和Experience Cloud资产之间的集成，您必须：

* Adobe Experience cloud组织
* 启用Adobe IMS身份验证模式

要启用Adobe Campaign与Adobe Experience Cloud之间的连接，请通过IMS（Adobe ID连接服务）配置连接。 通过Adobe ID连接文档 [中详细介绍了此配置](../../integrations/using/about-adobe-id.md) 。 它涉及：

* 安装包 **[!UICONTROL Integration with the Adobe Experience Cloud]** 。
* 配置Adobe Experience cloud外部帐户。

>[!NOTE]
>
>链接到此集成的功能仅对通过IMS与其Adobe ID连接的用户可用。

## 与AEM资产集成 {#integrating-with-aem-assets}

要将AEM资产与Adobe Campaign集成，您必须首先配置Adobe Experience manager与Adobe Campaign之间的集成。 此配置主要要求：

* 安装 **[!UICONTROL AEM Integration]** 内置包
* 配置特定于Adobe Experience manager的外部帐户

在详细文档中了解如何集成Adobe Campaign和Adobe Experience Manager [](../../integrations/using/about-adobe-experience-manager.md)。

设置此集成后，您可以在Adobe Campaign中配置新的分发模板以使用AEM资产库。 为此请执行以下操作步骤：

1. 创建新的分发模板——或复制现有的分发模板。 For more on Delivery templates, refer to [this page](../../delivery/using/about-templates.md).
1. 编辑此 **模板的** “属性”。
1. 在选 **[!UICONTROL Advanced]** 项卡中，将 **[!UICONTROL Content editing mode]** 设置 **为DCE**。
1. 选择您需 **[!UICONTROL AEM account]** 要用来访问AEM资产库的外部。

   ![](assets/dam_aem_assets1.png)

当您基于此模板将图像插入分发的内容时，该选 **[!UICONTROL Select a shared asset]** 项随后将允许您浏览AEM资产库中的图像。 在本节中了解 [更多信息](../../integrations/using/inserting-a-shared-asset.md)。

>[!NOTE]
>
>如果Adobe **[!UICONTROL Integration with the Adobe Experience Cloud]** Campaign实例中也安装了该包，则您只能使用Adobe Experience cloud库中的可用资产。 要同时访问AEM资产库中的资产，您必须同步AEM资产和Adobe Experience Cloud。 随后，AEM资产中的资产也将显示在Adobe Experience cloud库中。 在这种情况下，您无需创建特定的分发模板。 有关在AEM资产与Adobe Experience cloud之间同步的更多信息，请参阅详细 [文档](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

