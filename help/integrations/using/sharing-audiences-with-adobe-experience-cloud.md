---
product: campaign
title: 与Adobe Experience Cloud共享受众
description: 与Adobe Experience Cloud共享受众
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 6%

---

# 与Adobe Experience Cloud共享受众{#sharing-audiences-with-adobe-experience-cloud}

![](../../assets/common.svg)

>[!CAUTION]
>
>要与Adobe Experience Cloud解决方案共享受众，您需要实施AdobeIdentity Management系统。 [进一步了解IMS。](../../integrations/using/about-adobe-id.md).

通过Adobe Campaign，您可以与Adobe Experience Cloud解决方案和核心服务共享受众和区段。 有两个选项可用：

1. 将Adobe Experience Platform区段数据发送到Adobe Campaign。 要实施此集成，您需要将Real-time Customer Data Platform与Campaign(RTCDP)连接起来。 [在本节中了解详情](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).


1. 集成 **Adobe Campaign** with **People核心服务** (也称为 **Profiles &amp; Audiences核心服务**)或Adobe Audience Manager。 然后，您将能够：

   * 将不同Adobe Experience Cloud解决方案中的共享受众/区段导入Adobe Campaign。 受众可通过Adobe Campaign中的列表导入。

   * 以Adobe Experience Cloud共享受众的形式导出列表。 这些受众可在您使用的不同Adobe Experience Cloud解决方案中使用。 可在工作流中使用专用的 **[!UICONTROL Update shared audience]** 活动。

此集成支持两种类型的Adobe Experience Cloud ID:

* **访客ID**:此类标识符可协调Adobe Experience Cloud访客与Adobe Campaign收件人。
* **声明的ID**:此类型的标识符将所有类型的数据与Adobe Campaign数据库中的元素进行协调。 它在Adobe Campaign中表示为预定义的对帐密钥。

   >[!NOTE]
   >
   > Declared ID 数据源现在还可以与 People 核心服务集成一起使用。
   >
   >如果您使用“人员”核心服务集成并想要添加Audience Manager集成，则需要Adobe Audience Manager顾问的帮助，以避免在Adobe Audience Manager上下文中转换到使用此声明的ID数据源时收集的所有ID同步丢失。
