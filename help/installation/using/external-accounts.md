---
solution: Campaign Classic
product: campaign
title: 外部帐户
description: 了解如何创建外部帐户
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '1543'
ht-degree: 8%

---

# 外部帐户{#external-accounts}

Adobe Campaign 提供了一组预定义的外部帐户。要设置与外部系统的连接，您可以创建新外部帐户。

技术工作流或营销策划工作流等技术流程，会使用外部帐户。例如，在工作流中设置文件传输或与任何其他应用程序(Adobe Target、Experience Manager等)进行数据交换时，您需要选择外部帐户。

## 创建外部帐户{#creating-an-external-account}

要创建新外部帐户，请执行以下步骤。 详细设置取决于外部帐户类型。

1. 从活动&#x200B;**[!UICONTROL Explorer]**&#x200B;中，选择&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

   ![](assets/ext_account_1.png)

1. 单击 **[!UICONTROL New]** 按钮。

   ![](assets/ext_account_2.png)

1. 输入&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal Name]**。
1. 选择要创建的外部帐户&#x200B;**[!UICONTROL Type]**。
1. 根据所选外部帐户类型指定凭据，配置对帐户的访问。

   所连接服务器的提供者通常会提供必需的信息。

1. 选中&#x200B;**[!UICONTROL Enabled]**&#x200B;选项以激活连接。
1. 单击 **[!UICONTROL Save]**.

将创建外部帐户并将其添加到外部帐户列表。

## 活动特定外部帐户

### 退回邮件{#bounce-mails-external-account}

**弹回邮件**&#x200B;外部帐户指定用于连接到电子邮件服务的外部POP3帐户。 有关此外部帐户的详细信息，请参阅此[页面](../../workflow/using/inbound-emails.md)。

为POP3访问配置的所有服务器都可用于接收返回邮件。

![](assets/ext_account_6.png)

配置&#x200B;**[!UICONTROL Bounce mails (defaultPopAccount)]**&#x200B;外部帐户:

* **[!UICONTROL Server]**

   POP3服务器的URL。

* **[!UICONTROL Port]**

   POP3连接端口号。 默认端口为110。

* **[!UICONTROL Account]**

   用户的名称。

* **[!UICONTROL Password]**

   用户帐户密码。

* **[!UICONTROL Encryption]**

   在&#x200B;**[!UICONTROL By default]**、**[!UICONTROL POP3 + STARTTLS]**、**[!UICONTROL POP3]**&#x200B;或&#x200B;**[!UICONTROL POP3S]**&#x200B;之间选择的加密的类型。

### 路由{#routing-external-account}

**[!UICONTROL Routing]**&#x200B;外部帐户允许您根据所安装的包配置Adobe Campaign中可用的每个渠道。

![](assets/ext_account_7.png)

可以配置以下渠道:

