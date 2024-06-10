---
product: campaign
title: 外部帐户
description: 了解如何创建外部帐户
feature: Installation, Application Settings, External Account
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: ef6a864c76c04ac94383c1c2ad74095dd5ef63a1
workflow-type: tm+mt
source-wordcount: '1757'
ht-degree: 8%

---

# 外部帐户{#external-accounts}

Adobe Campaign 提供了一组预定义的外部帐户。要设置与外部系统的连接，您可以创建新的外部帐户。

技术工作流或营销策划工作流等技术流程，会使用外部帐户。例如，在工作流中设置文件传输或与任何其他应用程序(Adobe Target、Experience Manager等)进行数据交换时，您需要选择外部帐户。

## 创建外部帐户 {#creating-an-external-account}

要创建新的外部帐户，请执行以下步骤。 详细设置取决于外部帐户的类型。

1. 来自营销活动 **[!UICONTROL Explorer]**，选择 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. 单击 **[!UICONTROL New]** 按钮。

   ![](assets/ext_account_2.png)

1. 输入 **[!UICONTROL Label]** 和 **[!UICONTROL Internal Name]**.
1. 选择外部帐户 **[!UICONTROL Type]** 您要创建哪个。
1. 根据所选外部帐户类型指定凭据，以配置对帐户的访问权限。

   所连接服务器的提供者通常会提供必需的信息。

1. 查看 **[!UICONTROL Enabled]** 用于激活连接的选项。
1. 单击 **[!UICONTROL Save]**。

外部帐户已创建并添加到外部帐户列表。

## 特定于Campaign的外部帐户

### 退回邮件 {#bounce-mails-external-account}

此 **退回邮件** 外部帐户指定要用于连接到电子邮件服务的外部POP3帐户。 有关此外部帐户的更多信息，请参阅此 [页面](../../workflow/using/inbound-emails.md).

所有配置为POP3访问的服务器都可以接收回邮。

![](assets/ext_account_6.png)

配置 **[!UICONTROL Bounce mails (defaultPopAccount)]** 外部帐户：

* **[!UICONTROL Server]**

  pop3服务器的URL。

* **[!UICONTROL Port]**

  POP3连接端口号。 默认端口为110。

* **[!UICONTROL Account]**

  用户的名称。

* **[!UICONTROL Password]**

  用户帐户密码。

* **[!UICONTROL Encryption]**

  选择的加密类型，介于 **[!UICONTROL By default]**， **[!UICONTROL POP3 + STARTTLS]**， **[!UICONTROL POP3]** 或 **[!UICONTROL POP3S]**.

* **[!UICONTROL Function]**

  入站电子邮件或SOAP路由器

>[!IMPORTANT]
>
>在使用Microsoft OAuth 2.0配置POP3外部帐户之前，您首先需要在Azure门户中注册应用程序。 有关详细信息，请参见[此页面](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app)。

要使用配置POP3外部 **Microsoft OAuth 2.0**，查看 **[!UICONTROL Microsoft OAuth 2.0]** 并填写以下字段：

* **[!UICONTROL Azure tenant]**

  可在以下位置找到Azure ID(或目录（租户）ID)： **Essentials** Azure门户中应用程序概述的下拉列表。

* **[!UICONTROL Azure Client ID]**

  客户端ID(或应用程序（客户端）ID)可在 **Essentials** Azure门户中应用程序概述的下拉列表。

* **[!UICONTROL Azure Client secret]**

  客户端密码ID可在 **客户端密钥** 中的列 **证书和密钥** Azure门户中应用程序的菜单。

