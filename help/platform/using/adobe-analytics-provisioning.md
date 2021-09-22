---
solution: Campaign Classic
product: campaign
title: Adobe Analytics Connector
description: 了解有关 Adobe Analytics Connector 的更多信息 设置
feature: Overview
role: User, Admin
level: Beginner
source-git-commit: 5f596c14639e085edab9c08c2e3abba36e76acd3
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 4%

---

# Adobe Analytics Connector配置 {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> 这些步骤只应由混合实施和内部部署实施执行。
>
>对于托管的实施，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)团队。

Adobe Campaign Classic与Adobe Analytics身份验证之间的集成支持AdobeIdentity Management服务(IMS)。 您必须实施Adobe IMS，并通过Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=en)连接到Campaign [，然后才能开始实施Analytics连接器。

要使此集成正常工作，您必须创建专门用于Analytics连接器的Adobe Analytics产品配置文件。 然后，您将需要创建一个Adobe I/O项目。

## 创建Adobe Analytics产品配置文件 {#analytics-product-profile}

产品配置文件可确定用户对您的不同Analytics组件具有的访问级别。

如果您已经拥有Analytics产品配置文件，则仍应该创建一个专门用于Analytics连接器的新Adobe Analytics产品配置文件。 这将确保您的产品配置文件已设置为具有此集成的正确权限。

有关产品配置文件的更多信息，请参阅[Admin Console文档](https://helpx.adobe.com/mt/enterprise/admin-guide.html)。

1. 从[管理控制台](https://adminconsole.adobe.com/)中，选择您的Adobe Analytics **[!UICONTROL Product]**。

   ![](assets/do-not-localize/triggers_1.png)

1. 单击 **[!UICONTROL New Profile]**。

   ![](assets/do-not-localize/triggers_2.png)

1. 添加&#x200B;**[!UICONTROL Product profile name]**，我们建议使用以下语法：`reserved_campaign_classic_<Company Name>`。 然后，单击&#x200B;**[!UICONTROL Next]**。

   此&#x200B;**[!UICONTROL Product profile]**&#x200B;应专门用于Analytics连接器，以防止出现配置错误。

1. 打开新创建的&#x200B;**[!UICONTROL Product profile]** ，然后选择&#x200B;**[!UICONTROL Permissions]**&#x200B;选项卡。

   ![](assets/do-not-localize/triggers_3.png)

1. 单击&#x200B;**[!UICONTROL Edit]**&#x200B;配置不同的功能，然后单击加号(+)图标以选择要分配给&#x200B;**[!UICONTROL Product profile]**&#x200B;的权限。

   有关如何管理权限的更多信息，请参阅[Admin Console文档](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html)。

1. 对于&#x200B;**[!UICONTROL Report Suites]**&#x200B;功能，添加您以后需要使用的&#x200B;**[!UICONTROL Report Suites]**。

   如果您没有任何报表包，则可以按照[这些步骤](../../platform/using/adobe-analytics-connector.md#report-suite-analytics)创建报表包。

   ![](assets/do-not-localize/triggers_4.png)

1. 对于&#x200B;**[!UICONTROL Metrics]**&#x200B;功能，添加以后需要配置的&#x200B;**[!UICONTROL Metrics]**。

   如果需要，您可以打开自动包含选项，该选项会将每个权限项添加到包含的列表中，并自动添加新权限项。

   ![](assets/do-not-localize/triggers_13.png)

1. 对于&#x200B;**[!UICONTROL Dimensions]**&#x200B;功能，添加以后需要配置的&#x200B;**[!UICONTROL Dimensions]**。

1. 对于&#x200B;**[!UICONTROL Report Suite Tools]**&#x200B;功能，添加以下权限：

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. 对于&#x200B;**[!UICONTROL Analytics Tools]**&#x200B;功能，添加以下权限：

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

您的产品配置文件现已配置完成。 然后，您需要创建Adobe I/O项目。

## 创建Adobe I/O项目 {#create-adobe-io}

1. 访问Adobe I/O并以IMS组织的&#x200B;**系统管理员**&#x200B;的身份登录。

   有关管理员角色的更多信息，请参阅此[页面](https://helpx.adobe.com/enterprise/using/admin-roles.html)。

1. 单击 **[!UICONTROL Create a new project]**。

   ![](assets/do-not-localize/triggers_5.png)

1. 单击&#x200B;**[!UICONTROL Add to Project]**&#x200B;并选择&#x200B;**[!UICONTROL API]**。

   ![](assets/do-not-localize/triggers_6.png)

1. 选择 [!DNL Adobe Analytics] 并单击 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_7.png)

1. 选择&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;作为身份验证类型，然后单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_8.png)

1. 选择&#x200B;**[!UICONTROL Option 1: Generate a Key-Pair]**&#x200B;选项并单击&#x200B;**[!UICONTROL Generate a Key-Pair]**。

   随后将自动下载config.zip文件。

   ![](assets/do-not-localize/triggers_9.png)

1. 单击 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_10.png)

1. 选择在此[部分](#analytics-product-profile)中详细描述的上一步骤中创建的&#x200B;**[!UICONTROL Product profile]**。

1. 然后，单击&#x200B;**[!UICONTROL Save Configured API]**。

   ![](assets/do-not-localize/triggers_11.png)

1. 在您的项目中，选择[!DNL Adobe Analytics]并复制&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;下的以下信息：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. 使用以下命令将这些服务帐户凭据粘贴到nlserver:

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

您现在可以开始使用Analytics连接器并跟踪客户行为。
