---
solution: Campaign Classic
product: campaign
title: Adobe Analytics Connector
description: 了解有关 Adobe Analytics Connector 的更多信息 设置
feature: Overview
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 671e29425e8962ced833c10303b6edce7afda462
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 4%

---

# Adobe Analytics Connector 配置 {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> 这些步骤只应由混合实施和内部部署实施执行。
>
>对于托管的实施，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 团队。

The integration between Adobe Campaign Classic and Adobe Analytics authentication supports Adobe Identity Management Service (IMS):

* 如果您管理迁移的外部帐户，则必须实施Adobe IMS并通过Adobe ID连接到Adobe Campaign。 通过Adobe ID IMS登录的用户应是 **数据连接器** 帐户，并且拥有 **产品配置文件** 下文提及。

* 如果您要实施新连接器，则实施Adobe IMS是可选的。 如果没有Adobe ID用户，Adobe Campaign将使用技术用户与Adobe Analytics同步。

要使此集成正常工作，您必须创建专门用于Analytics连接器的Adobe Analytics产品配置文件。 然后，您将需要创建一个Adobe I/O项目。

## 创建Adobe Analytics产品配置文件 {#analytics-product-profile}

产品配置文件可确定用户对您的不同Analytics组件具有的访问级别。

如果您已经拥有Analytics产品配置文件，则仍应该创建一个专门用于Analytics连接器的新Adobe Analytics产品配置文件。 这将确保您的产品配置文件已设置为具有此集成的正确权限。

有关产品配置文件的更多信息，请参阅 [管理控制台文档](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. From the [Admin console](https://adminconsole.adobe.com/), select your Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. 单击 **[!UICONTROL New Profile]**。

   ![](assets/do-not-localize/triggers_2.png)

1. 添加 **[!UICONTROL Product profile name]**，我们建议使用以下语法： `reserved_campaign_classic_<Company Name>`. 然后，单击 **[!UICONTROL Next]**.

   此 **[!UICONTROL Product profile]** 应专门用于Analytics Connector，以防止出现配置错误。

1. 打开新创建的 **[!UICONTROL Product profile]** ，然后选择 **[!UICONTROL Permissions]** 选项卡。

   ![](assets/do-not-localize/triggers_3.png)

1. 配置不同功能单击 **[!UICONTROL Edit]** ，然后选择要分配给 **[!UICONTROL Product profile]** 单击加号(+)图标。

   有关如何管理权限的更多信息，请参阅 [管理控制台文档](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. 对于 **[!UICONTROL Report Suites]** 功能，添加 **[!UICONTROL Report Suites]** 您需要稍后使用。

   如果您没有任何报表包，可以在以下步骤中创建 [这些步骤](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. For the **[!UICONTROL Metrics]** capability, add the **[!UICONTROL Metrics]** you will need to configure later on.

   If needed, you can switch on the Auto-include option which will add every permissions item into the included list and will automatically add new permission items.

   ![](assets/do-not-localize/triggers_13.png)

1. 对于 **[!UICONTROL Dimensions]** 功能，添加 **[!UICONTROL Dimensions]** 您以后需要配置。

1. 对于 **[!UICONTROL Report Suite Tools]** 功能，请添加以下权限：

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. 对于 **[!UICONTROL Analytics Tools]** 功能，请添加以下权限：

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

您的产品配置文件现已配置完成。 然后，您需要创建Adobe I/O项目。

## 创建Adobe I/O项目 {#create-adobe-io}

1. 访问Adobe I/O并登录为 **系统管理员** IMS组织的ID。

   For more information on Admin roles, refer to this [page](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. 单击 **[!UICONTROL Create a new project]**。

   ![](assets/do-not-localize/triggers_5.png)

1. 单击 **[!UICONTROL Add to Project]** 选择 **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. 选择 [!DNL Adobe Analytics] 并单击 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_7.png)

1. 选择 **[!UICONTROL Service Account (JWT)]** 作为身份验证类型，单击 **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_8.png)

1. 选择 **[!UICONTROL Option 1: Generate a Key-Pair]** 选项并单击 **[!UICONTROL Generate a Key-Pair]**.

   随后将自动下载config.zip文件。

   ![](assets/do-not-localize/triggers_9.png)

1. 单击 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_10.png)

1. 选择 **[!UICONTROL Product profile]** 创建于 [部分](#analytics-product-profile).

1. 然后，单击 **[!UICONTROL Save Configured API]**.

   ![](assets/do-not-localize/triggers_11.png)

1. 在您的项目中，选择 [!DNL Adobe Analytics] 并在 **[!UICONTROL Service Account (JWT)]**:

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