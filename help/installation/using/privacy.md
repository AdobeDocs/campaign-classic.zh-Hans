---
product: campaign
title: 个性化和隐私
description: 了解隐私和个性化的安全最佳实践
feature: Installation, Privacy, Privacy Tools, URL Personalization
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
TQID: 'https://experienceleague.adobe.com/8u-ItsbouC0wIsamVYfyzQR1o-z-jY90Z3pKem-yarc'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: ac72e249-ebbf-4bb6-96c9-596af925419a
    internal-label: Privacy tools
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
  - id: fb2a841f-c522-491f-9901-a1b939d252df
    internal-label: Security
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: f55cfb22-471c-4161-8ea1-12868351e460
    internal-label: URL personalization
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 3%
---
# 个性化和隐私 {#privacy}

本页介绍URL个性化、URL签名以及保护包含个人信息的页面。

>[!NOTE]
>
>作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关数据限制和隐私请求的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/privacy/security#data-restriction){target=_blank}。
>
>[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/privacy/security#data-restriction){target=_blank}

在Campaign Classic v7中，限制对整个实体的访问需要内部版本8770或更高版本。

## URL PERSONALIZATION {#url-personalization}

向内容添加个性化链接时，请始终避免在URL的主机名部分进行任何个性化设置，以避免潜在的安全缺口。 绝不应该在所有URL属性&lt;`a href="">`或`<img src="">`中使用以下示例：

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 推荐

要验证并确保未使用上述功能，请通过[Campaign通用查询编辑器](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/data/query/query-editor){target="_blank"}（Campaign v8文档）对跟踪URL表运行查询，或在查询活动中创建具有筛选条件的工作流。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=zh-Hans){target="_blank"}。

示例：

1. 创建工作流并添加&#x200B;**查询**&#x200B;活动。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=zh-Hans){target="_blank"}。

1. 打开&#x200B;**查询**&#x200B;活动并在`nmsTrackingUrl`表上创建筛选器，如下所示：

   `source URL starts with http://<% or source URL starts with https://<%`

1. 运行工作流并检查结果是否存在。

1. 如果是这样，请打开输出过渡以查看URL列表。

   ![](assets/privacy-query-dynamic-url.png)


### URL签名

为了提高安全性，引入了一种用于跟踪电子邮件中链接的签名机制。 它从19.1.4版(9032@3a9dc9c)和20.2版开始提供。 此功能默认处于启用状态。

>[!NOTE]
>
>单击格式错误的签名URL时，返回此错误： `Requested URL '…' was not found.`

此外，您还可以使用增强功能来禁用在以前的内部版本中生成的URL。 默认情况下，此功能处于禁用状态。 您可以联系[客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以启用此功能。

如果您在19.1.4内部版本上运行，则在使用跟踪链接或使用锚点标记进行投放时可能会遇到问题。 如果出现这种情况，建议您禁用URL签名。

作为活动托管、托管云服务或混合型客户，您必须联系[客户关怀](https://helpx.adobe.com/cn/enterprise/using/support-for-experience-cloud.html)以禁用URL签名。

如果您在混合架构中运行Campaign，则在启用URL签名之前，请确保已如下所示升级托管的中源实例：

* 首先是内部部署营销实例
* 然后，升级到与内部部署营销实例相同的版本或略高的版本

否则，可能会出现以下一些问题：

* 在升级中间源实例之前，将通过该实例发送URL，而不进行签名。
* 升级中间源实例并在两个实例上启用URL签名后，先前未签名发送的URL将被拒绝。 原因是营销实例提供的跟踪文件需要签名。

要禁用以前内部版本中生成的URL，请同时在所有Campaign服务器上执行以下步骤：

1. 在服务器配置文件(`serverConf.xml`)中，将&#x200B;**blockRedirectForUnsignedTrackingLink**&#x200B;选项更改为&#x200B;**true**。
1. 重新启动`nlserver`服务。
1. 在`tracking`服务器上，重新启动`web`服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

要启用URL签名，请同时在所有Campaign服务器上执行以下步骤：

1. 在服务器配置文件(`serverConf.xml`)中，将&#x200B;**signEmailLinks**&#x200B;选项更改为&#x200B;**true**。
1. 重新启动&#x200B;**nlserver**&#x200B;服务。
1. 在`tracking`服务器上，重新启动`web`服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

## 使用PI保护页面

我们强烈建议内部部署客户保护可能包含个人信息(PI)的页面，如镜像页面、Web应用程序等。

此过程的目标是防止对这些页编制索引，从而避免潜在的安全风险。 以下是一些有用的文章：

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

要保护您的页面，请执行以下步骤：

1. 在Web服务器（Apache或IIS）的根目录下添加`robots.txt`文件。 以下是文件的内容：

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   对于IIS，请参阅[此页面](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files)。

   对于Apache，您可以将文件放在&#x200B;**/var/www/robots.txt** (Debian)中。

1. 有时添加&#x200B;**robots.txt**&#x200B;文件的安全性不够。 例如，如果其他网站包含指向您的页面的链接，则该链接可能会显示在搜索结果中。

   除了&#x200B;**robots.txt**&#x200B;文件外，还建议添加&#x200B;**X-Robots-Tag**&#x200B;标头。 您可以在Apache或IIS以及&#x200B;**serverConf.xml**&#x200B;配置文件中执行该操作。

   有关详细信息，请参阅[本文](https://developers.google.com/search/reference/robots_meta_tag)。
