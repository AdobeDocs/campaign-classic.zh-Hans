---
title: 使用Adobe Experience Cloud共享受众
seo-title: 使用Adobe Experience Cloud共享受众
description: 使用Adobe Experience Cloud共享受众
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 418a36cd51106dae2b4201c8b5abda9b05285a18

---


# 使用Adobe Experience Cloud共享受众{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>使用此集成需要实现IMS。 请查阅有关 [IMS的部分](../../integrations/using/about-adobe-id.md)。

Adobe Campaign允许您使用Adobe Experience cloud解决方案和核心服务交换和共享受众／细分。 为此，您需要将 **Adobe Campaign** 与People核心服务 **(也称为Profiles &amp; Audiences核心服务******)或Adobe Audience Manager相集成。 您随后将能够：

* 将不同Adobe Experience cloud解决方案中的共享受众／区段导入Adobe Campaign。 可以通过Adobe Campaign中的列表导入受众。
* 以Adobe Experience cloud共享受众的形式导出列表。 这些受众可用于您使用的不同Adobe Experience cloud解决方案。 在工作流中进行定位后，可使用专用活动导出受 **[!UICONTROL Update shared audience]** 众。

>[!CAUTION]
>
>根据数据类型，在Adobe Campaign中导入受众可能会受到法律限制。

该集成支持两种类型的Adobe Experience Cloud ID:

* **访客ID**:这种类型的标识符将Adobe Experience cloud访客与Adobe Campaign收件人进行协调。
* **声明的ID**:此类型标识符将所有类型的数据与Adobe Campaign数据库中的元素进行协调。 它在Adobe Campaign中表示为预定义的对帐密钥。
