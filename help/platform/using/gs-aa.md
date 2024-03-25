---
product: campaign
title: 使用Adobe Campaign和AdobeAnalytics
description: 使用Adobe Campaign和Adobe Analytics
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Analytics Integration
role: User, Admin
level: Beginner
source-git-commit: 59156851156338c9462781d31ce81a651362f2da
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 26%

---

# 使用Adobe Campaign和Adobe Analytics {#adobe-analytics-connector-gs}

Adobe Analytics Connector 允许 Adobe Campaign 和 Adobe Analytics 通过 **[!UICONTROL Web Analytics connectors]** 包进行交互。它会以区段形式将数据转发到Adobe Campaign，这些区段涉及到营销活动后的用户行为。 反过来，它会将Adobe Campaign交付的营销活动的指标和属性发送到Adobe Analytics。

## 护栏和先决条件 {#adobe-analytics-connector-guardrails}

在开始使用Adobe Campaign-Adobe Analytics连接器之前，请考虑以下护栏和先决条件。

* 对于此集成，需要使用AdobeIdentity Management System (IMS)连接到Campaign。 [了解详情](../../integrations/using/about-adobe-id.md)。

* Adobe Analytics Connector 与事务性消息传递（消息中心）不兼容。

* 必须通过专用软件包在您的环境中安装Web Analytics连接器加载项。

   * 对于混合和内部部署实施，请确保遵循此[页面](../../platform/using/adobe-analytics-provisioning.md)中详述的配置步骤。
   * 作为托管或托管Cloud Service用户，请联系Adobe以将Campaign与Adobe Experience Cloud服务和解决方案配合使用。


## 配置和使用情况 {#adobe-analytics-connector-usage}

了解如何在中使用Adobe Campaign和Adobe Analytics [Adobe Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.

