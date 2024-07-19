---
product: campaign
title: 使用Adobe Campaign和Adobe Analytics
description: 使用Adobe Campaign和Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
source-git-commit: a38d53f4b37aadbc53446b5e399af2eae56c12af
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 13%

---

# 使用Adobe Campaign和Adobe Analytics {#adobe-analytics-connector-gs}

Adobe Analytics Connector 允许 Adobe Campaign 和 Adobe Analytics 通过 **[!UICONTROL Web Analytics connectors]** 包进行交互。它会以区段形式将数据转发到Adobe Campaign，这些区段涉及到营销活动后的用户行为。 反过来，它会将Adobe Campaign交付的营销活动的指标和属性发送到Adobe Analytics。

## 护栏和先决条件 {#adobe-analytics-connector-guardrails}

在开始使用Adobe Campaign-Adobe Analytics连接器之前，请考虑以下护栏和先决条件。

* 对于此集成，需要使用AdobeIdentity Management System (IMS)连接到Campaign。 [了解详情](../../integrations/using/about-adobe-id.md)。

* Adobe Analytics Connector 与事务性消息传递（消息中心）不兼容。

* 必须通过专用软件包在您的环境中安装Web Analytics连接器加载项。

   * 对于混合和内部部署实施，请确保遵循此[页面](adobe-analytics-provisioning.md)中详述的配置步骤。
   * 作为托管或托管Cloud Service用户，请联系Adobe以将Campaign与Adobe Experience Cloud服务和解决方案配合使用。


## 配置和使用情况 {#adobe-analytics-connector-usage}

要启用此集成，必须创建您的Adobe技术帐户，如[此页面](oauth-technical-account.md)中所详述。

请参阅[Adobe Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}以了解如何使用Adobe Campaign和Adobe Analytics。
