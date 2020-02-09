---
title: 关于 Campaign 集成
description: 了解Adobe Campaign当前版本与[Adobe Experience cloud解决方案]之间可用的功能集成
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
source-git-commit: 2e16d4de068f8cb1e61069aa53626f7bf7021466

---


# 关于 Campaign 集成{#about-campaign-integrations}

了解Adobe Campaign当前版本与Adobe Experience cloud解决方案及核心服务之 [间的功能集](https://marketing.adobe.com/resources/help/en_US/mcloud/marketing-cloud-integrations.html) 成 [功能](https://marketing.adobe.com/resources/help/en_US/mcloud/core-services-landing.html)。

Adobe Experience cloud是一套全面的一流集成解决方案，构建于一个通用数据平台上，并提供一组功能强大的核心服务。

在本页中查找可与Adobe Campaign集成的Adobe解决方案和核心服务的完整列表以及相关 [文档](#experience-cloud-integrations)。

>[!CAUTION]
>
>这些集成中的大多数都需要通过Adobe ID(IMS)登录。 For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>IMS的实现是一个复杂的过程，需要经过一段时间的规划。 它仅由Adobe技术管理员负责。

## 使用Experience cloud解决方案 {#working-with-experience-cloud-solutions}

根据您的环境，可以将多个解决方案关联到Adobe Experience Cloud。 它们作为组织链接。 组 **织** ，是允许管理员配置组和用户并控制Experience cloud中的单点登录的实体。 该组织的工作方式与跨所有Experience cloud产品和解决方案的登录公司类似。 大多数情况下，组织是您的公司名称。 但是，公司可以拥有许多组织。

Adobe Experience cloud帮助门户中详细介绍了组织管理和关 [联Adobe Experience cloud帐户的信息](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html)。

>[!CAUTION]
>
>新安装Adobe Campaign或将现有安装与Adobe Experience cloud集成时，将启 [用Experience Cloud ID服务](https://marketing.adobe.com/resources/help/en_US/mcvid/) 。 此服务取代了Adobe Campaign首先使用的永久cookie，用于跟踪功能。
>
>随后，将为生成跟踪日志的收件人分配唯一访客ID。 此ID将保存在表 **[!UICONTROL Requester UUID (@sourceID)]** 的字 **[!UICONTROL nms:trackingLogRcp]** 段中。 因此，在实施访客ID服务之前存在的收件人的跟踪数据将不再可用。
>
>然后，使用相同CNAME的其他Adobe Experience cloud解决方案将识别该 [ID](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_cname.html)。

## Experience Cloud 集成 {#experience-cloud-integrations}

下表提供了对可用Experience cloud集成文档的访问。

<table> 
 <thead> 
  <tr> 
   <th> 解决方案和核心服务<br /> </th> 
   <th> 用例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign Standard</strong> （Prime产品）<br /> </td> 
   <td> 允许您将数据复制到 <strong>Campaign Standard</strong>，将两个应用程序的最佳组合在一起。 Campaign Classic v7具有用于管理主营销数据库的高级工具。 Campaign Classic v7中的数据复制使Campaign standard能够在用户友好的环境中利用丰富的数据。<br /><p> <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">了解有关</a> Adobe Campaign Classic - Adobe Campaign Standard集成的更多信息。</p><br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> 允许您使用与其他Adobe Experience cloud解决方案相同的Adobe ID连接到Adobe Campaign。<br /> 必须使用Adobe ID登录，才能使用与Adobe Experience cloud集成相关的特定功能，特别是核心服务。<br /> <p><a href="../../integrations/using/about-adobe-id.md">了解关于</a> “使用Adobe Campaign实施Adobe ID”的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 允许您在 <strong>Adobe Experience Manager中直接创建映射到Adobe Campaign数据库的电子邮件内容或表单</strong>。<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">了解有关</a> Adobe Campaign - Adobe Experience manager集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 允许您插入在打开由 <strong>Adobe Campaign创建和发送的电子邮件时由</strong> Adobe Target动态计算的图像。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">了解有关</a> Adobe Campaign - Adobe Target集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People核心服务</strong><br /><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 允许您在Adobe Experience cloud解决方案和您使用的核心之间共享受众。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解有关</a> Adobe Campaign —— 人员核心服务和Adobe Audience manager集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>资产核心服务</strong><br /> </td> 
   <td> 允许您将Adobe Experience cloud库中的资产插入在Adobe Campaign中创建的电子邮件和登录页面中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">了解有关Adobe</a> Campaign - Assets核心服务集成的更多信息</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM资产</strong><br /> </td> 
   <td> 允许您将 <strong></strong> AEM资产库中的资产插入在Adobe Campaign中创建的电子邮件和登录页面中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">了解有关</a> Adobe Campaign - AEM资产集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud触发器</strong><br /> </td> 
   <td> Triggers核心服 <strong></strong> 务与Adobe Campaign之间的集成允许您向客户发送个性化电子邮件，作为对Adobe Analytics在您网站上跟踪的特定行为的反应。 有关详细信息，请参阅以下 <a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">文章</a>。<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">了解有关Adobe</a> Campaign - Experience cloud触发器集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Data Connectors</strong><br /> </td> 
   <td> <strong>数据连接器</strong> （以前称为Adobe Genesis）允许Adobe Campaign和Adobe Analytics通过与电子邮件营销活动后的用户行为相关的细分进行交互。 相反，它会将Adobe Campaign提供的电子邮件营销活动的指标和属性发送到Adobe Analytics - Data connector。<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">了解有关</a> Campaign - Data Connectors集成的更多信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe实时客户数据平台</strong><br /> </td> 
   <td> Adobe Campaign与Adobe实时客户数据平台之间的集成允许您共享细分数据并将受众导入Adobe Campaign。<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">了解有关</a> Campaign - Adobe实时客户数据平台集成的更多信息。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

