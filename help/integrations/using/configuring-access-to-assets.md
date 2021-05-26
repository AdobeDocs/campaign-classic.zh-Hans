---
solution: Campaign Classic
product: campaign
title: 配置对资产的访问权限
description: 配置对资产的访问权限
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 1%

---

# 配置对Assets的访问{#configuring-access-to-assets}

本节详细介绍Adobe Campaign中使用Assets核心服务或Adobe Experience Manager Assets库集成功能所需的配置步骤。

>[!CAUTION]
>
>这些集成是并发的。 在进行任何配置之前，请仔细阅读以下信息。

* 与&#x200B;**Experience Cloud资产**&#x200B;集成：此集成允许您从Adobe Experience Cloud库插入图像。 根据您的配置和许可模式，此库可以是Assets核心服务或Assets on Demand。 必须通过在Adobe Campaign中安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;内置包来设置此集成。
* 与&#x200B;**AEM Assets**&#x200B;集成：此集成允许您从Adobe Experience Manager资产库插入图像。 必须通过在Adobe Campaign中安装&#x200B;**[!UICONTROL AEM Integration]**&#x200B;内置包来设置此集成。

>[!NOTE]
>
>如果安装了两个包（**[!UICONTROL AEM Integration]**&#x200B;和&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**），则只能使用Adobe Experience Cloud库中的可用资产。

## 与Experience Cloud资产集成{#integrating-with-experience-cloud-assets}

要使用Adobe Campaign与Experience Cloud资产之间的集成，您必须：

* Adobe Experience Cloud组织
* 已启用AdobeIMS身份验证模式

要启用Adobe Campaign与Adobe Experience Cloud之间的连接，请通过IMS(Adobe ID连接服务)配置连接。 [通过Adobe ID](../../integrations/using/about-adobe-id.md)连接文档中详细介绍了此配置。 它涉及：

* 安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包。
* 配置Adobe Experience Cloud外部帐户。

>[!NOTE]
>
>与此集成关联的功能仅适用于通过IMS与其Adobe ID关联的用户。

## 与AEM Assets集成{#integrating-with-aem-assets}

要将AEM Assets与Adobe Campaign集成，您必须先配置Adobe Experience Manager与Adobe Campaign之间的集成。 此配置主要要求：

* 安装&#x200B;**[!UICONTROL AEM Integration]**&#x200B;内置软件包
* 配置特定于Adobe Experience Manager的外部帐户

在[详细文档](../../integrations/using/about-adobe-experience-manager.md)中了解如何集成Adobe Campaign和Adobe Experience Manager。

设置此集成后，您可以在Adobe Campaign中配置新的投放模板以使用AEM Assets库。 为此请执行以下操作步骤：

1. 创建新投放模板 — 或复制现有投放模板。 有关投放模板的更多信息，请参阅[此页面](../../delivery/using/about-templates.md)。
1. 编辑此模板的&#x200B;**属性**。
1. 在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中，将&#x200B;**[!UICONTROL Content editing mode]**&#x200B;设置为&#x200B;**DCE**。
1. 选择访问AEM Assets库时需要使用的外部&#x200B;**[!UICONTROL AEM account]**。

   ![](assets/dam_aem_assets1.png)

当您基于此模板将图像插入投放内容时，**[!UICONTROL Select a shared asset]**&#x200B;选项随后将允许您浏览AEM Assets库中的图像。 在[此部分](../../integrations/using/inserting-a-shared-asset.md)中了解详情。

>[!NOTE]
>
>如果您的Adobe Campaign实例上也安装了&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包，则您将只能使用Adobe Experience Cloud库中可用的资产。 要同时访问AEM Assets库中的资产，您必须同步AEM Assets和Adobe Experience Cloud。 随后，AEM Assets中的资产也将在Adobe Experience Cloud库中提供。 在这种情况下，您无需创建特定的投放模板。 有关在AEM Assets和Adobe Experience Cloud之间同步的更多信息，请参阅[详细文档](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html#integration)。