* [电子邮件](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [手机（短信）](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [电话](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [直邮](../../delivery/using/about-direct-mail-channel.md)
* [代理](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS渠道](../../delivery/using/configuring-the-mobile-application.md)
* [Android渠道](../../delivery/using/configuring-the-mobile-application-android.md)


### 执行实例{#execution-instance-external-account}

如果您有一个分解的架构，您需要指定链接到该控制实例的执行实例并连接它们。 事务性消息模板部署到执行实例

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   安装执行实例的服务器的URL。

* **[!UICONTROL Account]**

   帐户名称必须与在运算符文件夹中定义的消息中心代理匹配。

* **[!UICONTROL Password]**

   操作符文件夹中定义的帐户密码。

有关此配置的详细信息，请参阅此[页面](../../message-center/using/creating-a-shared-connection.md#control-instance)。


## 访问外部系统外部帐户

### FTP {#ftp-external-account}

FTP外部帐户允许您配置和测试对Adobe Campaign之外的服务器的访问。 要与外部系统（如用于文件传输的FTP服务器898）建立连接，您可以创建自己的外部帐户。 有关详细信息，请参见此 [ 页面](../../workflow/using/file-transfer.md)。

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

   在&#x200B;**[!UICONTROL None]**&#x200B;或&#x200B;**[!UICONTROL SSL]**&#x200B;之间选择的加密的类型。

要了解这些凭据的位置，请参阅此[页面](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials)。

### SFTP {#sftp-external-account}

SFTP外部帐户允许您配置和测试对Adobe Campaign之外的服务器的访问。 要设置与外部系统（如用于文件传输的SFTP）的连接，您可以创建自己的外部帐户。 有关详细信息，请参见此 [ 页面](../../workflow/using/file-transfer.md)。

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   SFTP服务器的URL。

* **[!UICONTROL Port]**

   FTP连接端口号。 默认端口为22。

* **[!UICONTROL Account]**

   用于连接到SFTP服务器的帐户名。

* **[!UICONTROL Password]**

   用于连接到SFTP服务器的口令。

### 外部数据库(联合数据访问){#external-database-external-account}

使用&#x200B;**外部数据库**&#x200B;类型外部帐户连接到外部数据库。 了解有关[本节](../../installation/using/about-fda.md)中的联合数据访问(联合数据访问)选项的更多信息。

[兼容性矩阵](../../rn/using/compatibility-matrix.md)中列出了与活动兼容的外部数据库

![](assets/ext_account_11.png)

外部帐户配置设置取决于数据库引擎。 请通过以下部分了解更多信息：

* 配置对[Azure synapse](../../installation/using/configure-fda-synapse.md)的访问
* 配置对[Hadoop](../../installation/using/configure-fda-hadoop.md)的访问
* 配置对[Oracle](../../installation/using/configure-fda-oracle.md)的访问
* 配置对[Netezza](../../installation/using/configure-fda-netezza.md)的访问
* 配置对[SAP HANA](../../installation/using/configure-fda-sap-hana.md)的访问
* 配置对[Snowflake](../../installation/using/configure-fda-snowflake.md)的访问
* 配置对[Sybase IQ](../../installation/using/configure-fda-sybase.md)的访问
* 配置对[Teradata](../../installation/using/configure-fda-teradata.md)的访问

### Facebook connect {#facebook-connect-external-account}

**[!UICONTROL Facebook Connect]**&#x200B;外部帐户允许您在Facebook应用程序中显示个性化内容，从而更轻松地通过此社交网络获取潜在客户。

对于每个Facebook应用程序，您需要创建&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;类型外部帐户。 有关详细信息，请参阅[页面](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   在&#x200B;**[!UICONTROL hosted by a partner]**&#x200B;或&#x200B;**[!UICONTROL hosted by this instance]**&#x200B;之间托管应用程序的模式。

* **[!UICONTROL Application ID]**

   您的Facebook应用程序的应用程序ID。

* **[!UICONTROL Application secret]**

   您的Facebook应用程序的应用程序机密。

如果选择了由此实例模式托管的Canvas URL，则需要将“安全”粘贴到Facebook上的&#x200B;**Facebook Web Games(https)**&#x200B;字段

要了解这些凭据的位置，请参阅此[页面](https://developers.facebook.com/docs/facebook-login/access-tokens)。

## Adobe解决方案集成外部帐户

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

要使用Adobe ID连接到Adobe Campaign控制台，必须配置&#x200B;**[!UICONTROL Adobe Experience Cloud (MAC)]**&#x200B;外部帐户。

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

   您的IMS组织的ID。 要查找您的组织ID，请参阅此[页](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html)（**在哪里可以找到我的IMS组织ID?**）。

* **[!UICONTROL Association mask]**

   允许Enterprise仪表板中的配置名称与Adobe Campaign中的组同步的语法。

* **[!UICONTROL Server]**

   Adobe Experience Cloud实例的URL。

* **[!UICONTROL Tenant]**

   您的Adobe Experience Cloud租户的名称。

有关此配置的详细信息，请参阅此[页面](../../integrations/using/configuring-ims.md)。

## 网络分析 {#web-analytics-external-account}

**[!UICONTROL Web Analytics (Adobe Analytics - Data connector)]**&#x200B;外部帐户允许您以区段形式将数据从Adobe Analytics转发到Adobe Campaign。 相反，它会通过Adobe Campaign将电子邮件活动的指示符和属性发送到Adobe Analytics — 数据连接器。

![](assets/ext_account_10.png)

对于此外部帐户，必须丰富跟踪URL的计算公式，并批准两个解决方案之间的连接。 有关详细信息，请参见此 [ 页面](../../platform/using/adobe-analytics-data-connector.md#step-2--create-the-external-account-in-campaign)。

### Adobe Experience Manager {#adobe-experience-manager-external-account}

**[!UICONTROL AEM (AEM instance)]**&#x200B;外部帐户允许您直接在Adobe Experience Manager中管理电子邮件投放以及表单的内容。

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   Adobe Experience Manager服务器的URL。

* **[!UICONTROL Port]**

   用于连接到Adobe Experience Manager创作实例的帐户名。

* **[!UICONTROL Password]**

   用于连接到Adobe Experience Manager创作实例的口令。

有关更多信息，请参阅此](../../integrations/using/about-adobe-experience-manager.md)章节[。



## CRM连接器外部帐户

### Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

**[!UICONTROL Microsoft Dynamics CRM]**&#x200B;外部帐户允许您将Microsoft Dynamics数据导入并导出到Adobe Campaign。

了解有关活动的更多信息 — 此[页面](../../platform/using/crm-ms-dynamics.md)中的Microsoft Dynamics CRM连接器。

>[!NOTE]
>
> **[!UICONTROL On-premise]** 和部 **[!UICONTROL Office 365]** 署类型现已弃用。[了解详情](../../rn/using/deprecated-features.md)。

对于&#x200B;**[!UICONTROL Web API]**&#x200B;部署类型和&#x200B;**[!UICONTROL Password credentials]**&#x200B;身份验证，您需要提供以下详细信息：

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   用于登录Microsoft CRM的帐户。

* **[!UICONTROL Server]**

   Microsoft CRM服务器的URL。

* **[!UICONTROL Client identifier]**

   可从&#x200B;**[!UICONTROL Update your code]**&#x200B;类别&#x200B;**[!UICONTROL Client ID]**&#x200B;字段的Microsoft Azure管理门户中找到的客户端ID。

* **[!UICONTROL CRM version]**

   **[!UICONTROL Dynamics CRM 2007]**、**[!UICONTROL Dynamics CRM 2015]**&#x200B;或&#x200B;**[!UICONTROL Dynamics CRM 2016]**&#x200B;之间的CRM版本。

对于&#x200B;**[!UICONTROL Web API]**&#x200B;部署类型和&#x200B;**[!UICONTROL Certificate]**&#x200B;身份验证，您需要提供以下详细信息：

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   Microsoft CRM服务器的URL。

* **[!UICONTROL Private Key (Base64 encoded)]**

   已编码到Base64的私钥

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   可从&#x200B;**[!UICONTROL Update your code]**&#x200B;类别&#x200B;**[!UICONTROL Client ID]**&#x200B;字段的Microsoft Azure管理门户中找到的客户端ID。

* **[!UICONTROL CRM version]**

   **[!UICONTROL Dynamics CRM 2007]**、**[!UICONTROL Dynamics CRM 2015]**&#x200B;或&#x200B;**[!UICONTROL Dynamics CRM 2016]**&#x200B;之间的CRM版本。

有关此配置的详细信息，请参阅此[页面](../../platform/using/crm-connectors.md)。

### Salesforce.com CRM {#salesforce-crm-external-account}

**[!UICONTROL Salesforce CRM]**&#x200B;外部帐户允许您将Salesforce数据导入并导出到Adobe Campaign。

![](assets/ext_account_17.png)

要配置Salesforce CRM外部帐户以与Adobe Campaign一起使用，您需要提供以下详细信息：

* **[!UICONTROL Account]**

   用于登录Salesforce CRM的帐户。

* **[!UICONTROL Password]**

   用于登录Salesforce CRM的密码。

* **[!UICONTROL Client identifier]**

   要了解在何处查找客户端标识符，请参阅此[页面](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

* **[!UICONTROL Security token]**

   要了解在何处查找安全令牌，请参阅此[页面](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

* **[!UICONTROL API version]**

   选择API的版本。

对于此外部帐户，您需要使用配置向导配置Salesforce CRM。

有关此配置的详细信息，请参阅此[页面](../../platform/using/crm-connectors.md)。

## 传输数据外部帐户

### Amazon Simple 存储 Service(S3){#amazon-simple-storage-service--s3--external-account}

Amazon Simple 存储 Service(S3)连接器可用于将数据导入或导出到Adobe Campaign。 可以在工作流活动中设置。 有关详细信息，请参见此 [ 页面](../../workflow/using/file-transfer.md)。

![](assets/ext_account_3.png)

在设置此新外部帐户时，您需要提供以下详细信息：

* **[!UICONTROL AWS S3 Account Server]**

   服务器的URL，应按如下方式填写：

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   要了解在何处找到您的AWS访问密钥ID，请参阅此[页面](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)。

* **[!UICONTROL Secret access key to AWS]**

   要了解在何处查找您的AWS秘密访问密钥，请参阅此[页面](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)。

* **[!UICONTROL AWS Region]**

   要了解有关AWS区域的更多信息，请参阅此[页面](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)。

* **[!UICONTROL Use server side encryption]**&#x200B;复选框允许您以S3加密模式存储文件。

要了解在何处查找访问密钥ID和秘密访问密钥，请参阅Amazon Web服务[文档](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)。

### Azure Blob存储(#azure-blob-external-account)

**Azure Blob存储**&#x200B;外部帐户可用于使用&#x200B;**[!UICONTROL Transfer file]**&#x200B;工作流活动将数据导入或导出到Adobe Campaign。 有关更多信息，请参阅此](../../workflow/using/file-transfer.md)章节[。

![](assets/ext_account_23.png)

要配置&#x200B;**[!UICONTROL Azure external account]**&#x200B;以使用Adobe Campaign，您需要提供以下详细信息：

* **[!UICONTROL Server]**

   您的Azure Blob存储服务器的URL。

* **[!UICONTROL Encryption]**

   在&#x200B;**[!UICONTROL None]**&#x200B;或&#x200B;**[!UICONTROL SSL]**&#x200B;之间选择的加密的类型。

* **[!UICONTROL Access key]**

   要了解在何处找到您的&#x200B;**[!UICONTROL Access key]**，请参阅此[页面](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal)。
