---
product: campaign
title: 关于 Campaign 集成
description: 使用其他 Adobe 解决方案，并将其各种功能与 Campaign 相结合
feature: Overview
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 59156851156338c9462781d31ce81a651362f2da
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 7%

---

# Adobe Campaign集成快速入门 {#about-campaign-integrations}



Adobe Experience Cloud是一套业内最佳的综合性集成解决方案，它基于常用的数据平台而构建，提供了一组功能强大的通用核心服务。

了解Adobe Campaign与之间可用的功能集成 [Adobe Experience Cloud解决方案](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html) 和 [核心服务](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html). 然后，您可以使解决方案实施符合现代化要求和实施Experience Cloud，以便能够使用客户属性和受众等功能。

![](assets/ExCloud-solutions.png)

可与Adobe Campaign集成的Adobe解决方案和核心服务的完整列表以及相关文档位于 [本节](#experience-cloud-integrations).

>[!CAUTION]
>
>这些集成中的大多数都需要实施AdobeIdentity Management System (IMS)，才能通过Adobe ID登录。 [请参阅此页面](../../integrations/using/about-adobe-id.md)以了解详情。
>

## 关联您的解决方案 {#working-with-experience-cloud-solutions}

可以将多个解决方案链接到Adobe Experience Cloud。 此 **组织** 是一个客户实体，它允许管理员配置群组和用户，并控制Adobe Experience Cloud中的单点登录(SSO)。 该组织的作用类似于一个衔接所有Experience Cloud产品和解决方案的登录公司。 大多数情况下，组织是您的公司名称。但是，公司可以具有多个组织。

有关组织管理和关联Adobe Experience Cloud帐户的详情，请参见 [Adobe Experience Cloud帮助门户](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html).

## 身份和Cookie管理 {#id-and-cookies}

安装Adobe Campaign或将现有安装与Adobe Experience Cloud集成时， [Adobe Experience Cloud Identity服务](https://experienceleague.adobe.com/docs/id-service/using/home.html) 已启用。 此服务取代了Adobe Campaign首先用于跟踪功能的永久Cookie。

Adobe Experience Cloud Identity服务（ID服务）提供了一个通用的永久性ID，用于在Experience Cloud的所有解决方案中标识您的访客。

独特访客ID将分配给生成跟踪日志的收件人。 此ID将保存在 **[!UICONTROL Requester UUID (@sourceID)]** 字段 **[!UICONTROL nms:trackingLogRcp]** 表格。 **因此，在实施访客ID服务之前存在的收件人的跟踪数据将不再可用**.

随后，该ID将由具有相同CNAME的其他Adobe Experience Cloud解决方案识别。 [了解详情](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html)

## Experience Cloud 集成 {#experience-cloud-integrations}

下表提供了对可用Experience Cloud集成文档的访问权限。

<table> 
 <thead> 
  <tr> 
   <th> 解决方案与核心服务<br /> </th> 
   <th> 用例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> Adobe Campaign与Adobe Real-time Customer Data Platform (RTCDP)之间的集成允许您共享区段数据并将受众导入到Adobe Campaign。<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">了解详情</a> 关于Campaign - Adobe Real-time Customer Data Platform集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AdobeIdentity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> 允许您使用与其他Adobe Campaign解决方案相同的Adobe ID连接到Adobe Experience Cloud。<br /> 要使用Adobe ID集成所关联的特定功能（尤其是核心服务），必须使用Adobe Experience Cloud登录。<br /> <p><a href="../../integrations/using/about-adobe-id.md">了解详情</a> 关于使用Adobe Campaign实施Adobe ID的信息。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 允许您在中直接创建映射到Adobe Campaign数据库的电子邮件内容或表单 <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">了解详情</a> 关于Adobe Campaign - Adobe Experience Manager集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 允许您插入由动态计算的图像 <strong>Adobe Target</strong> 打开由Adobe Campaign创建和发送的电子邮件时。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">了解详情</a> 关于Adobe Campaign - Adobe Target集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People核心服务</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 允许您在Adobe Experience Cloud解决方案和您使用的核心之间共享受众。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解详情</a> 关于Adobe Campaign — 人员核心服务和Adobe Audience Manager集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets核心服务</strong><br /> </td> 
   <td> 允许将来自 Adobe Experience Cloud 库的资源插入到在 Adobe Campaign 中创建的电子邮件和登陆页。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">了解详情</a> 关于Adobe Campaign - Assets核心服务集成</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 允许您从插入资产 <strong>AEM Assets</strong> 库中的电子邮件和在Adobe Campaign中创建的登陆页面。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">了解详情</a> 关于Adobe Campaign - AEM Assets集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud触发器</strong><br /> </td> 
   <td> 集成介于 <strong>触发核心服务</strong> 和Adobe Campaign允许您向客户发送个性化电子邮件，以对Adobe Analytics在网站上跟踪的特定行为作出反应。<br /> <p><a href="https://helpx.adobe.com/cn/campaign/kb/triggers-and-campaign.html">了解详情</a> 关于Adobe Campaign -Experience Cloud触发器集成。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics连接器</strong><br /> </td> 
   <td> <strong>Adobe Analytics连接器</strong> 允许Adobe Campaign和Adobe Analytics在电子邮件营销活动后，通过有关用户行为的区段进行交互。 反过来，它会将Adobe Campaign投放的电子邮件营销活动的指标和属性发送到Adobe Analytics。<br /> <p><a href="../../platform/using/gs-aa.md">了解详情</a> 关于Campaign - Analytics连接器集成。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
