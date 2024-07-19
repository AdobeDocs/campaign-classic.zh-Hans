---
product: campaign
title: 与Adobe Experience Cloud共享受众
description: 与Adobe Experience Cloud共享受众
feature: Audiences
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 50%

---

# 与Adobe Experience Cloud共享受众 {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>要与Adobe Experience Cloud解决方案共享受众，您需要实施AdobeIdentity Management System。 [了解有关IMS的更多信息](../../integrations/using/about-adobe-id.md)。

通过Adobe Campaign，您可以与Adobe Experience Cloud服务共享受众和区段。 提供了两个选项：

1. 将Adobe Experience Platform区段数据发送到Adobe Campaign。 要实施此集成，您需要将Real-time Customer Data Platform连接到Campaign (RTCDP)。 [在本节中了解详情](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html){target="_blank"}。

1. 将&#x200B;**Adobe Campaign**&#x200B;与&#x200B;**Experience Cloud受众**&#x200B;或&#x200B;**Adobe Audience Manager**&#x200B;集成。 然后，您将能够：

   * 从不同的 Adobe Experience Cloud 解决方案导入共享受众/区段到 Adobe Campaign 中。 可通过 Adobe Campaign 中的列表导入受众。

   * 以 Adobe Experience Cloud 共享受众的形式导出列表。您可在所用的不同 Adobe Experience Cloud 解决方案中使用这些受众。在工作流中完成定位后，可使用专门的 **[!UICONTROL Update shared audience]** 活动导出受众。

此集成支持两种类型的 Adobe Experience Cloud ID：

* **访客 ID**：此类标识符可协调 Adobe Experience Cloud 访客与 Adobe Campaign 收件人。
* **声明的 ID**：此类型的标识符会使所有类型的数据与 Adobe Campaign 数据库中的元素相协调。它在 Adobe Campaign 中表示为预定义的合并关键项。

  >[!NOTE]
  >
  > “声明的ID”数据源现在还可以与Experience CloudAssets集成一起使用。
  >
