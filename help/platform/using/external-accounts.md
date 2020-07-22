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
source-git-commit: c1f7ff6a281c2830ac23ad995b750dc09ade5e92
workflow-type: tm+mt
source-wordcount: '2218'
ht-degree: 0%

---


# 外部帐户{#external-accounts}

外部帐户是一种配置，允许您配置和测试对Adobe Campaign外部服务器的访问。 这些外部帐户可用于活动工作流访问和管理数据。

您可以设置以下类型的外部帐户:

* [路由外部帐户](#routing-external-account)
* [FTP外部帐户](#ftp-external-account)
* [外部数据库外部帐户](#external-database-external-account)
* [WebAnalytics外部帐户](#web-analytics-external-account)
* [Facebook连接外部帐户](#facebook-connect-external-account)
* [执行实例外部帐户](#execution-instance-external-account)
* [Adobe Experience Cloud外部帐户](#adobe-experience-cloud-external-account)
* [SFTP外部帐户](#sftp-external-account)
* [Adobe Experience Manager外部帐户](#adobe-experience-manager-external-account)
* [Amazon Simple存储服务(S3)外部帐户](#amazon-simple-storage-service--s3--external-account)
* [Azure外部帐户](#azure-external-account)
* [Hadoop外部帐户](#hadoop-external-account)
* [Microsoft Dynamics CRM外部帐户](#microsoft-dynamics-crm-external-account)
* [Oracle按需外部帐户](#oracle-on-demand-external-account)
* [Salesforce CRM外部帐户](#salesforce-crm-external-account)

## 创建外部帐户 {#creating-an-external-account}

Adobe Campaign附带一组预定义外部帐户。 要与外部系统（如用于文件传输的FTP服务器）建立连接，您可以创建自己的外部帐户。

外部帐户由技术工作流或活动工作流等技术流程使用。 在工作流中设置文件传输或与任何其他应用程序(Adobe Target、Experience Manager等)进行数据交换时，您需要选择外部帐户。

1. 从中 **[!UICONTROL Explorer]**&#x200B;展开菜 **[!UICONTROL Administration]** 单。
1. 展开菜 **[!UICONTROL Platform]** 单并单击 **[!UICONTROL External accounts]**。

   ![](assets/ext_account_1.png)

1. 单击&#x200B;**[!UICONTROL New]**&#x200B;按钮。

   ![](assets/ext_account_2.png)

1. 输入 **[!UICONTROL Label]** 和 **[!UICONTROL Internal Name]**。 在工作流中选择外部帐户时，将同时使用这两种方法。
1. 检 **[!UICONTROL Enabled]** 查您是否希望启用连接。
1. 选择要 **[!UICONTROL Type]** 创建的外部帐户。
1. 根据所选的外部帐户类型指定凭据，以配置对帐户的访问。

   必需信息通常由您所连接的服务器的提供者提供。

1. 单击 **[!UICONTROL Save]**.

将创建外部帐户并将其添加到外部帐户列表。 它现在可用于工作流活动和路由属性中的数据／文件传输或投放配置。

## 弹回邮件外部帐户 {#bounce-mails-external-account}

弹 **回邮件** 外部帐户指定用于连接电子邮件服务的外部POP3帐户。 For more on this external account, refer to this [page](../../workflow/using/inbound-emails.md).

为POP3访问配置的所有服务器都可用于接收返回邮件。

![](assets/ext_account_6.png)

配置 **[!UICONTROL Bounce mails (defaultPopAccount)]** 外部帐户:

* **[!UICONTROL Server]**

   POP3服务器的URL。

* **[!UICONTROL Port]**

   POP3连接端口号。 默认端口为110。

* **[!UICONTROL Account]**

   用户的名称。

* **[!UICONTROL Password]**

   用户帐户密码。

* **[!UICONTROL Encryption]**

   在、或之间选 **[!UICONTROL By default]**&#x200B;择 **[!UICONTROL POP3 + STARTTLS]**&#x200B;的加 **[!UICONTROL POP3]** 密类型 **[!UICONTROL POP3S]**。

## 路由外部帐户 {#routing-external-account}

该 **[!UICONTROL Routing]** 外部帐户允许您根据所安装的包配置Adobe Campaign中可用的每个渠道。

![](assets/ext_account_7.png)

可以配置以下渠道:

* [电子邮件](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [移动(SMS)](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)
* [电话](../../delivery/using/communication-channels.md#other-channels)
* [直邮](../../delivery/using/about-direct-mail-channel.md)
* [代理](../../delivery/using/communication-channels.md#other-channels)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS渠道](../../delivery/using/configuring-the-mobile-application.md#configuring-the-mobile-application-ios)
* [Android渠道](../../delivery/using/configuring-the-mobile-application.md#configuring-the-mobile-application-android)

## FTP外部帐户 {#ftp-external-account}

FTP外部帐户允许您配置和测试对Adobe Campaign外服务器的访问。 要与外部系统（如用于文件传输的FTP服务器898）建立连接，您可以创建自己的外部帐户。 For more on this, refer to this [page](../../workflow/using/file-transfer.md).

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

   在或之间选择的加 **[!UICONTROL None]** 密的类 **[!UICONTROL SSL]**&#x200B;型。

要了解这些凭据的位置，请参阅此 [页](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials)。

## 外部数据库外部帐户 {#external-database-external-account}

Adobe Campaign提供了多个连接器，允许您与外部应用程序通信并连接到数据库引擎。

![](assets/ext_account_11.png)

可以配置以下连接类型：

* Azure突触。 For more information, refer to this [page](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse).
* 甲骨文。 For more information, refer to this [page](../../platform/using/specific-configuration-database.md#configure-access-to-oracle).
* 内泰扎。 For more information, refer to this [page](../../platform/using/specific-configuration-database.md#configure-access-to-netezza).
* SAP HANA。 For more information, refer to this [page](../../platform/using/specific-configuration-database.md#configure-access-to-sap-hana).
* InfiniDB
* Microsoft SQL Server
* AsterData
* PostgreSQL
* Teradata
* DB2
* Amazon Redshift
* ODBC(Sybase ASE、Sybase IQ)
* HTTP中继到远程数据库

### 雪花外部帐户 {#snowflake-external-account}

雪 **花外部帐户** ，可将活动实例连接到雪花外部数据库。 有关如何使用雪花配置Campaign Classic的详细信息，请参阅 [本页](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)。

要配置此外部帐户以与Adobe Campaign配合使用，您需要提供以下详细信息：

* **[!UICONTROL Server]**

       雪花服务器的URL。
   
* **[!UICONTROL Account]**

       用户的名称。
   
* **[!UICONTROL Password]**

       用户帐户密码。
   
* **[!UICONTROL Database]**

       数据库的名称。
   
![](assets/snowflake.png)

### Teradata外部帐户 {#teradata-external-account}

Teradata **外部帐户** 允许您将活动实例连接到Teradata外部数据库。 有关如何使用Teradata配置Campaign Classic的详细信息，请参 [阅本页](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) 或本 [部分](../../platform/using/specific-configuration-database.md#configure-access-to-teradata)。

![](assets/ext_account_19.png)

要配置此外部帐户以与Adobe Campaign配合使用，您需要提供以下详细信息：

* **[!UICONTROL Type]**

   选择类 **[!UICONTROL Teradata]** 型。

* **[!UICONTROL Server]**

   您的Teradata服务器的URL或名称。

* **[!UICONTROL Account]**

   用于访问Teradata数据库的帐户的名称。

* **[!UICONTROL Password]**

   用于连接到Teradata数据库的口令。

* **[!UICONTROL Database]**

   此字段可以留空。

* **[!UICONTROL Options]**

   通过Teradata传递的选项。

* **[!UICONTROL Timezone]**

   在Teradata中设置时区。

![](assets/ext_account_20.png)

当多个Adobe Campaign用户连接到同一联合数据访问Teradata外部帐户时，该选 **[!UICONTROL Query banding]** 项卡允许您在会话中设置查询带，即一组键／值对。

每次活动用户对Teradata查询库执行时，Adobe Campaign都会发送元数据，元数据由与此用户关联的密钥列表组成。 此数据随后可由Teradata管理员用于审核或管理访问权限。

选中该 **[!UICONTROL Active]** 复选框以激活此功能

通 **[!UICONTROL Default]** 过该字段，您可以输入默认的查询带，在用户没有关联的查询带时将使用该带。 如果此字段留空，则没有查询带的用户将无法使用Teradata。

该 **[!UICONTROL Users]** 字段允许您为每个用户指定查询带。 您可以添加所需数量的键／值对，如priority=1;workload=high。 如果用户未分配查询带， **[!UICONTROL Default]** 将应用该字段。

For more information on **[!UICONTROL Query banding]**, refer to the [Teradata documentation](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

## WebAnalytics外部帐户 {#web-analytics-external-account}

外部帐户 **[!UICONTROL Web Analytics (Adobe Analytics - Data connector)]** 允许您以细分形式将数据从AdobeAnalytics转发到Adobe Campaign。 相反，它会通过Adobe Campaign将电子邮件活动的指示符和属性发送给AdobeAnalytics-数据连接器。

![](assets/ext_account_10.png)

对于此外部帐户，必须丰富跟踪URL的计算公式，并批准两个解决方案之间的连接。 For more on this, refer to this [page](../../platform/using/adobe-analytics-data-connector.md#step-2--create-the-external-account-in-campaign).

## Facebook连接外部帐户 {#facebook-connect-external-account}

该外部帐户 **[!UICONTROL Facebook Connect]** 允许您在Facebook应用程序中显示个性化内容，从而更轻松地通过此社交网络获取潜在客户。

对于每个Facebook应用程序，您需要创建一个类 **[!UICONTROL Facebook Connect]** 型外部帐户。 For more on this, refer to [page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   或之间的应用程序的 **[!UICONTROL hosted by a partner]** 托管模 **[!UICONTROL hosted by this instance]**&#x200B;式。

* **[!UICONTROL Application ID]**

   您的Facebook应用程序的应用程序ID。

* **[!UICONTROL Application secret]**

   您的Facebook应用程序的应用程序机密。

如果选择由此实例模式托管，则“安全Canvas URL”需要粘贴到Facebook **上的Facebook Web Games(https)** 字段中

要了解这些凭据的位置，请参阅此 [页](https://developers.facebook.com/docs/facebook-login/access-tokens)。

## 执行实例外部帐户 {#execution-instance-external-account}

如果您有分解的架构，则需要指定链接到执行实例的控制实例并连接它们。 事务性消息模板部署到执行实例

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   安装执行实例的服务器的URL。

* **[!UICONTROL Account]**

   帐户的名称，必须与操作符文件夹中定义的消息中心代理匹配。

* **[!UICONTROL Password]**

   操作符文件夹中定义的帐户密码。

For more information on this configuration, refer to this [page](../../message-center/using/creating-a-shared-connection.md#control-instance).

## Adobe Experience Cloud外部帐户 {#adobe-experience-cloud-external-account}

要使用Adobe Campaign连接到Adobe ID控制台，必须配置外部帐户。 **[!UICONTROL Adobe Experience Cloud (MAC)]**

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   IMS服务器的URL。 确保舞台和生产实例指向同一IMS生产端点。

* **[!UICONTROL IMS scope]**

   此处定义的范围必须是IMS提供的范围的子集。

* **[!UICONTROL IMS client identifier]**

   IMS客户端的ID。

* **[!UICONTROL IMS client secret]**

   您的IMS客户端机密的凭据。

* **[!UICONTROL Callback server]**

   访问Adobe Campaign实例的URL。

* **[!UICONTROL IMS organization ID]**

   IMS组织的ID。 要查找您的组织ID，请参 [阅本页](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html) (**在哪里可以找到我的IMS组织ID?**)。

* **[!UICONTROL Association mask]**

   允许在企业仪表板中与Adobe Campaign中的组同步的配置名称的语法。

* **[!UICONTROL Server]**

   您的Adobe Experience Cloud实例的URL。

* **[!UICONTROL Tenant]**

   您的Adobe Experience Cloud租户的名称。

For more information on this configuration, refer to this [page](../../integrations/using/configuring-ims.md).

## SFTP外部帐户 {#sftp-external-account}

SFTP外部帐户允许您配置和测试对Adobe Campaign外服务器的访问。 要与外部系统（如用于文件传输的SFTP）建立连接，您可以创建自己的外部帐户。 For more on this, refer to this [page](../../workflow/using/file-transfer.md).

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   SFTP服务器的URL。

* **[!UICONTROL Port]**

   FTP连接端口号。 默认端口为22。

* **[!UICONTROL Account]**

   用于连接到SFTP服务器的帐户名称。

* **[!UICONTROL Password]**

   用于连接到SFTP服务器的口令。

## Adobe Experience Manager外部帐户 {#adobe-experience-manager-external-account}

外部帐户 **[!UICONTROL AEM (AEM instance)]** 允许您直接以Adobe Experience Manager管理电子邮件投放和表单的内容。

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   Adobe Experience Manager服务器的URL。

* **[!UICONTROL Port]**

   用于连接到Adobe Experience Manager创作实例的帐户名称。

* **[!UICONTROL Password]**

   用于连接到Adobe Experience Manager创作实例的口令。

For more on this, refer to this [section](../../integrations/using/about-adobe-experience-manager.md).

## Amazon Simple存储服务(S3)外部帐户 {#amazon-simple-storage-service--s3--external-account}

Amazon Simple存储服务(S3)连接器可用于将数据导入或导出到Adobe Campaign。 可以在工作流活动中设置。 For more on this, refer to this [page](../../workflow/using/file-transfer.md).

![](assets/ext_account_3.png)

在设置此新外部帐户时，您需要提供以下详细信息：

* **[!UICONTROL AWS S3 Account Server]**

   服务器的URL，应按如下方式填写：

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   要了解在何处找到您的AWS访问密钥ID，请参阅本 [页](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) 。

* **[!UICONTROL Secret access key to AWS]**

   要了解在何处找到AWS的秘密访问密钥，请参阅本 [页](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)。

* **[!UICONTROL AWS Region]**

   要了解有关AWS区域的更多信息，请参阅本 [页](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)。

* 此复 **[!UICONTROL Use server side encryption]** 选框允许您以S3加密模式存储文件。

要了解在何处查找访问密钥ID和秘密访问密钥，请参阅Amazon Web服务 [文档](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) 。

## Azure外部帐户 {#azure-external-account}

该 **[!UICONTROL Azure]** 外部帐户启用到共享外部数据库的连接，只要此连接处于活动状态，就可以通过Adobe Campaign访问数据库。

![](assets/ext_account_15.png)

* **[!UICONTROL Server]**

   Azure服务器的URL。

* **[!UICONTROL Encryption]**

   在或之间选择的加 **[!UICONTROL None]** 密的类 **[!UICONTROL SSL]**&#x200B;型。

* **[!UICONTROL Access key]**

   要了解在何处找到您的访问密钥，请参阅此 [页](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-manage) (部分 **视图和复制访问密钥**)。

## Hadoop外部帐户 {#hadoop-external-account}

该 **[!UICONTROL Hadoop]** 外部帐户启用到共享外部数据库的连接，只要此连接处于活动状态，就可以通过Adobe Campaign访问数据库。 有关如何配置对Hadoop的访问的详细信息，请参阅此 [部分](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop)。

![](assets/ext_account_16.png)

* **[!UICONTROL Server]**

   Hadoop服务器的URL。

* **[!UICONTROL User account name]**

   用于访问Hadoop的帐户的名称。

## Microsoft Dynamics CRM外部帐户 {#microsoft-dynamics-crm-external-account}

该 **[!UICONTROL Microsoft Dynamics CRM]** 外部帐户允许您将Microsoft Dynamics数据导入并导出到Adobe Campaign。

Microsoft Dynamics连接器的Adobe Campaign配置取决于您的部署类型。
对于 **[!UICONTROL On-premise]** 和 **[!UICONTROL Office 365]** 部署类型，您需要提供以下详细信息：

![](assets/ext_account_21.png)

* **[!UICONTROL Account]**

   用于登录Microsoft CRM的帐户。

* **[!UICONTROL Server]**

   Microsoft CRM服务器的URL。

* **[!UICONTROL Password]**

   用于登录Microsoft CRM的口令。

* **[!UICONTROL Company name]** 用于内部部署和Office 365部署

   公司的名称。

* **[!UICONTROL Organization name]** 用于内部部署

   您的组织的名称。
组织名称，可在Microsoft Dynamics的“开发人员资源”仪表板中找到该 **[!UICONTROL Unique Name]** 名称。

* **[!UICONTROL CRM version]** 适用于内部部署

   或之间的CRM **[!UICONTROL Dynamics CRM 2007]**&#x200B;版 **[!UICONTROL Dynamics CRM 2015]** 本 **[!UICONTROL Dynamics CRM 2016]**。

在部 **[!UICONTROL Web API]** 署类型和 **[!UICONTROL Password credentials]** 身份验证方面，您需要提供以下详细信息：

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   用于登录Microsoft CRM的帐户。

* **[!UICONTROL Server]**

   Microsoft CRM服务器的URL。

* **[!UICONTROL Client identifier]**

   客户端ID，可从Microsoft Azure管理门户的“类别”字 **[!UICONTROL Update your code]** 段中找 **[!UICONTROL Client ID]** 到。

* **[!UICONTROL CRM version]**

   或之间的CRM **[!UICONTROL Dynamics CRM 2007]**&#x200B;版 **[!UICONTROL Dynamics CRM 2015]** 本 **[!UICONTROL Dynamics CRM 2016]**。

在部 **[!UICONTROL Web API]** 署类型和 **[!UICONTROL Certificate]** 身份验证方面，您需要提供以下详细信息：

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   Microsoft CRM服务器的URL。

* **[!UICONTROL Private Key (Base64 encoded)]**

   已编码为Base64的私钥

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   客户端ID，可从Microsoft Azure管理门户的“类别”字 **[!UICONTROL Update your code]** 段中找 **[!UICONTROL Client ID]** 到。

* **[!UICONTROL CRM version]**

   或之间的CRM **[!UICONTROL Dynamics CRM 2007]**&#x200B;版 **[!UICONTROL Dynamics CRM 2015]** 本 **[!UICONTROL Dynamics CRM 2016]**。

For more information on this configuration, refer to this [page](../../platform/using/crm-connectors.md#example-for-microsoft-dynamics).

## Oracle按需外部帐户 {#oracle-on-demand-external-account}

该 **[!UICONTROL Oracle on demand]** 外部帐户允许您将Oracle数据导入并导出到Adobe Campaign。

![](assets/ext_account_18.png)

要将Oracle按需外部帐户配置为与Adobe Campaign结合使用，您需要提供以下详细信息：

* **[!UICONTROL Account]**

   用于登录Oracle CRM点播的帐户。

* **[!UICONTROL Server]**

   Oracle CRM on demand服务器的URL。

* **[!UICONTROL Password]**

   用于登录Oracle CRM on demand的口令。

For more information on this configuration, refer to this [page](../../platform/using/crm-connectors.md#example-for-oracle-on-demand).

## Salesforce CRM外部帐户 {#salesforce-crm-external-account}

该 **[!UICONTROL Salesforce CRM]** 外部帐户允许您将Salesforce数据导入并导出到Adobe Campaign。

![](assets/ext_account_17.png)

要配置Salesforce CRM外部帐户以与Adobe Campaign配合使用，您需要提供以下详细信息：

* **[!UICONTROL Account]**

   用于登录Salesforce CRM的帐户。

* **[!UICONTROL Password]**

   用于登录Salesforce CRM的口令。

* **[!UICONTROL Client identifier]**

   要了解在何处查找客户端标识符，请参阅此 [页](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

* **[!UICONTROL Security token]**

   要了解在何处找到您的安全令牌，请参阅此 [页](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

* **[!UICONTROL API version]**

   或之间的API **[!UICONTROL Version 37]**&#x200B;的 **[!UICONTROL Version 21]** 版本 **[!UICONTROL Version 15]**。

对于此外部帐户，您需要使用配置向导配置Salesforce CRM。

For more information on this configuration, refer to this [page](../../platform/using/crm-connectors.md#example-for-salesforce-com).
