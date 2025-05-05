---
product: campaign
title: 关于 Campaign 集成
description: 使用其他 Adobe 解决方案，并将其各种功能与 Campaign 相结合
feature: Overview
badge-v8: label="也适用于v8" type="Positive" tooltip="同样适用于Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 4%

---

# 开始使用Adobe Campaign集成 {#about-campaign-integrations}

Adobe Experience Cloud是一组一流的集成式解决方案，构建在通用数据平台之上，具有一组通用的强大解决方案和应用程序。

在[此页面](https://experienceleague.adobe.com/zh-hans/docs/core-services/interface/administration/integrations){_blank}中了解有关Adobe Campaign与Adobe Experience Cloud解决方案之间可用功能集成的更多信息。

[此部分](#experience-cloud-integrations)中提供了可与Adobe集成的Adobe Campaign解决方案和应用程序服务的完整列表以及相关文档。

>[!CAUTION]
>
>这些集成需要实施Adobe Identity Management System (IMS)，以通过Adobe ID登录。 [请参阅此页面](../../integrations/using/about-adobe-id.md)以了解详情。
>

## 关联您的解决方案 {#working-with-experience-cloud-solutions}

可将多个解决方案链接到Adobe Experience Cloud。 **组织**&#x200B;是一个客户实体，它允许管理员配置组和用户，并控制Adobe Experience Cloud中的单点登录(SSO)。 公司的行为就像一家登录公司，负责处理所有Experience Cloud产品和解决方案。 大多数情况下，组织是您的公司名称。但是，一家公司可以有多个组织。

[Adobe Experience Cloud帮助门户](https://experienceleague.adobe.com/zh-hans/docs/core-services/interface/administration/organizations){_blank}中详细介绍了组织管理和关联Adobe Experience Cloud帐户。

## 身份和Cookie管理 {#id-and-cookies}

在安装Adobe Campaign或将现有安装与Adobe Experience Cloud集成时，将启用[Adobe Experience Cloud Identity服务](https://experienceleague.adobe.com/zh-hans/docs/id-service/using/home){_blank}。 此服务取代了Adobe Campaign首先用于跟踪功能的永久Cookie。

Adobe Experience Cloud身份服务（ID服务）提供一个通用的持久ID，用于在Experience Cloud中的所有解决方案中标识您的访问者。

一个唯一的访客ID将被分配给生成跟踪日志的收件人。 此ID将保存在&#x200B;**[!UICONTROL nms:trackingLogRcp]**&#x200B;表的&#x200B;**[!UICONTROL Requester UUID (@sourceID)]**&#x200B;字段中。 **因此，在实现访客ID服务之前存在的收件人的跟踪数据将不再可用**。

该ID随后将被具有相同CNAME的其他Adobe Experience Cloud解决方案识别。 [了解详情](https://experienceleague.adobe.com/zh-hans/docs/id-service/using/reference/analytics-reference/cname){_blank}。

## Experience Cloud 集成 {#experience-cloud-integrations}

下表提供了对可用Experience Cloud集成文档的访问。

<table> 
 <thead> 
  <tr> 
   <th> 解决方案和应用程序<br /> </th> 
   <th> 用例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> 配置Adobe Campaign与Adobe Real-time Customer Data Platform (RTCDP)之间的集成，以共享分段数据并将受众导入到Adobe Campaign。<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">了解有关Campaign - Adobe Real-time Customer Data Platform集成的更多信息</a>。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> 将Adobe IMS配置为使用与其他Adobe Campaign解决方案相同的Adobe ID连接到Adobe Experience Cloud。<br />要使用Adobe ID集成所关联的特定功能，必须使用Adobe Experience Cloud登录。<br /> <p><a href="../../integrations/using/about-adobe-id.md">了解有关Adobe Campaign实施Adobe ID的更多信息</a>。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 配置此集成以在<strong>Adobe Experience Manager</strong>.<br />中创建直接映射到Adobe Campaign数据库的电子邮件内容或表单 <p><a href="../../integrations/using/about-adobe-experience-manager.md">了解有关Adobe Campaign - Adobe Experience Manager集成的更多信息</a>。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 配置此集成，以便在打开由Adobe Target创建和发送的电子邮件时插入由<strong>Adobe Campaign</strong>动态计算的图像。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">了解有关Adobe Campaign - Adobe Target集成的更多信息</a>。</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 配置此集成以在Adobe Experience Cloud解决方案和您使用的应用程序之间共享访问群体。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解有关Adobe Campaign - Adobe Audience Manager集成的更多信息</a>。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>资源</strong><br /> </td> 
   <td> 配置此集成，以将您的Adobe Experience Cloud Library中的资源插入在Adobe Campaign中创建的电子邮件和登陆页面中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">了解有关Adobe Campaign - Assets集成的更多信息</a></p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 配置此集成，将您的<strong>AEM Assets</strong>库中的资源插入到在Adobe Campaign中创建的电子邮件和登陆页中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">了解有关Adobe Campaign - AEM Assets集成的更多信息</a>。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> 配置<strong>Adobe Experience Cloud Triggers</strong>与Adobe Campaign之间的集成，以根据Adobe Analytics对网站上特定行为的跟踪，向客户发送个性化电子邮件作为回应。<br /> <p><a href="about-triggers.md">了解有关Adobe Campaign - Experience Cloud triggers集成的更多信息</a>。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics连接器</strong><br /> </td> 
   <td> 配置此集成，以允许Adobe Campaign和Adobe Analytics在电子邮件营销活动后，通过有关用户行为的区段进行交互。 相反，它向Adobe Analytics发送由Adobe Campaign发送的电子邮件营销活动的指示器和属性。<br /> <p><a href="../../integrations/using/gs-aa.md">了解有关Campaign - Analytics Connectors集成的更多信息</a>。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
