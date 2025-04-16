---
product: campaign
title: Adobe Analytics连接器配置
description: 了解有关Adobe Analytics连接器配置的更多信息
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于v7内部部署和混合部署"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 84e6b2fad97f0ca5d6621cff4648e0be0bef7521
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 1%

---

# Adobe Analytics Connector 配置 {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> 这些步骤只能通过混合和内部部署实施来执行。
>
>对于Hosted和Campaign Managed Services实施，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)团队。

Adobe Campaign Classic与Adobe Analytics身份验证之间的集成支持Adobe Identity Management服务(IMS)：

* 如果您正在管理已迁移的外部帐户，则必须实施Adobe IMS并通过Adobe ID连接到Adobe Campaign。

  请注意，通过Adobe ID IMS登录的用户必须是Adobe Analytics中&#x200B;**Data Connector**&#x200B;帐户的所有者，并且拥有以下[提及的&#x200B;**产品配置文件**&#x200B;的权限](#analytics-product-profile)。

问题是Data Connector的所有者不是登录Campaign并尝试与Analytics集成的用户。

* 如果您正在实施新连接器，实施Adobe IMS是可选的。 如果没有Adobe ID用户，Adobe Campaign将使用技术用户与Adobe Analytics同步。

为使这种集成正常工作，您必须创建专门用于Analytics连接器的Adobe Analytics产品配置文件。 然后，您需要创建一个开发人员控制台项目。

>[!AVAILABILITY]
>
> Adobe已弃用服务帐户(JWT)凭据，Campaign与Adobe解决方案和应用程序的集成现在必须依赖OAuth服务器到服务器凭据。 </br>
>
> * 如果您已实施与Campaign的入站集成，则必须迁移技术帐户，如[本文档](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank)中所述。 现有[服务帐户(JWT)凭据](oauth-technical-account.md)将继续工作直至2025年6月30日。</br>
>
> * 如果您实施了叫客集成，如Campaign-Analytics集成或Experience Cloud Triggers集成，则在2025年6月30日之前它们将继续工作。 但是，在该日期之前，您必须将Campaign环境升级到v7.4.1，并将您的技术帐户迁移到OAuth。

## 创建Adobe Analytics产品配置文件 {#analytics-product-profile}

产品配置文件确定用户对其他Analytics组件的访问级别。

如果您已有Analytics产品配置文件，则仍应创建一个新的Adobe Analytics产品配置文件，专门用于Analytics连接器。 这将确保为您的产品配置文件设置此集成的正确权限。

有关产品配置文件的详细信息，请参阅[管理控制台文档](https://helpx.adobe.com/mt/enterprise/admin-guide.html)。

1. 从[Admin Console](https://adminconsole.adobe.com/)中，选择您的Adobe Analytics **[!UICONTROL Product]**。

   ![](assets/do-not-localize/triggers_1.png)

1. 单击 **[!UICONTROL New Profile]**。

   ![](assets/do-not-localize/triggers_2.png)

1. 添加&#x200B;**[!UICONTROL Product profile name]**，我们建议使用以下语法： `reserved_campaign_classic_<Company Name>`。 然后，单击&#x200B;**[!UICONTROL Next]**。

   此&#x200B;**[!UICONTROL Product profile]**&#x200B;应专门用于Analytics Connector，以防止配置错误。

1. 打开新创建的&#x200B;**[!UICONTROL Product profile]**&#x200B;并选择&#x200B;**[!UICONTROL Permissions]**&#x200B;选项卡。

   ![](assets/do-not-localize/triggers_3.png)

1. 单击&#x200B;**[!UICONTROL Edit]**&#x200B;配置不同的功能，并通过单击加号(+)图标选择要分配给您的&#x200B;**[!UICONTROL Product profile]**&#x200B;的权限。

   有关如何管理权限的更多信息，请参阅[Admin Console文档](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html)。

1. 对于&#x200B;**[!UICONTROL Report Suites]**&#x200B;功能，请添加稍后需要使用的&#x200B;**[!UICONTROL Report Suites]**。

   如果您没有任何报表包，则可以按照[这些步骤](../../integrations/using/gs-aa.md)创建报表包。

   ![](assets/do-not-localize/triggers_4.png)

1. 对于&#x200B;**[!UICONTROL Metrics]**&#x200B;功能，添加稍后需要配置的&#x200B;**[!UICONTROL Metrics]**。

   如果需要，您可以打开自动包含选项，该选项会将每个权限项添加到已包含列表中，并自动添加新权限项。

   ![](assets/do-not-localize/triggers_13.png)

1. 对于&#x200B;**[!UICONTROL Dimensions]**&#x200B;功能，添加未来配置所需的&#x200B;**[!UICONTROL Dimensions]**。

   确保所选维度与要在外部帐户中配置的维度匹配，并与Adobe Analytics中的相应eVar编号一致。

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

您的产品配置文件现已配置完成。 然后，您需要创建OAuth项目。

## 创建OAuth项目 {#create-adobe-io}

要继续配置Adobe Analytics连接器，请访问Adobe Developer控制台并创建您的OAuth服务器到服务器项目。

有关详细信息，请参阅[此页面](oauth-technical-account.md#oauth-service)。

## 配置和使用情况 {#adobe-analytics-connector-usage}

请参阅[Adobe Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}以了解如何使用Adobe Campaign和Adobe Analytics。