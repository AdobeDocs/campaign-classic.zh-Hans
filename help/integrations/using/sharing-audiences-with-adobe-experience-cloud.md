---
solution: Campaign Classic
product: campaign
title: 与Adobe Experience Cloud共享受众
description: 与Adobe Experience Cloud共享受众
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 40abbf1f981331b8a19d3607c57624aac22c91f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# 与Adobe Experience Cloud共享受众{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>要与Adobe Experience Cloud解决方案共享受众，您需要实施Adobe Identity Management系统。 [进一步了解IMS](../../integrations/using/about-adobe-id.md)。

借助Adobe Campaign，您可以与Adobe Experience Cloud解决方案和核心服务共享受众和细分。 有两个选项可用：

1. 将Adobe Experience Platform区段数据发送到Adobe Campaign。 要实施此集成，您需要将实时客户数据平台与活动(RTCDP)连接起来。 [在本节中了解更多信息](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html)。


1. 将&#x200B;**Adobe Campaign**&#x200B;与&#x200B;**People核心服务**(也称为&#x200B;**用户档案和受众核心服务**)或Adobe Audience Manager集成。 然后，您将能够：

   * 将不同Adobe Experience Cloud解决方案中的共享受众/区段导入Adobe Campaign。 受众可以在Adobe Campaign中通过列表导入。

   * 以Adobe Experience Cloud共享列表的形式导出受众。 这些受众可用于您使用的不同Adobe Experience Cloud解决方案。 受众在工作流中定位后可使用专用的&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活动导出。

此集成支持两种类型的Adobe Experience Cloud ID:

* **访客ID**:此类型的标识符将Adobe Experience Cloud访客与Adobe Campaign收件人协调。
* **声明的ID**:此类型的标识符将所有类型的数据与Adobe Campaign数据库中的元素进行协调。它在Adobe Campaign中表示为预定义合并关键项。

   >[!NOTE]
   >
   > 声明的ID数据源现在还可以与People核心服务集成一起使用。
   >
   >如果您使用People核心服务集成并想添加Audience Manager集成，则需要Adobe Audience Manager顾问的帮助，以避免在Adobe Audience Manager上下文中转换到使用此Declared ID数据源时收集的所有ID同步丢失。
