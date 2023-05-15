---
product: campaign
title: 配置对资产的访问权限
description: 配置对资产的访问权限
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 2%

---

# 配置对资产的访问权限{#configuring-access-to-assets}



本节详细介绍Adobe Campaign中使用Assets核心服务或Adobe Experience Manager Assets(AEM Assets)库的集成功能所需的配置步骤。

>[!CAUTION]
>
>这些集成是并发的。 在进行任何配置之前，请仔细阅读以下信息。

* 与集成 **Experience Cloud资产**:此集成允许您从Adobe Experience Cloud库插入图像。 此集成必须通过安装 **[!UICONTROL Integration with the Adobe Experience Cloud]** Adobe Campaign中的内置包。
* 与集成 **AEM Assets**:此集成允许您从Adobe Experience Manager Assets库插入图像。 此集成必须通过安装 **[!UICONTROL AEM Integration]** Adobe Campaign中的内置包。 请注意，从Adobe Experience Manager 6.4开始，此集成不再可用。

>[!NOTE]
>
>如果两个包(**[!UICONTROL AEM Integration]** 和 **[!UICONTROL Integration with the Adobe Experience Cloud]** )，则只能使用Adobe Experience Cloud库中可用的资产。

## 与Experience Cloud资产集成 {#integrating-with-experience-cloud-assets}

要使用Adobe Campaign与Experience Cloud资产之间的集成，您必须：

* Adobe Experience Cloud组织
* 已启用Adobe IMS身份验证模式

要启用Adobe Campaign与Adobe Experience Cloud之间的连接，请通过IMS(Adobe ID连接服务)配置连接。 此配置详见 [通过Adobe ID连接](../../integrations/using/about-adobe-id.md) 文档。 它涉及：

* 安装 **[!UICONTROL Integration with the Adobe Experience Cloud]** 包。
* 配置Adobe Experience Cloud外部帐户。

>[!NOTE]
>
>与此集成关联的功能仅适用于通过IMS与其Adobe ID关联的用户。

## 与AEM Assets集成 {#integrating-with-aem-assets}


>[!CAUTION]
>
>此功能已从Adobe Experience Manager 6.4开始停用。 [了解更多](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=en#removed-features)

要将AEM Assets与Adobe Campaign集成，您必须先配置Adobe Experience Manager与Adobe Campaign之间的集成。 此配置主要要求：

* 安装 **[!UICONTROL AEM Integration]** 内置包
* 配置特定于Adobe Experience Manager的外部帐户

了解如何在中集成Adobe Campaign和Adobe Experience Manager [详细文档](../../integrations/using/about-adobe-experience-manager.md).

设置此集成后，您可以在Adobe Campaign中配置新的投放模板以使用AEM Assets库。 为此请执行以下操作步骤：

1. 创建新投放模板 — 或复制现有投放模板。 有关投放模板的更多信息，请参阅 [本页](../../delivery/using/about-templates.md).
1. 编辑 **属性** 模板。
1. 在 **[!UICONTROL Advanced]** 选项卡，设置 **[!UICONTROL Content editing mode]** to **DCE**.
1. 选择外部 **[!UICONTROL AEM account]** 用于访问AEM Assets库的ID。

   ![](assets/dam_aem_assets1.png)

在基于此模板将图像插入投放内容时， **[!UICONTROL Select a shared asset]** 然后，利用选项可浏览AEM Assets库中的图像。 在[此章节](../../integrations/using/inserting-a-shared-asset.md)中了解更多信息。

>[!NOTE]
>
>如果 **[!UICONTROL Integration with the Adobe Experience Cloud]** 包也会安装在Adobe Campaign实例上，您将只能使用Adobe Experience Cloud库中提供的资产。 要同时访问AEM Assets库中的资产，您必须同步AEM Assets和Adobe Experience Cloud。 随后，AEM Assets中的资产也将在Adobe Experience Cloud库中提供。 在这种情况下，您无需创建特定的投放模板。
