---
solution: Campaign Classic
product: campaign
title: 配置对资产的访问权限
description: 配置对资产的访问权限
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 5d5d4b87bae44ce0a93458f79179434a5bf315c3
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---


# 配置对资产{#configuring-access-to-assets}的访问

本节详细介绍Adobe Campaign中使用Assets核心服务或Adobe Experience Manager资源库集成功能所需的配置步骤。

>[!CAUTION]
>
>这些集成是并行的。 进行任何配置前，请仔细阅读以下信息。

* 与&#x200B;**Experience Cloud资产**&#x200B;集成：此集成允许您插入Adobe Experience Cloud库中的图像。 根据您的配置和许可模式，此库可以是Assets核心服务或Assets on Demand。 必须通过在Adobe Campaign中安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;内置包来设置此集成。
* 与&#x200B;**AEM Assets**&#x200B;集成：此集成允许您插入Adobe Experience Manager资源库中的图像。 必须通过在Adobe Campaign中安装&#x200B;**[!UICONTROL AEM Integration]**&#x200B;内置包来设置此集成。

>[!NOTE]
>
>如果安装了两个包（**[!UICONTROL AEM Integration]**&#x200B;和&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**），则只能使用Adobe Experience Cloud库中可用的资源。 要同时访问AEM Assets库中的资源，必须同步AEM Assets和Adobe Experience Cloud。 AEM Assets中的资源随后也可在Adobe Experience Cloud库中使用。 有关同步AEM Assets和Adobe Experience Cloud的详细信息，请参阅[详细文档](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

## 与Experience Cloud资产{#integrating-with-experience-cloud-assets}集成

要使用Adobe Campaign和Experience Cloud资产之间的集成，您必须：

* Adobe Experience Cloud组织
* 已启用AdobeIMS验证模式

要启用Adobe Campaign与Adobe Experience Cloud之间的连接，请通过IMS(Adobe ID连接服务)配置连接。 此配置详见[通过Adobe ID](../../integrations/using/about-adobe-id.md)文档连接。 它涉及：

* 正在安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包。
* 配置Adobe Experience Cloud外部帐户。

>[!NOTE]
>
>与此集成关联的功能仅适用于通过IMS与Adobe ID连接的用户。

## 与AEM Assets{#integrating-with-aem-assets}集成

要将AEM Assets与Adobe Campaign集成，您必须首先配置Adobe Experience Manager与Adobe Campaign之间的集成。 此配置主要要求：

* 安装&#x200B;**[!UICONTROL AEM Integration]**&#x200B;内置包
* 配置特定于Adobe Experience Manager的外部帐户

了解如何在[详细文档](../../integrations/using/about-adobe-experience-manager.md)中集成Adobe Campaign和Adobe Experience Manager。

设置此集成后，您可以在Adobe Campaign中配置新投放模板以使用AEM Assets库。 为此请执行以下操作步骤：

1. 创建新投放模板 — 或重复现有的。 有关投放模板的详细信息，请参阅[此页](../../delivery/using/about-templates.md)。
1. 编辑此模板的&#x200B;**属性**。
1. 在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中，将&#x200B;**[!UICONTROL Content editing mode]**&#x200B;设置为&#x200B;**数字内容编辑器**。
1. 选择访问AEM Assets库时需要使用的外部&#x200B;**[!UICONTROL AEM account]**。

   ![](assets/dam_aem_assets1.png)

当您基于此模板将图像插入投放内容时，**[!UICONTROL Select a shared asset]**&#x200B;选项随后将允许您浏览AEM Assets库中的图像。 请阅读[本节](../../integrations/using/inserting-a-shared-asset.md)了解更多信息。

>[!NOTE]
>
>如果您的Adobe Campaign实例中也安装了&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包，则您只能使用Adobe Experience Cloud库中的可用资源。 要同时访问AEM Assets库中的资源，必须同步AEM Assets和Adobe Experience Cloud。 AEM Assets中的资源随后也可在Adobe Experience Cloud库中使用。 在这种情况下，您无需创建特定投放模板。 有关在AEM Assets和Adobe Experience Cloud之间同步的详细信息，请参阅[详细文档](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html#integration)。


