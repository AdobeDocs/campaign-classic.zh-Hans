---
product: campaign
title: 配置对Assets的访问权限
description: 配置对Assets的访问权限
feature: Asset Sharing
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---

# 配置对Assets的访问权限 {#configuring-access-to-assets}

此部分详细介绍Adobe Campaign中的必要配置步骤，以便能够将集成功能与Assets或Adobe Experience Manager Assets (AEM Assets)库一起使用。

>[!CAUTION]
>
>这些集成是并发的。 在进行任何配置之前，请仔细阅读以下信息。

* 与&#x200B;**Experience CloudAssets**&#x200B;集成：此集成允许您从Adobe Experience Cloud库插入图像。 必须通过在Adobe Campaign中安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;内置包来设置此集成。
* 与&#x200B;**AEM Assets**&#x200B;集成：此集成允许您从Adobe Experience Manager Assets库插入图像。 必须通过在Adobe Campaign中安装&#x200B;**[!UICONTROL AEM Integration]**&#x200B;内置包来设置此集成。 请注意，从Adobe Experience Manager 6.4开始，此集成不再可用。

>[!NOTE]
>
>如果已安装两个包（**[!UICONTROL AEM Integration]**&#x200B;和&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]** ），则只能使用Adobe Experience Cloud库中的可用资源。

## 与Experience CloudAssets集成 {#integrating-with-experience-cloud-assets}

要使用Adobe Campaign与Experience CloudAssets之间的集成，您必须具有：

* Adobe Experience Cloud组织
* 已启用Adobe IMS身份验证模式

要启用Adobe Campaign与Adobe Experience Cloud之间的连接，请通过IMS(Adobe ID连接服务)配置连接。 有关该配置的详情，请参阅[通过Adobe ID连接](../../integrations/using/about-adobe-id.md)文档。 它涉及：

* 正在安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包。
* 配置Adobe Experience Cloud外部帐户。

>[!NOTE]
>
>与此集成关联的功能仅适用于通过IMS连接到Adobe ID的用户。

## 与AEM Assets集成 {#integrating-with-aem-assets}


>[!CAUTION]
>
>此功能已从Adobe Experience Manager 6.4开始停用。[了解详情](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

要将AEM Assets与Adobe Campaign集成，您必须首先配置Adobe Experience Manager与Adobe Campaign之间的集成。 此配置主要需要：

* 正在安装&#x200B;**[!UICONTROL AEM Integration]**&#x200B;内置包
* 配置特定于Adobe Experience Manager的外部帐户

请参阅[详细文档](../../integrations/using/about-adobe-experience-manager.md)以了解如何集成Adobe Campaign和Adobe Experience Manager。

设置此集成后，您可以在Adobe Campaign中配置新的投放模板以使用AEM Assets库。 为此请执行以下操作步骤：

1. 创建新投放模板 — 或复制现有模板。 有关投放模板的详细信息，请参阅[此页面](../../delivery/using/about-templates.md)。
1. 编辑此模板的&#x200B;**属性**。
1. 在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中，将&#x200B;**[!UICONTROL Content editing mode]**&#x200B;设置为&#x200B;**DCE**。
1. 选择访问AEM Assets库所需的外部&#x200B;**[!UICONTROL AEM account]**。

   ![](assets/dam_aem_assets1.png)

当您基于此模板将图像插入投放的内容时，**[!UICONTROL Select a shared asset]**&#x200B;选项将允许您浏览AEM Assets库中的图像。 可在[此部分](../../integrations/using/inserting-a-shared-asset.md)中了解详情。

>[!NOTE]
>
>如果&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包也安装在您的Adobe Campaign实例上，则您只能使用Adobe Experience Cloud库中可用的资源。 要同时访问AEM Assets库中的资源，必须同步AEM Assets和Adobe Experience Cloud。 随后，AEM Assets中的资源也将在Adobe Experience Cloud库中可用。 在这种情况下，您无需创建特定的投放模板。
