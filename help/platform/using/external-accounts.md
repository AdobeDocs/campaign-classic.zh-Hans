---
title: 外部帐户
seo-title: 外部帐户
description: 外部帐户
seo-description: null
page-status-flag: never-activated
uuid: e06e7a36-b449-4ab0-a4f6-fa82dbb8de11
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: da60b9ca-4b51-4bff-affc-2b12c576973a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6ae45cbd87fc0152fc654202e03501fc8d2abd06

---


# 外部帐户{#external-accounts}

外部帐户是一种配置，允许您配置和测试对Adobe Campaign外部服务器的访问。 这些外部帐户可用于Campaign工作流程中访问和管理数据。

您可以设置以下类型的外部帐户：

* [传送外部帐户](#routing-external-account)
* [FTP外部帐户](#ftp-external-account)
* [外部数据库外部帐户](#external-database-external-account)
* [Web Analytics外部帐户](#web-analytics-external-account)
* [Facebook Connect外部帐户](#facebook-connect-external-account)
* [执行实例外部帐户](#execution-instance-external-account)
* [Adobe Experience cloud外部帐户](#adobe-experience-cloud-external-account)
* [SFTP外部帐户](#sftp-external-account)
* [Adobe Experience manager外部帐户](#adobe-experience-manager-external-account)
* [Amazon Simple Storage Service(S3)外部帐户](#amazon-simple-storage-service--s3--external-account)
* [Azure外部帐户](#azure-external-account)
* [Hadoop外部帐户](#hadoop-external-account)
* [Microsoft Dynamics CRM外部帐户](#microsoft-dynamics-crm-external-account)
* [Oracle on demand外部帐户](#oracle-on-demand-external-account)
* [Salesforce CRM外部帐户](#salesforce-crm-external-account)

## 创建外部帐户 {#creating-an-external-account}

Adobe Campaign附带一组预定义的外部帐户。 要与外部系统（如用于文件传输的FTP服务器）建立连接，您可以创建自己的外部帐户。

技术流程（如技术工作流或营销活动工作流程）使用外部帐户。 在工作流中设置文件传输或与任何其他应用程序（Adobe Target、Experience Manager等）进行数据交换时，您需要选择一个外部帐户。

1. 从中 **[!UICONTROL Explorer]**&#x200B;展开菜 **[!UICONTROL Administration]** 单。
1. 展开菜 **[!UICONTROL Platform]** 单并单击 **[!UICONTROL External accounts]**。

   ![](assets/ext_account_1.png)

1. Click the **[!UICONTROL New]** button.

   ![](assets/ext_account_2.png)

1. 输入 **[!UICONTROL Label]** 和 **[!UICONTROL Internal Name]**。 在工作流中选择外部帐户时，将同时使用这两个帐户。
1. 检查 **[!UICONTROL Enabled]** 您是否希望启用连接。
1. 选择要创建 **[!UICONTROL Type]** 的外部帐户。
1. 根据所选的外部帐户类型指定凭据，以配置对帐户的访问权限。

   必需的信息通常由您所连接的服务器的提供者提供。

1. 单击 **[!UICONTROL Save]**.

将创建外部帐户并将其添加到外部帐户列表。 它现在可用于工作流活动和交付属性中的数据／文件传输或路由配置。

## 弹回邮件外部帐户 {#bounce-mails-external-account}

弹 **回邮件** ，外部帐户指定用于连接到电子邮件服务的外部POP3帐户。 For more on this external account, refer to this [page](../../workflow/using/inbound-emails.md).

为POP3访问配置的所有服务器都可用于接收返回邮件。

![](assets/ext_account_6.png)

要配置外部帐 **[!UICONTROL Bounce mails (defaultPopAccount)]** 户，请执行以下操作：

* **[!UICONTROL Server]**

   POP3服务器的URL。

* **[!UICONTROL Port]**

   POP3连接端口号。 默认端口为110。

* **[!UICONTROL Account]**

   用户的名称。

* **[!UICONTROL Password]**

   用户帐户密码。

* **[!UICONTROL Encryption]**

   在、或之间选择的加 **[!UICONTROL By default]**&#x200B;密 **[!UICONTROL POP3 + STARTTLS]**&#x200B;的类 **[!UICONTROL POP3]** 型 **[!UICONTROL POP3S]**。

## 传送外部帐户 {#routing-external-account}

外 **[!UICONTROL Routing]** 部帐户允许您根据安装的包配置Adobe Campaign中可用的每个渠道。

![](assets/ext_account_7.png)

可以配置以下渠道：

* [电子邮件](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [移动(SMS)](../../delivery/using/sms-channel.md#activating-an-external-account)。
* [电话](../../delivery/using/other-channels.md)
* [直邮](../../delivery/using/about-direct-mail-channel.md)
* [代理](../../delivery/using/other-channels.md)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS渠道](../../delivery/using/setting-up-mobile-app-channel.md#ios-connectors)
* [Android通道](../../delivery/using/setting-up-mobile-app-channel.md#android-connectors)

## FTP外部帐户 {#ftp-external-account}

通过FTP外部帐户，您可以配置和测试对Adobe Campaign外部服务器的访问。 要与外部系统（如用于文件传输的FTP服务器898）建立连接，您可以创建自己的外部帐户。 For more on this, refer to this [page](../../workflow/using/file-transfer.md).

为此，请在此外部帐户中指定用于建立与FTP服务器连接的地址和凭据

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

   FTP服务器的名称。

* **[!UICONTROL Port]**

   FTP连接端口号。 默认端口为21。

* **[!UICONTROL Account]**

   用户的名称。

* **[!UICONTROL Password]**

   用户帐户密码。

* **[!UICONTROL Encryption]**

   在或之间选择的加 **[!UICONTROL None]** 密类型 **[!UICONTROL SSL]**。

要了解这些凭据的查找位置，请参阅此 [页](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials)。

## 外部数据库外部帐户 {#external-database-external-account}

Adobe Campaign提供了多个连接器，允许您与外部应用程序通信并连接到数据库引擎。

![](assets/ext_account_11.png)

可以配置以下连接类型：

* Oracle。 For more information, refer to this [page](../../platform/using/accessing-an-external-database.md#configure-access-to-oracle).
* MySQL。 要配置对MYSQL的访问，请参阅此 [页](../../platform/using/accessing-an-external-database.md#configure-access-to-mysql)。
* 老千。 For more information, refer to this [page](../../platform/using/accessing-an-external-database.md#configure-access-to-netezza).
* SAP HANA。 For more information, refer to this [page](../../platform/using/accessing-an-external-database.md#configure-access-to-sap-hanaa).
* InfiniDB
* Microsoft SQL Server
* AsterData
* PostgreSQL
* Teradata
* DB2
* Amazon Redshift
* ODBC(Sybase ASE, Sybase IQ)
* HTTP中继到远程数据库

### Teradata外部帐户 {#teradata-external-account}

通过 **Teradata** 外部帐户，您可以将Campaign实例连接到Teradata外部数据库。 有关如何使用Teradata配置Campaign Classic的详细信息，请参阅本页 [或](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) 本节 [内容](../../platform/using/accessing-an-external-database.md#configure-access-to-teradata)。

![](assets/ext_account_19.png)

要配置此外部帐户以与Adobe Campaign一起使用，您需要提供以下详细信息：

* **[!UICONTROL Type]**

   选择类 **[!UICONTROL Teradata]** 型。

* **[!UICONTROL Server]**

   Teradata服务器的URL或名称。

* **[!UICONTROL Account]**

   用于访问Teradata数据库的帐户的名称。

* **[!UICONTROL Password]**

   用于连接到Teradata数据库的口令。

* **[!UICONTROL Database]**

   此字段可留空。

* **[!UICONTROL Options]**

   要通过Teradata传递的选项

* **[!UICONTROL Timezone]**

   Teradata中的时区设置

![](assets/ext_account_20.png)

当多个Adobe Campaign用户连接到同一FDA Teradata外部帐户时，该选项卡允许您在会话中设置查询栏，即一组键／值对。 **[!UICONTROL Query banding]**

每次Campaign用户对Teradata数据库执行查询时，Adobe Campaign都会发送元数据，元数据包括与该用户关联的键列表。 然后，Teradata管理员可以将这些数据用于审计目的或管理访问权限。

选中该 **[!UICONTROL Active]** 框以激活此功能

该字 **[!UICONTROL Default]** 段允许您输入默认的查询栏，如果用户没有关联的查询栏，则将使用该栏。 如果此字段留空，则没有查询带的用户将无法使用Teradata。

该字 **[!UICONTROL Users]** 段允许您为每个用户指定查询栏。 您可以添加所需数量的键／值对，例如priority=1;workload=high。 如果用户未分配查询栏，则 **[!UICONTROL Default]** 将应用该字段。

有关的详细信 **[!UICONTROL Query banding]**&#x200B;息，请参阅 [Teradata文档](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw)。

## Web Analytics外部帐户 {#web-analytics-external-account}

外 **[!UICONTROL Web Analytics (Adobe Analytics - Data connector)]** 部帐户允许您以细分形式将数据从Adobe Analytics转发到Adobe Campaign。 相反，它会将Adobe Campaign提供的电子邮件营销活动的指标和属性发送到Adobe Analytics - Data connector。

![](assets/ext_account_10.png)

对于此外部帐户，必须丰富跟踪URL的计算公式，并批准两个解决方案之间的连接。 For more on this, refer to this [page](../../platform/using/adobe-analytics-data-connector.md#step-2--create-the-external-account-in-campaign).

## Facebook Connect外部帐户 {#facebook-connect-external-account}

外部 **[!UICONTROL Facebook Connect]** 帐户可让您在Facebook应用程序中显示个性化内容，从而更轻松地通过此社交网络获取潜在客户。

对于每个Facebook应用程序，您需要创建一个类 **[!UICONTROL Facebook Connect]** 型外部帐户。 For more on this, refer to [page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   或之间的应用程序托管 **[!UICONTROL hosted by a partner]** 模式 **[!UICONTROL hosted by this instance]**。

* **[!UICONTROL Application ID]**

   您的Facebook应用程序的应用程序ID。

* **[!UICONTROL Application secret]**

   您的Facebook应用程序的应用程序机密

如果选择由此实例模式托管，则需要将安全画布URL粘贴到Facebook上的 **Facebook web游戏(https)字段**

要了解这些凭据的查找位置，请参阅此 [页](https://developers.facebook.com/docs/facebook-login/access-tokens)。

## 执行实例外部帐户 {#execution-instance-external-account}

如果您有分解架构，则需要指定与控件实例链接的执行实例并连接它们。 事务消息模板被部署到执行实例

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   安装执行实例的服务器的URL。

* **[!UICONTROL Account]**

   帐户的名称，必须与操作符文件夹中定义的消息中心代理匹配。

* **[!UICONTROL Password]**

   操作符文件夹中定义的帐户密码。

For more information on this configuration, refer to this [page](../../message-center/using/creating-a-shared-connection.md#control-instance).

## Adobe Experience cloud外部帐户 {#adobe-experience-cloud-external-account}

要使用Adobe ID连接到Adobe Campaign控制台，必须配置外 **[!UICONTROL Adobe Experience Cloud (MAC)]** 部帐户。

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   IMS服务器的URL。 确保舞台和生产实例都指向同一个IMS生产端点。

* **[!UICONTROL IMS scope]**

   此处定义的范围必须是IMS提供的范围的子集。

* **[!UICONTROL IMS client identifier]**

   IMS客户端的ID。

* **[!UICONTROL IMS client secret]**

   IMS客户端机密的凭据

* **[!UICONTROL Callback server]**

   访问Adobe Campaign实例的URL

* **[!UICONTROL IMS organization ID]**

   IMS组织的ID。 要查找您的组织ID，请参阅此 [页](https://marketing.adobe.com/resources/help/en_US/mcloud/faq.html) (在&#x200B;**哪里可以找到我的IMS组织ID?**)。

* **[!UICONTROL Association mask]**

   允许Enterprise Dashboard中的配置名称与Adobe Campaign中的组同步的语法。

* **[!UICONTROL Server]**

   您的Adobe Experience cloud实例的URL。

* **[!UICONTROL Tenant]**

   您的Adobe Experience cloud租户的名称。

For more information on this configuration, refer to this [page](../../integrations/using/configuring-ims.md).

## SFTP外部帐户 {#sftp-external-account}

通过SFTP外部帐户，您可以配置和测试对Adobe Campaign外部服务器的访问。 要与外部系统（如用于文件传输的SFTP）建立连接，您可以创建自己的外部帐户。 For more on this, refer to this [page](../../workflow/using/file-transfer.md).

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   SFTP服务器的URL。

* **[!UICONTROL Port]**

   FTP连接端口号。 默认端口为22。

* **[!UICONTROL Account]**

   用于连接到SFTP服务器的帐户名。

* **[!UICONTROL Password]**

   用于连接到SFTP服务器的口令。

## Adobe Experience manager外部帐户 {#adobe-experience-manager-external-account}

外部 **[!UICONTROL AEM (AEM instance)]** 帐户允许您直接在Adobe Experience manager中管理电子邮件分发以及表单的内容。

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   Adobe Experience Manager服务器的URL。

* **[!UICONTROL Port]**

   用于连接到Adobe Experience manager创作实例的帐户名称。

* **[!UICONTROL Password]**

   用于连接到Adobe Experience manager创作实例的口令。

For more on this, refer to this [section](../../integrations/using/about-adobe-experience-manager.md).

## Amazon Simple Storage Service(S3)外部帐户 {#amazon-simple-storage-service--s3--external-account}

Amazon Simple Storage Service(S3)连接器可用于将数据导入或导出到Adobe Campaign。 可以在工作流活动中设置它。 For more on this, refer to this [page](../../workflow/using/file-transfer.md).

![](assets/ext_account_3.png)

在设置此新外部帐户时，您需要提供以下详细信息：

* **[!UICONTROL AWS S3 Account Server]**

   服务器的URL，应按如下方式填写：

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   要了解在何处找到您的AWS访问密钥ID，请参阅此 [页](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) 。

* **[!UICONTROL Secret access key to AWS]**

   要了解在何处找到AWS的秘密访问密钥，请参阅本 [页](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)。

* **[!UICONTROL AWS Region]**

   要了解有关AWS区域的更多信息，请参阅本 [页](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)。

* 此复 **[!UICONTROL Use server side encryption]** 选框允许您以S3加密模式存储文件。

要了解在何处查找访问密钥ID和秘密访问密钥，请参阅Amazon web服务文 [档](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) 。

## Azure外部帐户 {#azure-external-account}

外部 **[!UICONTROL Azure]** 帐户支持与共享外部数据库的连接，只要此连接处于活动状态，就可以通过Adobe Campaign访问该数据库。

![](assets/ext_account_15.png)

* **[!UICONTROL Server]**

   Azure服务器的URL。

* **[!UICONTROL Encryption]**

   在或之间选择的加 **[!UICONTROL None]** 密类型 **[!UICONTROL SSL]**。

* **[!UICONTROL Access key]**

   要了解在何处查找访问密钥，请参阅此页 [面](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-manage) (查看 **和复制访问密钥部分**)。

## Hadoop外部帐户 {#hadoop-external-account}

外部 **[!UICONTROL Hadoop]** 帐户支持与共享外部数据库的连接，只要此连接处于活动状态，就可以通过Adobe Campaign访问该数据库。 有关如何配置对Hadoop的访问的详细信息，请参阅此 [部分](../../platform/using/accessing-an-external-database.md#configure-access-to-hadoop)。

![](assets/ext_account_16.png)

* **[!UICONTROL Server]**

   Hadoop服务器的URL。

* **[!UICONTROL User account name]**

   用于访问Hadoop的帐户的名称。

## Microsoft Dynamics CRM外部帐户 {#microsoft-dynamics-crm-external-account}

外 **[!UICONTROL Microsoft Dynamics CRM]** 部帐户允许您将Microsoft Dynamics数据导入并导出到Adobe Campaign中。

Microsoft Dynamics连接器的Adobe Campaign配置取决于您的部署类型。
对于 **[!UICONTROL On-premise]** 和部 **[!UICONTROL Office 365]** 署类型，您需要提供以下详细信息：

![](assets/ext_account_21.png)

* **[!UICONTROL Account]**

   用于登录Microsoft CRM的帐户。

* **[!UICONTROL Server]**

   Microsoft CRM服务器的URL。

* **[!UICONTROL Password]**

   用于登录Microsoft CRM的口令。

* **[!UICONTROL Company name]** 用于内部部署和Office 365部署

   您的公司名称。

* **[!UICONTROL Organization name]** 用于内部部署

   您的组织的名称。
组织名称，可在Microsoft Dynamics的“开发人员资源”功能板中找到，该字 **[!UICONTROL Unique Name]** 段为。

* **[!UICONTROL CRM version]** 适用于内部部署

   或之间的CRM **[!UICONTROL Dynamics CRM 2007]**&#x200B;版 **[!UICONTROL Dynamics CRM 2015]** 本 **[!UICONTROL Dynamics CRM 2016]**。

使用 **[!UICONTROL Web API]** 部署类型 **[!UICONTROL Password credentials]** 和身份验证，您需要提供以下详细信息：

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   用于登录Microsoft CRM的帐户。

* **[!UICONTROL Server]**

   Microsoft CRM服务器的URL。

* **[!UICONTROL Client identifier]**

   客户端ID，可从类别字段中的Microsoft azure管理门 **[!UICONTROL Update your code]** 户中找到 **[!UICONTROL Client ID]** 它。

* **[!UICONTROL CRM version]**

   或之间的CRM **[!UICONTROL Dynamics CRM 2007]**&#x200B;版 **[!UICONTROL Dynamics CRM 2015]** 本 **[!UICONTROL Dynamics CRM 2016]**。

使用 **[!UICONTROL Web API]** 部署类型 **[!UICONTROL Certificate]** 和身份验证，您需要提供以下详细信息：

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   Microsoft CRM服务器的URL。

* **[!UICONTROL Private Key (Base64 encoded)]**

   编码为Base64的私钥

* **[!UICONTROL Custom Key identifier]**


* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   客户端ID，可从类别字段中的Microsoft azure管理门 **[!UICONTROL Update your code]** 户中找到 **[!UICONTROL Client ID]** 它。

* **[!UICONTROL CRM version]**

   或之间的CRM **[!UICONTROL Dynamics CRM 2007]**&#x200B;版 **[!UICONTROL Dynamics CRM 2015]** 本 **[!UICONTROL Dynamics CRM 2016]**。

For more information on this configuration, refer to this [page](../../platform/using/crm-connectors.md#example-for-microsoft-dynamics).

## Oracle on demand外部帐户 {#oracle-on-demand-external-account}

外 **[!UICONTROL Oracle on demand]** 部帐户允许您将Oracle数据导入和导出到Adobe Campaign中。

![](assets/ext_account_18.png)

要配置Oracle按需外部帐户以与Adobe Campaign结合使用，您需要提供以下详细信息：

* **[!UICONTROL Account]**

   用于登录Oracle CRM（按需）的帐户。

* **[!UICONTROL Server]**

   Oracle CRM on demand服务器的URL。

* **[!UICONTROL Password]**

   用于登录Oracle CRM点播的密码。

For more information on this configuration, refer to this [page](../../platform/using/crm-connectors.md#example-for-oracle-on-demand).

## Salesforce CRM外部帐户 {#salesforce-crm-external-account}

外 **[!UICONTROL Salesforce CRM]** 部帐户允许您将Salesforce数据导入和导出到Adobe Campaign。

![](assets/ext_account_17.png)

要配置Salesforce CRM外部帐户以与Adobe Campaign结合使用，您需要提供以下详细信息：

* **[!UICONTROL Account]**

   用于登录Salesforce CRM的帐户。

* **[!UICONTROL Password]**

   用于登录Salesforce CRM的口令。

* **[!UICONTROL Client identifier]**

   要了解在何处查找客户端标识符，请参阅此 [页](https://help.salesforce.com/articleView?id=000205876&type=1)。

* **[!UICONTROL Security token]**

   要了解在何处找到您的安全令牌，请参阅此 [页](https://help.salesforce.com/articleView?id=000205876&type=1)。

* **[!UICONTROL API version]**

   或之间的API **[!UICONTROL Version 37]**&#x200B;版 **[!UICONTROL Version 21]** 本 **[!UICONTROL Version 15]**。

对于此外部帐户，您需要使用配置向导配置Salesforce CRM。

For more information on this configuration, refer to this [page](../../platform/using/crm-connectors.md#example-for-salesforce-com).
