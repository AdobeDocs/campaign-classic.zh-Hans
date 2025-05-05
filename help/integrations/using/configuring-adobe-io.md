---
product: campaign
title: 为Adobe Experience Cloud Triggers配置Developer Console
description: 了解如何配置Developer Console Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---

# 为Adobe Experience Cloud Triggers配置Developer Console {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## 先决条件 {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

在开始此实施之前，请检查您是否拥有：

* 有效的&#x200B;**组织标识符**：组织ID是Adobe Experience Cloud中的唯一标识符，用于VisitorID服务和IMS单点登录(SSO)。 [了解详情](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-hans)
* 您组织的&#x200B;**开发人员访问权限**。 组织的系统管理员需要遵循此页面[&#128279;](https://helpx.adobe.com/cn/enterprise/using/manage-developers.html)中详细的的&#x200B;**将开发人员添加到单个产品配置文件**&#x200B;过程，以便为与触发器关联的Adobe Analytics产品的`Analytics - {tenantID}`产品配置文件提供开发人员访问权限。

## 步骤1：创建/更新OAuth项目 {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> Adobe已弃用服务帐户(JWT)凭据，Campaign与Adobe解决方案和应用程序的集成现在必须依赖OAuth服务器到服务器凭据。 </br>
>
> * 如果您已实施与Campaign的入站集成，则必须迁移技术帐户，如[本文档](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank)中所述。 现有的[服务帐户(JWT)凭据](oauth-technical-account.md)将继续工作到2025年1月27日。</br>
>
> * 如果您实施了叫客集成，如Campaign-Analytics集成或Experience Cloud Triggers集成，则在2025年1月27日之前它们将继续工作。 但是，在该日期之前，您必须将Campaign环境升级到v7.4.1，并将技术帐户迁移到oAuth。

要继续配置Adobe Analytics连接器，请访问Adobe Developer控制台并创建您的OAuth服务器到服务器项目。

有关详细信息，请参阅[此页面](oauth-technical-account.md#oauth-service)。

## 步骤2：在Adobe Campaign中添加项目凭据 {#add-credentials-campaign}

按照[此页面](oauth-technical-account.md#add-credentials)中详述的步骤进行操作，以在Adobe Campaign中添加您的OAuth项目凭据。

## 步骤3：更新管道标记 {#update-pipelined-tag}

要更新[!DNL pipelined]标记，您需要将身份验证类型更新到配置文件&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的开发人员控制台项目，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```

然后，运行`config -reload`并重新启动[!DNL pipelined]以考虑更改。
