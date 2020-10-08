---
title: 与Adobe Experience Cloud共享受众
seo-title: 与Adobe Experience Cloud共享受众
description: 与Adobe Experience Cloud共享受众
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>使用此集成需要实现IMS。 请查阅有关IMS [的部分](../../integrations/using/about-adobe-id.md)。

Adobe Campaign允许您与Adobe Experience Cloud解决方案和核心服务交换和共享受众/细分。 为此，您需要将Adobe Campaign **与People****核心服务** (也称为 **用户档案和受众核心服务**)或Adobe Audience Manager相集成。 然后，您将能够：

* 将共享受众/区段从不同的Adobe Experience Cloud解决方案导入Adobe Campaign。 受众可以通过Adobe Campaign中的列表导入。
* 以Adobe Experience Cloud共享列表形式导出受众。 这些受众可用于您使用的不同Adobe Experience Cloud解决方案。 受众在工作流中定位后，可使用专用活动导 **[!UICONTROL Update shared audience]** 出。

>[!CAUTION]
>
>根据Adobe Campaign的受众类型，在中导入数据可能受法律限制。

集成支持两种类型的Adobe Experience CloudID:

* **访客ID**:此类标识符将Adobe Experience Cloud访客与Adobe Campaign收件人协调。
* **声明的ID**:此类型的标识符将所有类型的数据与Adobe Campaign库中的元素进行协调。 它以Adobe Campaign表示为预定义合并关键项。
