---
product: campaign
title: 与Adobe Experience Cloud共享受众
description: 与Adobe Experience Cloud共享受众
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 63%

---

# 与Adobe Experience Cloud共享受众{#sharing-audiences-with-adobe-experience-cloud}



>[!CAUTION]
>
>要与Adobe Experience Cloud解决方案共享受众，您需要实施AdobeIdentity Management System。 [了解有关IMS的更多信息](../../integrations/using/about-adobe-id.md).

借助Adobe Campaign，您可以与Adobe Experience Cloud解决方案和核心服务共享受众和区段。 提供了两个选项：

1. 将Adobe Experience Platform区段数据发送到Adobe Campaign。 要实施此集成，您需要将Real-time Customer Data Platform连接到Campaign (RTCDP)。 [在此章节中了解详情](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html)。

1. 集成 **Adobe Campaign** 替换为 **人员核心服务** (也称为 **配置文件和受众核心服务**)或Adobe Audience Manager。 然后，您将能够：

   * 从不同的 Adobe Experience Cloud 解决方案导入共享受众/区段到 Adobe Campaign 中。 可通过 Adobe Campaign 中的列表导入受众。

   * 以 Adobe Experience Cloud 共享受众的形式导出列表。您可在所用的不同 Adobe Experience Cloud 解决方案中使用这些受众。在工作流中完成定位后，可使用专门的 **[!UICONTROL Update shared audience]** 活动导出受众。

此集成支持两种类型的 Adobe Experience Cloud ID：

* **访客 ID**：此类标识符可协调 Adobe Experience Cloud 访客与 Adobe Campaign 收件人。
* **声明的 ID**：此类型的标识符会使所有类型的数据与 Adobe Campaign 数据库中的元素相协调。它在 Adobe Campaign 中表示为预定义的合并关键项。

   >[!NOTE]
   >
   > 声明的 ID 数据源现在还可以与 People 核心服务集成一起使用。
   >
   >如果您使用 People 核心服务集成，并想要添加 Audience Manager 集成，则需要 Adobe Audience Manager 顾问的帮助，以避免在 Adobe Audience Manager 环境中转换为使用此声明的 ID 数据源时收集的所有 ID 同步丢失。
