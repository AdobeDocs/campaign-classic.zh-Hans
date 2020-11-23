---
solution: Campaign Classic
product: campaign
title: 与Adobe Experience Cloud共享受众
description: 与Adobe Experience Cloud共享受众
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>要与Adobe Experience Cloud解决方案共享受众，您需要实施AdobeIdentity Management系统。 [进一步了解IMS](../../integrations/using/about-adobe-id.md)。

通过Adobe Campaign，您可以与Adobe Experience Cloud解决方案和核心服务共享受众和细分。 有两种选项可用：

1. 将Adobe Experience Platform细分数据发送给Adobe Campaign。 要实施此集成，您需要将实时客户数据平台与活动(RTCDP)连接。 [在本节中了解更多信息](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html)。


1. 将 **Adobe Campaign****与People核心服务** (也称为 **用户档案和受众核心服务**)或Adobe Audience Manager集成。 然后，您将能够：

   * 将共享受众/区段从不同的Adobe Experience Cloud解决方案导入Adobe Campaign。 受众可以通过Adobe Campaign中的列表导入。

   * 以Adobe Experience Cloud共享列表形式导出受众。 这些受众可用于您使用的不同Adobe Experience Cloud解决方案。 受众在工作流中定位后，可使用专用活动导 **[!UICONTROL Update shared audience]** 出。

此集成支持两种类型的Adobe Experience CloudID:

* **访客ID**:此类标识符将Adobe Experience Cloud访客与Adobe Campaign收件人协调。
* **声明的ID**:此类型的标识符将所有类型的数据与Adobe Campaign库中的元素进行协调。 它以Adobe Campaign表示为预定义合并关键项。
