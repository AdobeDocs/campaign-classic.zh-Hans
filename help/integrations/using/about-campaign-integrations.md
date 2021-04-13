---
solution: Campaign Classic
product: campaign
title: 关于 Campaign 集成
description: 使用其他 Adobe 解决方案，并将其不同的功能与 Campaign 相结合。
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
translation-type: tm+mt
source-git-commit: 326ccbad77f3bd03a8eba22d7714084d52d2f02b
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 9%

---

# 开始使用Adobe Campaign集成{#about-campaign-integrations}

Adobe Experience Cloud是一套全面的一流集成解决方案，构建在通用数据平台上，并具有一套通用的强大核心服务。

了解Adobe Campaign与[Adobe Experience Cloud解决方案](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html)和[核心服务](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)之间可用的功能集成。 然后，您可以现代化解决方案实施并实施Experience Cloud，以便您能够使用客户属性和受众等功能。

![](assets/ExCloud-solutions.png)

[本节](#experience-cloud-integrations)提供可与Adobe Campaign集成的Adobe解决方案和核心服务的完整列表以及相关文档。

>[!CAUTION]
>
>大多数这些集成需要实施Adobe Identity Management系统(IMS)，才能通过Adobe ID登录。 [在本页中了解更多信息](../../integrations/using/about-adobe-id.md)。


## 链接您的解决方案{#working-with-experience-cloud-solutions}

可以将多个解决方案链接到Adobe Experience Cloud。 **organization**&#x200B;是允许管理员配置组和用户以及控制Adobe Experience Cloud中的单点登录(SSO)的客户实体。 该组织的作用类似于跨所有Experience Cloud产品和解决方案的登录公司。 大多数情况下，组织是您的公司名称。但是，公司可以有许多组织。

[Adobe Experience Cloud帮助门户](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)中详细介绍了组织管理和链接Adobe Experience Cloud帐户。

## 标识和Cookie管理{#id-and-cookies}

在安装Adobe Campaign或将现有安装与Adobe Experience Cloud集成时，将启用[Adobe Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/id-service/using/home.html)。 此服务取代了首先由Adobe Campaign跟踪功能使用的永久Cookie。

Adobe Experience Cloud Identity Service（ID服务）提供通用的永久ID，用于在Experience Cloud中的所有解决方案中标识您的访客。

将为生成访客的收件人分配唯一的跟踪日志ID。 此ID将保存在&#x200B;**[!UICONTROL nms:trackingLogRcp]**&#x200B;表的&#x200B;**[!UICONTROL Requester UUID (@sourceID)]**&#x200B;字段中。 **因此，在实施访客ID服务之前存在的收件人的跟踪数据将不再可用**。

然后，具有相同[CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html)的其他Adobe Experience Cloud解决方案将识别该ID。

## Experience Cloud 集成 {#experience-cloud-integrations}

下表提供了对可用Experience Cloud集成文档的访问。

<table> 
 <thead> 
  <tr> 
   <th> 解决方案和核心服务<br /> </th> 
   <th> 用例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe实时客户数据平台(RTCDP)</strong><br /> </td> 
   <td> Adobe Campaign与Adobe实时客户数据平台(RTCDP)之间的集成使您能够共享区段数据并将受众导入Adobe Campaign。<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">进</a> 一步了解活动 -Adobe实时客户数据平台集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management系统(IMS)- Adobe ID</strong><br /> </td> 
   <td> 允许您使用与其他Adobe Campaign解决方案相同的Adobe ID连接到Adobe Experience Cloud。<br /> 必须使用Adobe ID登录才能使用与Adobe Experience Cloud集成相关的特定功能，特别是核心服务。<br /> <p><a href="../../integrations/using/about-adobe-id.md">进一</a> 步了解如何使用Adobe Campaign实施Adobe ID。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 允许您在<strong>Adobe Experience Manager</strong>中直接创建映射到Adobe Campaign数据库的电子邮件内容或表单。<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">进一步</a> 了解Adobe Campaign - Adobe Experience Manager集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 允许您插入在打开由Adobe Campaign创建和发送的电子邮件时由<strong>Adobe Target</strong>动态计算的图像。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">进一步</a> 了解Adobe Campaign - Adobe Target集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People核心服</strong><br /> <strong>务AdobeAudience Manager</strong><br /> </td> 
   <td> 允许您在Adobe Experience Cloud解决方案和您使用的核心之间共享受众。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">进一</a> 步了解Adobe Campaign — 人员核心服务和Adobe Audience Manager集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets核心服务</strong><br /> </td> 
   <td> 允许将来自 Adobe Experience Cloud 库的资源插入到在 Adobe Campaign 中创建的电子邮件和登陆页。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">进一步</a> 了解Adobe Campaign — 资产核心服务集成</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 允许您将<strong>AEM Assets</strong>库中的资源插入在Adobe Campaign中创建的电子邮件和登陆页中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">进一步</a> 了解Adobe Campaign - AEM Assets集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> <strong>触发器核心服务</strong>与Adobe Campaign之间的集成允许您向客户发送个性化电子邮件，作为对Adobe Analytics在您网站上跟踪的特定行为的反应。<br /> <p><a href="https://helpx.adobe.com/cn/campaign/kb/triggers-and-campaign.html">进一步</a> 了解Adobe Campaign -Experience Cloud触发器集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Data Connectors</strong><br /> </td> 
   <td> <strong>数据连接器</strong> (以前称为Adobe Genesis)允许Adobe Campaign和Adobe Analytics通过与电子邮件活动后的用户行为相关的细分进行交互。相反，它会向Adobe Analytics — 数据连接器发送由Adobe Campaign传送的电子邮件活动的指示符和属性。<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">了解</a> 有关活动 - Data Connectors集成的更多信息。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
