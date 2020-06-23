---
title: 关于 Campaign 集成
description: 了解当前版本的Adobe Campaign与[Adobe Experience Cloud解决方案]之间可用的功能集成
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c3737b22c7bf4e614c5a2fbe8e8fd954d3ece8a
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 1%

---


# 关于 Campaign 集成 {#about-campaign-integrations}

Adobe Experience Cloud是一套全面的同类最佳集成解决方案，构建在通用数据平台上，并提供一组通用的强大核心服务。

了解Adobe Campaign与Adobe Experience Cloud解决方案及核 [心服务之间](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) 的功 [能集成](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)。 然后，您可以现代化解决方案实施并实施Experience Cloud，以便能够使用客户属性和受众等功能。

本节提供可与Adobe Campaign集成的Adobe解决方案和核心服务的完整列表以及相关 [文档](#experience-cloud-integrations)。

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>这些集成中的大多数都需要通过Adobe ID(IMS)登录。 For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>请注意，IMS实施是一个复杂的过程，可能很长。 它仅由Adobe技术管理员保留。

## 关联您的解决方案 {#working-with-experience-cloud-solutions}

根据您的环境，可以将多个解决方案关联到Adobe Experience Cloud。 它们作为组织链接。 组 **织** 是允许管理员配置组和用户以及控制Experience Cloud中的单一登录的实体。 组织的功能类似于跨所有Experience Cloud产品和解决方案的登录公司。 大多数情况下，组织是您的公司名称。 但是，公司可以有许多组织。

Adobe Experience Cloud帮助门户中详细介绍了组织管 [理和关联Adobe Experience Cloud帐户](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)。

>[!CAUTION]
>
>新安装Adobe Campaign或将现有安装与Adobe Experience Cloud集成时，将启 [用Experience CloudID服务](https://docs.adobe.com/content/help/en/id-service/using/home.html) 。 此服务取代了首先由Adobe Campaign跟踪功能使用的永久cookie。
>
>随后将为生成访客的收件人分配唯一的跟踪日志ID。 此ID将保存在表 **[!UICONTROL Requester UUID (@sourceID)]** 的字段 **[!UICONTROL nms:trackingLogRcp]** 中。 因此，在实施收件人ID服务之前存在的访客的跟踪数据将不再可用。
>
>随后，使用相同CNAME的其他Adobe Experience Cloud解决方案将识别该 [ID](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html)。

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
   <td> <strong>Adobe实时客户数据Platform</strong><br /> </td> 
   <td> Adobe Campaign与Adobe实时客户数据Platform之间的集成使您能够共享细分数据并将受众导入Adobe Campaign。<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">进一步了</a> 解活动- Adobe实时客户Platform集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS -Adobe ID</strong><br /> </td> 
   <td> 允许您使用与其他Adobe Experience Cloud解决方案相同的Adobe Campaign连接到Adobe ID。<br /> 必须使用Adobe ID登录，才能使用与Adobe Experience Cloud集成相关的特定功能，特别是核心服务。<br /> <p><a href="../../integrations/using/about-adobe-id.md">了解有关使用</a> Adobe ID实施Adobe Campaign的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 允许您创建直接映射到Adobe Campaign库的电子邮件内容或表单，以 <strong>Adobe Experience Manager</strong>。<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">进一步了解Adobe Campaign</a> -Adobe Experience Manager集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 允许您插入在打开由Adobe Target创建 <strong>和发送</strong> 的电子邮件时由Adobe Campaign动态计算的图像。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">进一步了解Adobe Campaign</a> -Adobe Target集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>人员核心服务</strong><br /><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 允许您在Adobe Experience Cloud解决方案和您使用的核心解决方案之间共享受众。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解关于Adobe Campaign</a> -人员核心服务和Adobe Audience Manager集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>资产核心服务</strong><br /> </td> 
   <td> 允许您将Adobe Experience Cloud库中的资产插入在Adobe Campaign中创建的电子邮件和登陆页中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">了解有关Adobe Campaign</a> -资产核心服务集成的更多信息</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 允许您将AEM Assets库中的资 <strong>源插入</strong> 在Adobe Campaign中创建的电子邮件和登陆页。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">进一步了解Adobe Campaign</a> -AEM Assets集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud触发器</strong><br /> </td> 
   <td> 触发器 <strong>核心服务与Adobe Campaign</strong> ，使您能向客户发送个性化电子邮件，作为对AdobeAnalytics在您的网站上跟踪的特定行为的回应。<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">了解有关Adobe Campaign</a> -Experience Cloud触发器集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AdobeAnalytics-数据连接器</strong><br /> </td> 
   <td> <strong>数据连接器</strong> （以前称为Adobe Genesis）允许Adobe Campaign和Adobe Deasin通过与电子邮件活动后的用户行为相关的细分进行交互。 相反，它通过Adobe Campaign将电子邮件活动的指标和属性发送到Adobe Dibos-Data Connector。<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">了解有关活动</a> -数据连接器集成的更多信息。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

