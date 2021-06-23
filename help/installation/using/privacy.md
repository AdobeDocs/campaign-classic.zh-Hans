---
product: campaign
title: 隐私
description: 进一步了解有关隐私的最佳实践。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: f31591949bb033ff250cf4b33eddcc2c1d31cc6c
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 4%

---

# 隐私 {#privacy}

## 隐私请求

Adobe Campaign 提供一套工具，可帮助您确保符合《欧盟通用数据保护条例》(GDPR) 和《加州消费者隐私法案》(CCPA) 的隐私政策。

有关隐私管理概念及Adobe Campaign中实施步骤的一般信息，请参阅[此页面](../../platform/using/privacy-management.md)。 您还可以找到最佳实践以及用户流程和角色的概述。

## URL个性化 {#url-personalization}

在向内容添加个性化链接时，应始终避免在URL的主机名部分进行任何个性化，以避免潜在的安全漏洞。 以下示例绝不应用于所有URL属性`a href="">`或`<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 推荐

要验证并确保您未使用上述内容，请通过[促销活动通用查询编辑器](../../platform/using/steps-to-create-a-query.md)对跟踪URL表运行查询，或在[查询活动](../../workflow/using/query.md)中使用筛选条件创建工作流。

示例:

1. 创建工作流并添加查询活动。 了解详情.

1. 打开查询活动，并在nmsTrackingUrl表上创建过滤器，如下所示：源URL以http://&lt;%开头，或源URL以https://&lt;%开头。

1. 运行工作流并检查是否存在结果。

1. 如果是，请打开输出过渡以查看URL列表。

<img src="assets/privacy-query-dynamic-url.png">

### URL签名

为了提高安全性，引入了用于跟踪电子邮件中链接的签名机制。 该功能在版本19.1.4(9032@3a9dc9c)和Campaign 20.2中可用。默认情况下启用此功能。

>[!NOTE]
>
>单击格式错误的签名URL时，会返回以下错误：&quot;未找到请求的URL &#39;...&#39;。&quot;

此外，自Campaign 20.2和[!DNL Gold Standard]版本以来，您可以使用增强功能禁用在以前的内部版本中生成的URL。 此功能默认处于禁用状态。 您可以联系[客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以启用此功能。

如果您运行的是[!DNL Gold Standard] 19.1.4，则可能会遇到使用跟踪链接的推送通知投放问题，或使用锚点标记的投放问题。 如果是，我们建议您禁用URL签名。

无论您是在本地运行Campaign还是在混合架构中运行Campaign，都必须联系[客户关怀](https://helpx.adobe.com/cn/enterprise/using/support-for-experience-cloud.html)才能禁用URL签名。

如果您在混合架构中运行Campaign，则在启用URL签名之前，请确保已按如下方式升级托管的中间源实例：
* 在本地营销实例之前
* 更改为与内部部署营销实例相同的版本，或更高版本

否则，可能会出现以下问题：
* 在升级中间源实例之前，将通过此实例发送不带签名的URL。
* 升级中间源实例并在这两个实例上启用URL签名后，之前未经签名而发送的URL将被拒绝。 原因是营销实例提供的跟踪文件请求了签名。

要禁用在以前的内部版本中生成的URL，请同时在所有Campaign服务器上执行以下步骤：

1. 在服务器配置文件(serverConf.xml)中，将&#x200B;**blockRedirectForUnsignedTrackingLink**&#x200B;更改为&#x200B;**true**。
1. 重新启动&#x200B;**nlserver**&#x200B;服务。
1. 在跟踪服务器上，重新启动Web服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

要启用URL签名，请同时在所有Campaign服务器上执行以下步骤：

1. 在服务器配置文件(serverConf.xml)中，将&#x200B;**signEmailLinks**&#x200B;更改为&#x200B;**false**。
1. 重新启动&#x200B;**nlserver**&#x200B;服务。
1. 在跟踪服务器上，重新启动Web服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

## 数据限制

您必须确保经过身份验证的低权限用户无法访问加密密码。 要实现此目的，主要有两种方法：限制仅访问密码字段或访问整个实体（需要内部版本>= 8770）。

此限制允许您删除密码字段，但允许所有用户从界面访问外部帐户。 请参见[此页面](../../configuration/using/restricting-pii-view.md)。

1. 进入&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**。

1. 创建新的&#x200B;**[!UICONTROL Extension of a schema]**。

   ![](assets/privacy-data-restriction.png)

1. 选择&#x200B;**[!UICONTROL External Account]**(extAccount)。

1. 在最后一个向导屏幕中，您可以编辑新的srcSchema以限制对所有密码字段的访问：

   可以通过以下方式替换主元素(`<element name="extAccount" ... >`):

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   因此，扩展的srcSchema可能如下所示：

   ```
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >您可以将`$(loginId) = 0 or $(login) = 'admin'`替换为`hasNamedRight('admin')` ，以便所有具有管理员权限的用户都可以看到这些密码。

## 保护包含PII的页面

我们强烈建议内部部署客户保护可能包含个人信息（如镜像页面、Web应用程序等）的页面。

此过程的目标是防止这些页面被编入索引，从而避免潜在的安全风险。 以下是一些有用的文章：

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

要保护您的页面，请执行以下步骤：

1. 在Web服务器（Apache或IIS）的根位置添加robots.txt文件。 以下是文件的内容：

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   对于IIS，请参见[此页](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files)。

   对于Apache，可以将文件放置在&#x200B;**/var/www/robots.txt**(Debian)中。

1. 有时，添加&#x200B;**robots.txt**&#x200B;文件在安全性方面是不够的。 例如，如果其他网站包含指向您页面的链接，则该链接可能会显示在搜索结果中。

除了&#x200B;**robots.txt**&#x200B;文件外，还建议添加&#x200B;**X-Robots-Tag**&#x200B;标头。 您可以在Apache或IIS中以及在&#x200B;**serverConf.xml**&#x200B;配置文件中执行此操作。

有关更多信息，请参阅[本文](https://developers.google.com/search/reference/robots_meta_tag)。
