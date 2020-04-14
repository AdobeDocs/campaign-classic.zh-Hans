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
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# 关于 Campaign 集成 {#about-campaign-integrations}

Adobe Experience Cloud是一套全面的一流集成解决方案，构建于一个通用数据平台上，并提供一组功能强大的核心服务。

了解Adobe Campaign与Adobe Experience Cloud解决方案及核心服务之 [间的功能集](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) 成 [功能](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)。 然后，您可以使解决方案实施现代化并实施Experience Cloud，以便使用客户属性和受众等功能。

本节提供可与Adobe Campaign集成的Adobe解决方案和核心服务的完整列表以及相关文 [档](#experience-cloud-integrations)。

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>这些集成中的大多数都需要通过Adobe ID(IMS)登录。 For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>请注意，IMS实施是一个复杂的过程，可能很长。 它仅由Adobe技术管理员负责。

## 关联您的解决方案 {#working-with-experience-cloud-solutions}

根据您的环境，可以将多个解决方案关联到Adobe Experience Cloud。 它们作为组织链接。 组 **织** ，是允许管理员配置组和用户并控制Experience Cloud中的单点登录的实体。 组织的功能类似于跨所有Experience Cloud产品和解决方案的登录公司。 大多数情况下，组织是您的公司名称。 但是，公司可以有许多组织。

Adobe Experience Cloud帮助门户中详细介绍了组织管理和关 [联Adobe Experience Cloud帐户的信息](https://marketing.adobe.com/resources/help/zh_CN/mcloud/organizations.html)。

>[!CAUTION]
>
>在新安装Adobe Campaign或将现有安装与Adobe Experience Cloud集成时，将启 [用Experience Cloud ID服务](https://marketing.adobe.com/resources/help/en_US/mcvid/) 。 此服务取代了首先通过Adobe Campaign其跟踪功能而使用的永久Cookie。
>
>然后，将为生成访客的收件人分配唯一的跟踪日志ID。 此ID将保存在表 **[!UICONTROL Requester UUID (@sourceID)]** 的字 **[!UICONTROL nms:trackingLogRcp]** 段中。 因此，在实施收件人ID服务之前存在的访客的跟踪数据将不再可用。
>
>然后，使用相同CNAME的其他Adobe Experience Cloud解决方案将识别该 [ID](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_cname.html)。

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
   <td> <strong>Adobe实时客户数据平台</strong><br /> </td> 
   <td> Adobe Campaign与Adobe实时客户数据平台之间的集成使您能够共享细分数据并将受众导入Adobe Campaign。<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">了解关于活动</a> - Adobe实时客户数据平台集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> 允许您使用与其他Adobe Experience Cloud解决方案相同的Adobe ID连接到Adobe Campaign。<br /> 必须使用Adobe ID登录，才能使用与Adobe Experience Cloud集成相关的特定功能，特别是核心服务。<br /> <p><a href="../../integrations/using/about-adobe-id.md">了解有关实施</a> Adobe ID的更多信息(包含Adobe Campaign)。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 允许您在 <strong>Adobe Experience Manager中创建直接映射到Adobe Campaign数据库的电子邮件内容或表单</strong>。<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">了解有关Adobe Campaign</a> - Adobe Experience Manager集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe目标</strong><br /> </td> 
   <td> 允许您插入在打开由 <strong>Adobe目标创建和发送的电子邮件时</strong> ，由AdobeAdobe Campaign动态计算的图像。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">了解有关Adobe Campaign</a> - Adobe目标集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People核心服务</strong><br /><strong>Adobe受众经理</strong><br /> </td> 
   <td> 允许您在Adobe Experience Cloud解决方案和您使用的核心之间共享受众。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解关于Adobe Campaign</a> -人员核心服务和Adobe受众管理器集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>资产核心服务</strong><br /> </td> 
   <td> 允许您将Adobe Experience Cloud库中的资源插入在Adobe Campaign中创建的电子邮件和登陆页中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">了解关于Adobe Campaign</a> -资产核心服务集成的更多信息</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM资产</strong><br /> </td> 
   <td> 允许您将 <strong></strong> AEM资产库中的资产插入在Adobe Campaign中创建的电子邮件和登陆页中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">了解有关Adobe Campaign</a> - AEM Assets集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud触发器</strong><br /> </td> 
   <td> Triggers核心服 <strong>务与Adobe Campaign的集成</strong> ，允许您向客户发送个性化电子邮件，作为对Adobe Analytics在您网站上跟踪的特定行为的反应。<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">了解有关Adobe Campaign</a> - Experience Cloud触发器集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Data Connectors</strong><br /> </td> 
   <td> <strong>数据连接器</strong> （以前称为Adobe Genesis）允许Adobe Campaign和Adobe Analytics通过与电子邮件活动后的用户行为相关的细分进行交互。 相反，它通过Adobe Campaign将电子邮件活动的指标和属性发送到Adobe Analytics —— 数据连接器。<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">了解有关活动</a> - Data Connectors集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Campaign标准</strong> （优质产品）<br /> </td> 
   <td> 允许您将数据复制到 <strong>Campaign Standard</strong>，将两个应用程序的最佳组合在一起。 Campaign Classicv7具有用于管理主营销数据库的高级工具。 v7Campaign Classic的数据复制使Campaign Standard能够在用户友好的环境中利用丰富的数据。<br /><p> <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">了解有关Adobe Campaign</a> -Adobe Campaign标准集成的更多信息。</p><br /></td> 
  </tr> 
 </tbody> 
</table>