* **[!UICONTROL Azure Redirect URL]**

  可在以下位置找到重定向URL： **身份验证** Azure门户中应用程序的菜单。 它应以下列语法结束 `nl/jsp/oauth.jsp`，例如 `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

输入其他凭据后，您可以单击 **[!UICONTROL Setup the connection]** 以完成外部帐户配置。

### 路由{#routing-external-account}

此 **[!UICONTROL Routing]** 外部帐户允许您根据安装的包配置Adobe Campaign中可用的每个渠道。

![](assets/ext_account_7.png)

可以配置以下渠道：

* [电子邮件](#email-routing-external-account)
* [手机（短信）](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [电话](../../delivery/using/communication-channels.md#other-channels)
* [直邮](../../delivery/using/about-direct-mail-channel.md)
* [代理](../../delivery/using/communication-channels.md#other-channels)
* [X(以前称为Twitter)](../../social/using/about-social-marketing.md)
* [iOS 渠道](../../delivery/using/configuring-the-mobile-application.md)
* [Android 渠道](../../delivery/using/configuring-the-mobile-application-android.md)

### 电子邮件路由 {#email-routing-external-account}

默认情况下，会根据您的配置提供电子邮件路由外部帐户。

作为内部部署/混合部署客户，您可以创建新的路由外部帐户或更新参数，如下所述。 此配置仅供专家用户使用，可能会影响您的可投放性。 如有任何问题，请联系Adobe客户关怀团队或您的Adobe代表。

* 您可以使用 **中间源**， **外部** 路由，或 **批量** 投放路由类型。

* 对象 **批量** 和 **中间源** 投放模式，您可以在 **品牌化** 选项卡。 这些参数用于覆盖 [默认参数](../../installation/using/deploying-an-instance.md#email-channel-parameters) 对象 **镜像页面URL** 和 **错误地址** 具有特定于您品牌的设置。

  ![](assets/ext-account-branding.png)

* 要配置中间源外部帐户，请参阅 [本节](mid-sourcing-server.md)

### 执行实例  {#execution-instance-external-account}

如果您具有分解的体系结构，则需要指定链接到控制实例的执行实例并将它们连接起来。 将事务性消息模板部署到执行实例。

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

  安装执行实例的服务器的URL。

* **[!UICONTROL Account]**

  帐户的名称，它必须与操作员文件夹中定义的消息中心代理匹配。

* **[!UICONTROL Password]**

  运算符文件夹中定义的帐户密码。

有关此配置的更多信息，请参阅此 [页面](../../message-center/using/configuring-instances.md#control-instance).

## 访问外部系统外部帐户

### FTP {#ftp-external-account}

FTP外部帐户允许您配置和测试对Adobe Campaign外部服务器的访问。 要与外部系统（如用于文件传输的FTP服务器898）建立连接，您可以创建自己的外部帐户。 有关详细信息，请参见此 [ 页面](../../workflow/using/file-transfer.md)。

为此，请在此外部帐户中指定用于建立与FTP服务器连接的地址和凭据

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

  ftp服务器的名称。

* **[!UICONTROL Port]**

  FTP连接端口号。 默认端口为21。

* **[!UICONTROL Account]**

  用户的名称。

* **[!UICONTROL Password]**

  用户帐户密码。

* **[!UICONTROL Encryption]**

  选择的加密类型，介于 **[!UICONTROL None]** 或 **[!UICONTROL SSL]**.

要了解在何处查找这些凭据，请参阅此 [页面](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

SFTP外部帐户允许您配置和测试对Adobe Campaign外部服务器的访问。 要与外部系统（如用于文件传输的SFTP）建立连接，您可以创建自己的外部帐户。 有关详细信息，请参见此 [ 页面](../../workflow/using/file-transfer.md)。

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

  SFTP服务器的URL。

* **[!UICONTROL Port]**

  FTP连接端口号。 默认端口为22。

* **[!UICONTROL Account]**

  用于连接到SFTP服务器的帐户名称。

* **[!UICONTROL Password]**

  用于连接到SFTP服务器的密码。

<!--To add SSH keys on Windows:

1. Create the **HOME** environment variable with value set as the installation directory.

2. Add your private key to the `/$HOME/.ssh/id_rsa` folder.

3. Restart the Adobe Campaign services.
-->

### 外部数据库（联合数据访问） {#external-database-external-account}

使用 **外部数据库** 键入外部帐户以连接到外部数据库。 要了解有关联合数据访问(FDA)选项的更多信息，请参阅 [本节](../../installation/using/about-fda.md).

与Campaign兼容的外部数据库列在 [兼容性矩阵](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

外部帐户配置设置取决于数据库引擎。 请在以下部分中了解详情：

* 配置对的访问权限 [vertica analytics](../../installation/using/configure-fda-vertica.md)
* 配置对的访问权限 [Snowflake](../../installation/using/configure-fda-snowflake.md)
* 配置对的访问权限 [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* 配置对的访问权限 [azure synapse](../../installation/using/configure-fda-synapse.md)
* 配置对的访问权限 [hadoop](../../installation/using/configure-fda-hadoop.md)
* 配置对的访问权限 [oracle](../../installation/using/configure-fda-oracle.md)
* 配置对的访问权限 [netezza](../../installation/using/configure-fda-netezza.md)
* 配置对的访问权限 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* 配置对的访问权限 [Snowflake](../../installation/using/configure-fda-snowflake.md)
* 配置对的访问权限 [sybase IQ](../../installation/using/configure-fda-sybase.md)
* 配置对的访问权限 [teradata](../../installation/using/configure-fda-teradata.md)


## Adobe解决方案集成外部帐户

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

要使用Adobe ID连接到Adobe Campaign控制台，您必须配置 **[!UICONTROL Adobe Experience Cloud (MAC)]** 外部帐户。

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

  IMS服务器的URL。 确保暂存实例和生产实例都指向同一个IMS生产端点。

* **[!UICONTROL IMS scope]**

  此处定义的范围必须是IMS设置的范围的子集。

* **[!UICONTROL IMS client identifier]**

  IMS客户端的ID。

* **[!UICONTROL IMS client secret]**

  IMS客户端密钥的凭据。

* **[!UICONTROL Callback server]**

  访问Adobe Campaign实例的URL。

* **[!UICONTROL IMS organization ID]**

  您组织的ID。 要查找您的组织ID，请参阅 [此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans){_blank}.

* **[!UICONTROL Association mask]**

  语法允许Enterprise Dashboard中的配置名称与Adobe Campaign中的组同步。

* **[!UICONTROL Server]**

  Adobe Experience Cloud实例的URL。

* **[!UICONTROL Tenant]**

  您的Adobe Experience Cloud租户的名称。

有关此配置的更多信息，请参阅 [此页面](../../integrations/using/configuring-ims.md).

## Web 分析 {#web-analytics-external-account}

此 **[!UICONTROL Web Analytics]** 外部帐户允许您以区段形式将数据从Adobe Analytics转发到Adobe Campaign。 反过来，它会将Adobe Campaign投放的电子邮件营销活动的指标和属性发送到Adobe Analytics连接器。

![](assets/ext_account_10.png)

对于此外部帐户，必须扩充跟踪URL的计算公式，并且必须批准两个解决方案之间的连接。 有关详细信息，请参见此 [ 页面](../../platform/using/gs-aa.md)。

### Adobe Experience Manager {#adobe-experience-manager-external-account}

此 **[!UICONTROL AEM (AEM instance)]** 外部帐户允许您直接在Adobe Experience Manager中管理电子邮件投放和表单的内容。

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

  Adobe Experience Manager服务器的URL。

* **[!UICONTROL Port]**

  用于连接到Adobe Experience Manager创作实例的帐户名称。

* **[!UICONTROL Password]**

  用于连接到Adobe Experience Manager创作实例的密码。

有关更多信息，请参阅此](../../integrations/using/about-adobe-experience-manager.md)章节[。

## CRM连接器外部帐户

### Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> **[!UICONTROL On-premise]** 和 **[!UICONTROL Office 365]** 部署类型现已弃用。 [了解详情](../../rn/using/deprecated-features.md)。

此 **[!UICONTROL Microsoft Dynamics CRM]** 外部帐户允许您将Microsoft Dynamics数据导入和导出到Adobe Campaign。

请在此了解有关Campaign - Microsoft Dynamics CRM连接器的更多信息 [页面](../../platform/using/crm-ms-dynamics.md).

替换为 **[!UICONTROL Web API]** 部署类型和 **[!UICONTROL Password credentials]** 身份验证，您需要提供以下详细信息：

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

  用于登录到Microsoft CRM的帐户。

* **[!UICONTROL Server]**

  Microsoft CRM服务器的URL。

  查找您的Microsoft CRM **[!UICONTROL Server URL]**，访问您的Microsoft Dynamics CRM帐户，然后单击 **Dynamics 365** 并选择您的应用程序。 然后，您可以找到您的 **[!UICONTROL Server URL]** 在浏览器的地址栏中，例如 `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

  可以在Microsoft Azure管理门户网站中找到的客户端ID **[!UICONTROL Update your code]** 类别， **[!UICONTROL Client ID]** 字段。

