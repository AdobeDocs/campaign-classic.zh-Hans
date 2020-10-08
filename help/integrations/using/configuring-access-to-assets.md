---
title: 配置资产访问权限
seo-title: 配置资产访问权限
description: 配置资产访问权限
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 1%

---


# Configuring access to Assets{#configuring-access-to-assets}

本节详细介绍了在Adobe Campaign中使用与Assets核心服务或Adobe Experience Manager资产库集成功能的必要配置步骤。

>[!CAUTION]
>
>这些集成是并发的。 进行任何配置前，请仔细阅读以下信息。

* 与Experience Cloud **资产集成**:此集成允许您插入来自Adobe Experience Cloud图书馆的图像。 根据您的配置和许可模式，此库可以是Assets核心服务或Assets on Demand。 必须通过在Adobe Campaign中安装内 **[!UICONTROL Integration with the Adobe Experience Cloud]** 置包来设置此集成。
* 与 **AEM Assets**:此集成允许您插入来自Adobe Experience Manager资源库的图像。 必须通过在Adobe Campaign中安装内 **[!UICONTROL AEM Integration]** 置包来设置此集成。

>[!NOTE]
>
>如果安装了两个包&#x200B;**[!UICONTROL AEM Integration]** (和 **[!UICONTROL Integration with the Adobe Experience Cloud]** )，则只能使用Adobe Experience Cloud库中可用的资源。 要同时访问AEM Assets图书馆中的资源，必须同步AEM Assets和Adobe Experience Cloud。 AEM Assets的资产也将在Adobe Experience Cloud图书馆查阅。 有关同步AEM Assets和Adobe Experience Cloud的详细信息，请参阅详 [细文档](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

## 与Experience Cloud资产集成 {#integrating-with-experience-cloud-assets}

要使用Adobe Campaign和Experience Cloud资产之间的集成，您必须：

* Adobe Experience Cloud组织
* 启用AdobeIMS验证模式

要启用Adobe Campaign与Adobe Experience Cloud之间的连接，请通过IMS(Adobe ID连接服务)配置连接。 此配置在通过Adobe ID [文档连接中详细介绍](../../integrations/using/about-adobe-id.md) 。 它涉及：

* 正在安装 **[!UICONTROL Integration with the Adobe Experience Cloud]** 包。
* 配置Adobe Experience Cloud外部帐户。

>[!NOTE]
>
>与此集成相关的功能只适用于通过IMS与Adobe ID相连的用户。

## 与AEM Assets集成 {#integrating-with-aem-assets}

要将AEM Assets与Adobe Campaign集成，您必须首先配置Adobe Experience Manager与Adobe Campaign之间的集成。 此配置主要要求：

* 安装 **[!UICONTROL AEM Integration]** 内置包
* 配置特定于Adobe Experience Manager的外部帐户

在详细文档中了解如何整合Adobe Campaign [和Adobe Experience Manager](../../integrations/using/about-adobe-experience-manager.md)。

设置此集成后，您可以在Adobe Campaign中配置新投放模板以使用AEM Assets库。 为此请执行以下操作步骤：

1. 创建新投放模板-或重复现有的。 For more on Delivery templates, refer to [this page](../../delivery/using/about-templates.md).
1. 编辑此 **模板** 的属性。
1. 在选 **[!UICONTROL Advanced]** 项卡中，将 **[!UICONTROL Content editing mode]** 设置 **数字内容编辑器**。
1. 选择访问 **[!UICONTROL AEM account]** 您的AEM Assets图书馆时需要使用的外部。

   ![](assets/dam_aem_assets1.png)

当您根据此模板将图像插入投放内容时，该选 **[!UICONTROL Select a shared asset]** 项随后将允许您浏览AEM Assets库中的图像。 在本节中了 [解更多](../../integrations/using/inserting-a-shared-asset.md)。

>[!NOTE]
>
>如果Adobe Campaign **[!UICONTROL Integration with the Adobe Experience Cloud]** 实例中也安装了该包，则您将只能使用Adobe Experience Cloud库中提供的资源。 要同时访问AEM Assets图书馆中的资源，必须同步AEM Assets和Adobe Experience Cloud。 AEM Assets的资产也将在Adobe Experience Cloud图书馆查阅。 在这种情况下，您无需创建特定投放模板。 有关在AEM Assets和Adobe Experience Cloud之间同步的详细信息，请参阅详 [细文档](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

