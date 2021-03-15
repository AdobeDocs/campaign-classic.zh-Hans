---
solution: Campaign Classic
product: campaign
title: 隐私
description: 了解有关隐私权的最佳实践的更多信息。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 隐私 {#privacy}

## 隐私请求

Adobe Campaign 提供一套工具，可帮助您确保符合《欧盟通用数据保护条例》(GDPR) 和《加州消费者隐私法案》(CCPA) 的隐私政策。

有关隐私管理的一般信息以及Adobe Campaign中的实施步骤，请参阅[本页](../../platform/using/privacy-management.md)。 您还将找到最佳实践以及用户流程和角色的概述。

## URL个性化{#url-personalization}

在向内容添加个性化链接时，请始终避免在URL的主机名部分包含任何个性化，以避免潜在的安全漏洞。 以下示例不应用于所有URL属性&lt;`a href="">`或`<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 建议

要验证并确保您未使用上述查询，请通过[活动通用查询编辑器](../../platform/using/steps-to-create-a-query.md)对跟踪URL表运行一个，或在[查询活动](../../workflow/using/query.md)中创建具有过滤器标准的工作流。

示例:

1. 创建工作流并添加查询活动。 了解详情.

1. 打开查询活动，并在nmsTrackingUrl表上创建过滤器，如下所示：源URL开始为http://&lt;%，源URL开始为https://&lt;%。

1. 运行工作流并检查是否有结果。

1. 如果是，请打开输出过渡以视图URL的列表。

<img src="assets/privacy-query-dynamic-url.png">

### 签名机制

为了提高安全性，内部版本19.1.4(9032@3a9dc9c)中引入了用于跟踪电子邮件中链接的新签名机制，内部版本19.1.4(9032@3a9dc9c)和活动 20.2中提供了该机制。默认情况下，对所有客户都启用此选项。

>[!NOTE]
>
>单击格式错误的签名URL时，将返回以下错误：&quot;未找到请求的URL&quot;。..&quot;。&quot;

此外，从活动 20.2和Gold Standard版本开始，托管和混合客户可以使用增强功能禁用从先前构建生成的URL。 此选项在默认情况下处于禁用状态。 您可以联系[客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)来启用此功能。

要激活此新机制，预置型客户需要在所有活动服务器上执行以下步骤：

1. 在服务器配置文件(serverConf.xml)中，将&#x200B;**blockRedirectForUnsignedTrackingLink**&#x200B;更改为&#x200B;**true**。
1. 重新启动&#x200B;**nlserver**&#x200B;服务。
1. 在跟踪服务器上，重新启动Web服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

在Gold Standard 19.1.4上运行的客户可能会使用跟踪链接遇到推送通知投放问题，或使用锚记标签的投放。 如果是，Adobe建议禁用用于跟踪链接的新签名机制：

**托管和混合** 客户必须联系 [Customer ](https://helpx.adobe.com/cn/enterprise/using/support-for-experience-cloud.html) Careto禁用此机制。

**预置型客** 户扫描遵循以下步骤：

1. 在服务器配置文件(serverConf.xml)中，将&#x200B;**signEmailLinks**&#x200B;更改为&#x200B;**false**。
1. 重新启动&#x200B;**nlserver**&#x200B;服务。
1. 在跟踪服务器上，重新启动Web服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

## 数据限制

您必须确保经过身份验证的低权限用户无法访问加密的口令。 为此，有两种主要方式：仅限对密码字段或对整个实体（需要内部版本>= 8770）的访问。

此限制允许您删除口令字段，但允许所有用户从界面访问外部帐户。 请参见[此页面](../../configuration/using/restricting-pii-view.md)。

1. 进入&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**。

1. 新建&#x200B;**[!UICONTROL Extension of a schema]**。

   ![](assets/privacy-data-restriction.png)

1. 选择&#x200B;**[!UICONTROL External Account]**(extAccount)。

1. 在最后一个向导屏幕中，您可以编辑新的srcSchema以限制对所有口令字段的访问：

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

   因此，您的扩展srcSchema可以如下所示：

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
   >您可以通过`hasNamedRight('admin')`将`$(loginId) = 0 or $(login) = 'admin'`替换为允许具有管理员权限的所有用户查看这些密码。

## 保护包含PII的页面

我们强烈建议预置型客户保护可能包含个人信息(如镜像页面、Web应用程序等)的页面。

此程序的目标是防止这些页面被索引，从而避免潜在的安全风险。 以下是一些有用的文章：

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

要保护您的页面，请执行以下步骤：

1. 在Web服务器（Apache或IIS）的根位置添加robots.txt文件。 下面是文件的内容：

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   对于IIS，请参阅[此页](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files)。

   对于Apache，可以将文件放置在&#x200B;**/var/www/robots.txt**(Debian)中。

1. 有时，添加&#x200B;**robots.txt**&#x200B;文件在安全性方面是不够的。 例如，如果其他网站包含指向您的页面的链接，则该链接可能显示在搜索结果中。

除了&#x200B;**robots.txt**&#x200B;文件外，还建议添加&#x200B;**X-Robots-Tag**&#x200B;标头。 您可以在Apache或IIS中，在&#x200B;**serverConf.xml**&#x200B;配置文件中执行此操作。

有关详细信息，请参阅[本文](https://developers.google.com/search/reference/robots_meta_tag)。