* **[!UICONTROL CRM version]**

  选择 **[!UICONTROL Dynamics CRM 365]** crm版本。

替换为 **[!UICONTROL Web API]** 部署类型和 **[!UICONTROL Certificate]** 身份验证，您需要提供以下详细信息：

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

  Microsoft CRM服务器的URL。

  查找您的Microsoft CRM **[!UICONTROL Server URL]**，访问您的Microsoft Dynamics CRM帐户，然后单击 **Dynamics 365** 并选择您的应用程序。 然后，您可以找到您的 **[!UICONTROL Server URL]** 在浏览器的地址栏中，例如 `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Private Key (Base64 encoded)]**

  请注意，私钥需要编码为Base64。

  为此，您可以使用Base64编码器帮助或使用命令行 `base64 -w0 private.key` 用于Linux。

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

  可以在Microsoft Azure管理门户网站中找到的客户端ID **[!UICONTROL Update your code]** 类别， **[!UICONTROL Client ID]** 字段。

* **[!UICONTROL CRM version]**

  CRM的版本，介于 **[!UICONTROL Dynamics CRM 2007]**， **[!UICONTROL Dynamics CRM 2015]** 或 **[!UICONTROL Dynamics CRM 2016]**.

有关此配置的更多信息，请参阅此 [页面](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

此 **[!UICONTROL Salesforce CRM]** 外部帐户允许您将Salesforce数据导入和导出到Adobe Campaign中。

![](assets/ext_account_17.png)

要将Salesforce CRM外部帐户配置为与Adobe Campaign配合使用，您需要提供以下详细信息：

* **[!UICONTROL Account]**

  用于登录Salesforce CRM的帐户。

* **[!UICONTROL Password]**

  用于登录到Salesforce CRM的密码。

* **[!UICONTROL Client identifier]**

  要了解在何处查找您的客户端标识符，请参阅此 [页面](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

  要了解在何处查找您的安全令牌，请参阅此 [页面](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

  选择API的版本。

对于此外部帐户，您需要使用配置向导配置Salesforce CRM。

有关此配置的更多信息，请参阅此 [页面](../../platform/using/crm-connectors.md).

## 传输数据外部帐户

### Amazon Simple Storage Service (S3) {#amazon-simple-storage-service--s3--external-account}

Amazon Simple Storage Service (S3)连接器可用于将数据导入或导出Adobe Campaign。 它可以在工作流活动中设置。 有关详细信息，请参见此 [ 页面](../../workflow/using/file-transfer.md)。

![](assets/ext_account_3.png)

在设置此新外部帐户时，您需要提供以下详细信息：

* **[!UICONTROL AWS S3 Account Server]**

  服务器的URL，应按如下方式填写：

  ```
  <S3bucket name>.s3.amazonaws.com/<s3object path>
  ```

* **[!UICONTROL AWS access key ID]**

  要了解在何处查找您的AWS访问密钥ID，请参阅此 [页面](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Secret access key to AWS]**

  要了解在何处查找AWS的秘密访问密钥，请参阅此 [页面](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

  要了解有关AWS地区的更多信息，请参阅此 [页面](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* 此 **[!UICONTROL Use server side encryption]** 复选框允许您以S3加密模式存储文件。

要了解在何处查找访问密钥ID和访问密钥，请参阅Amazon Web服务 [文档](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Azure Blob Storage {#azure-blob-external-account}

此 **Azure Blob存储** 外部帐户可用于使用以下方式将数据导入或导出到Adobe Campaign **[!UICONTROL Transfer file]** 工作流活动。 有关更多信息，请参阅此](../../workflow/using/file-transfer.md)章节[。

![](assets/ext_account_23.png)

配置 **[!UICONTROL Azure external account]** 要使用Adobe Campaign，您需要提供以下详细信息：

* **[!UICONTROL Server]**

  Azure Blob Storage服务器的URL。

* **[!UICONTROL Encryption]**

  选择的加密类型，介于 **[!UICONTROL None]** 或 **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

  了解在何处查找您的 **[!UICONTROL Access key]**，请参阅此 [页面](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
