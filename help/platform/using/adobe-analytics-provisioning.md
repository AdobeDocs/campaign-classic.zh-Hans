---
product: campaign
title: Adobe Analytics connector预配
description: 了解有关Adobe Analytics连接器配置的更多信息
feature: Overview
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 2%

---

# Adobe Analytics Connector 配置 {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> 这些步骤只应由混合实施和内部部署实施执行。
>
>对于托管的实施，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 团队。

Adobe Campaign Classic与Adobe Analytics身份验证之间的集成支持AdobeIdentity Management服务(IMS):

* 如果您管理迁移的外部帐户，则必须实施Adobe IMS并通过Adobe ID连接到Adobe Campaign。 通过Adobe ID IMS登录的用户应是 **数据连接器** 帐户，并且拥有 **产品配置文件** 下文提及。

* 如果您要实施新连接器，则实施Adobe IMS是可选的。 如果没有Adobe ID用户，Adobe Campaign将使用技术用户与Adobe Analytics同步。

要使此集成正常工作，您必须创建专门用于Analytics连接器的Adobe Analytics产品配置文件。 然后，您将需要创建一个Adobe I/O项目。

## 创建Adobe Analytics产品配置文件 {#analytics-product-profile}

产品配置文件可确定用户对您的不同Analytics组件具有的访问级别。

如果您已经拥有Analytics产品配置文件，则仍应该创建一个专门用于Analytics连接器的新Adobe Analytics产品配置文件。 这将确保您的产品配置文件已设置为具有此集成的正确权限。

有关产品配置文件的更多信息，请参阅 [管理控制台文档](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. 从 [管理控制台](https://adminconsole.adobe.com/)，选择您的Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. 单击 **[!UICONTROL New Profile]**。

   ![](assets/do-not-localize/triggers_2.png)

1. 添加 **[!UICONTROL Product profile name]**，我们建议使用以下语法： `reserved_campaign_classic_<Company Name>`. 然后，单击 **[!UICONTROL Next]**.

   此 **[!UICONTROL Product profile]** 应专门用于Analytics连接器，以防止出现配置错误。

1. 打开新创建的 **[!UICONTROL Product profile]** ，然后选择 **[!UICONTROL Permissions]** 选项卡。

   ![](assets/do-not-localize/triggers_3.png)

1. 配置不同功能单击 **[!UICONTROL Edit]** ，然后选择要分配给 **[!UICONTROL Product profile]** 单击加号(+)图标。

   有关如何管理权限的更多信息，请参阅 [管理控制台文档](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. 对于 **[!UICONTROL Report Suites]** 功能，添加 **[!UICONTROL Report Suites]** 您需要稍后使用。

   如果您没有任何报表包，可以在以下步骤中创建 [这些步骤](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. 对于 **[!UICONTROL Metrics]** 功能，添加 **[!UICONTROL Metrics]** 您以后需要配置。

   如果需要，您可以打开自动包含选项，该选项会将每个权限项添加到包含的列表中，并自动添加新权限项。

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

1. 访问Adobe I/O并登录为 **系统管理员** 您组织的。

   有关管理员角色的更多信息，请参阅此 [页面](https://helpx.adobe.com/enterprise/using/admin-roles.html).

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

1. 使用步骤6中生成的私钥。

   如果您已使用这些凭据设置触发器，则此连接器配置的私钥必须相同。

1. 使用以下命令对私钥进行编码： `base64 ./private.key > private.key.base64`. 这会将base64内容保存到新文件 `private.key.base64`.

   >[!NOTE]
   >
   >有时，在复制/粘贴私钥时，会自动添加额外的行。 在对私钥进行编码之前，请记得将其删除。

1. 从文件复制内容 `private.key.base64`.

1. 通过SSH登录到安装了Adobe Campaign实例的每个容器，并通过以下命令(如 `neolane` 用户。 这将插入 **[!UICONTROL Technical Account]** 实例配置文件中的凭据。

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```
您现在可以开始使用Analytics连接器并跟踪客户行为。
