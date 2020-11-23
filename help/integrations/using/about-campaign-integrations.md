---
solution: Campaign Classic
product: campaign
title: 关于 Campaign 集成
description: 使用其他 Adobe 解决方案，并将其不同的功能与 Campaign 相结合。
audience: integrations
content-type: reference
topic-tags: campaign-integrations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 9%

---


# Get started with Adobe Campaign integrations {#about-campaign-integrations}

Adobe Experience Cloud是一套全面的一流集成解决方案，构建于一个具有一套强大核心服务的公共数据平台上。

了解Adobe Campaign与Adobe Experience Cloud解决方案及核心服务 [之间的功](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) 能 [集成](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)。 然后，您可以现代化解决方案实施并实施Experience Cloud，以便能够使用客户属性和受众等功能。

![](assets/ExCloud-solutions.png)

本节提供可与Adobe集成的完整列表解决方案和核心服务以及相关文 [档](#experience-cloud-integrations)。

>[!CAUTION]
>
>这些集成中的大多数都需要实施AdobeIdentity Management系统(IMS)，才能通过Adobe ID登录。 [在本页中了解更多信息](../../integrations/using/about-adobe-id.md)。


## 关联您的解决方案 {#working-with-experience-cloud-solutions}

可以将多个解决方案与Adobe Experience Cloud关联。 The **organization** is the customer entity that enables an administrator to configure groups and users, and to control single sign-on (SSO) in Adobe Experience Cloud. 该组织的工作方式类似于跨所有Experience Cloud产品和解决方案的登录公司。 大多数情况下，组织是您的公司名称。但是，公司可以有许多组织。

Adobe Experience Cloud帐户的组织管理和关联在Adobe Experience Cloud帮 [助门户中详细介绍](https://docs.adobe.com/content/help/zh-Hans/core-services/interface/manage-users-and-products/organizations.html)。

## 身份和cookie管理 {#id-and-cookies}

安装Adobe Campaign或将现有安装与Adobe Experience Cloud集成时，将启 [用Adobe Experience Cloud身](https://docs.adobe.com/content/help/en/id-service/using/home.html) 份服务。 此服务取代了首先由Adobe Campaign跟踪功能使用的永久cookie。

Adobe Experience Cloud标识服务（ID服务）提供通用的永久ID，用于在Experience Cloud中的所有解决方案中标识您的访客。

唯一访客ID将分配给生成跟踪日志的收件人。 此ID将保存在表 **[!UICONTROL Requester UUID (@sourceID)]** 的字段 **[!UICONTROL nms:trackingLogRcp]** 中。 **因此，在实施收件人ID服务之前存在的访客的跟踪数据将不再可用**。

随后，ID将被具有相同CNAME的其他Adobe Experience Cloud解决方 [案识别](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html)。

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
   <td> Adobe Campaign与Adobe实时客户数据平台(RTCDP)之间的集成使您能够共享细分数据并将受众导入Adobe Campaign。<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">进一步了解活动</a> -Adobe实时客户数据平台集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AdobeIdentity Management系统(IMS)-Adobe ID</strong><br /> </td> 
   <td> 允许您与其他Adobe Experience Cloud解决方案的Adobe Campaign连接到相同的Adobe ID。<br /> Adobe ID必须用于登录才能使用与Adobe Experience Cloud集成相关的特定功能，特别是核心服务。<br /> <p><a href="../../integrations/using/about-adobe-id.md">进一步了解</a> “用Adobe Campaign实施Adobe ID”。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Allows you to create email contents or forms mapped to the Adobe Campaign database directly in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">进一步了解Adobe Campaign</a> -Adobe Experience Manager集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Allows you to insert images that are dynamically computed by <strong>Adobe Target</strong> when the email created and sent by Adobe Campaign is opened.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">进一步了解Adobe Campaign</a> -Adobe Target集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>人员核心服务</strong><br /><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 允许您在Adobe Experience Cloud解决方案和您使用的核心之间共享受众。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解关于Adobe Campaign</a> -人员核心服务和Adobe Audience Manager集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>资产核心服务</strong><br /> </td> 
   <td> 允许将来自 Adobe Experience Cloud 库的资源插入到在 Adobe Campaign 中创建的电子邮件和登陆页。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">了解有关Adobe Campaign</a> -资产核心服务集成的更多信息</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Allows you to insert assets from your <strong>AEM Assets</strong> library into emails and landing pages created in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">进一步了解Adobe Campaign</a> -AEM Assets集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Integration between <strong>Triggers core service</strong> and Adobe Campaign allows you to send personalized emails to your customers as a reaction to specific behaviors that are tracked on your website by Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/cn/campaign/kb/triggers-and-campaign.html">了解有关Adobe Campaign</a> -Experience Cloud触发器集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics-数据连接器</strong><br /> </td> 
   <td> <strong>数据连接器</strong> (以前称为Adobe Genesis)允许Adobe Campaign和Adobe Analytics通过与电子邮件活动后的用户行为相关的细分进行交互。 相反，它会通过Adobe Campaign向Adobe Analytics-数据连接器发送电子邮件活动的指标和属性。<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">了解有关活动</a> -数据连接器集成的更多信息。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

