---
product: campaign
title: 个性化和隐私
description: 了解隐私和个性化的安全最佳实践
feature: Installation, Privacy, Privacy Tools, URL Personalization
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: a2106e55617209f28da42c50008d16188563b2da
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 3%

---

# 个性化和隐私 {#privacy}

## URL个性化 {#url-personalization}

向内容添加个性化链接时，请始终避免在URL的主机名部分进行任何个性化设置，以避免潜在的安全缺口。 绝不应该在所有URL属性中使用以下示例&lt;`a href="">` 或 `<img src="">`：

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 推荐

要验证并确保未使用上文，请通过以下方式运行跟踪URL表上的查询： [Campaign通用查询编辑器](../../platform/using/steps-to-create-a-query.md) 或者，使用中的筛选条件创建工作流 [查询活动](../../workflow/using/query.md).

例如：

1. 创建工作流并添加 **查询** 活动。 [了解详情](../../workflow/using/query.md)。

1. 打开 **查询** 活动，并根据以下内容创建过滤器： `nmsTrackingUrl` 表如下：

   `source URL starts with http://<% or source URL starts with https://<%`

1. 运行工作流并检查结果是否存在。

1. 如果是这样，请打开输出过渡以查看URL列表。

   ![](assets/privacy-query-dynamic-url.png)


### URL签名

为了提高安全性，引入了一种用于跟踪电子邮件中链接的签名机制。 它从19.1.4版(9032@3a9dc9c)和20.2版开始提供。此功能默认处于启用状态。

>[!NOTE]
>
>单击格式错误的签名URL时，将返回此错误： `Requested URL '…' was not found.`

此外，您还可以使用增强功能来禁用在以前的内部版本中生成的URL。 默认情况下，此功能处于禁用状态。 您可以联系 [客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 以启用此功能。

如果您在19.1.4内部版本上运行，则在使用跟踪链接或使用锚点标记进行投放时可能会遇到问题。 如果出现这种情况，建议您禁用URL签名。

作为Campaign托管、托管Cloud Service或混合型客户，您必须联系 [客户关怀](https://helpx.adobe.com/cn/enterprise/using/support-for-experience-cloud.html) 禁用URL签名。

如果您在混合架构中运行Campaign，则在启用URL签名之前，请确保已如下所示升级托管的中源实例：

* 首先是内部部署营销实例
* 然后，升级到与内部部署营销实例相同的版本或略高的版本

否则，可能会出现以下一些问题：

* 在升级中间源实例之前，将通过该实例发送URL，而不进行签名。
* 升级中间源实例并在两个实例上启用URL签名后，先前未签名发送的URL将被拒绝。 原因是营销实例提供的跟踪文件需要签名。

要禁用以前内部版本中生成的URL，请同时在所有Campaign服务器上执行以下步骤：

1. 在服务器配置文件中(`serverConf.xml`)，更改 **blockRedirectForUnsignedTrackingLink** 选项至 **true**.
1. 重新启动 `nlserver` 服务。
1. 在 `tracking` 服务器，重新启动 `web` 服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

要启用URL签名，请同时在所有Campaign服务器上执行以下步骤：

1. 在服务器配置文件中(`serverConf.xml`)，更改 **signEmailLinks** 选项，至 **true**.
1. 重新启动 **nlserver** 服务。
1. 在 `tracking` 服务器，重新启动 `web` 服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

## 数据限制

您必须确保低权限验证用户无法访问加密密码。 为此，应限制仅访问密码字段，或访问整个实体（需要build >= 8770）。

此限制允许您删除密码字段，但允许所有用户从界面访问外部帐户。 [了解详情](../../configuration/using/restricting-pii-view.md)。

要执行此操作，请按照以下步骤进行：

1. 浏览至 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** Campaign资源管理器的文件夹。

1. 创建数据架构，作为 **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. 选择 **[!UICONTROL External Account]** (extAccount)。

1. 在最后一个向导屏幕中，编辑新的“srcSchema”以限制对所有密码字段的访问：

   您可以替换主元素(`<element name="extAccount" ... >`)，按照：

   ```sql
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

   因此，您的扩展srcSchema可能如下所示：

   ```sql
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
   >您可以替换 `$(loginId) = 0 or $(login) = 'admin'` 替换为 `hasNamedRight('admin')` 允许所有具有管理员权限的用户查看这些密码。

## 带PI的Protect页面

我们强烈建议内部部署客户保护可能包含个人信息(PI)的页面，如镜像页面、Web应用程序等。

此过程的目标是防止对这些页编制索引，从而避免潜在的安全风险。 以下是一些有用的文章：

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

要保护您的页面，请执行以下步骤：

1. 添加 `robots.txt` 文件，该文件位于Web服务器的根目录下（Apache或IIS）。 以下是文件的内容：

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   对于IIS，请参阅 [此页面](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   对于Apache，您可以将该文件放入 **/var/www/robots.txt** (Debian)。

1. 有时添加 **robots.txt** 文件的安全性不够。 例如，如果其他网站包含指向您的页面的链接，则该链接可能会显示在搜索结果中。

   除了 **robots.txt** 文件，建议添加 **X-Robots-Tag** 标题。 您可以在Apache或IIS中以及在 **serverConf.xml** 配置文件。

   有关更多信息，请参阅 [本文](https://developers.google.com/search/reference/robots_meta_tag).


## 隐私请求

请参阅 [此页面](../../platform/using/privacy-management.md) 有关Adobe Campaign中隐私管理的概念和实施步骤的一般信息。 您还可以找到最佳实践以及用户流程和角色的概述。
