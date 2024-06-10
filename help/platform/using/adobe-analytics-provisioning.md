---
product: campaign
title: Adobe Analytics连接器配置
description: 了解有关Adobe Analytics连接器配置的更多信息
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于v7内部部署和混合部署"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 514f390b5615a504f3805de68f882af54e0c3949
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 1%

---

# Adobe Analytics Connector 配置 {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> 这些步骤只能通过混合和内部部署实施来执行。
>
>对于托管和营销活动Managed Services实施，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 团队。

Adobe Campaign Classic与Adobe Analytics身份验证之间的集成支持AdobeIdentity Management服务(IMS)：

* 如果您正在管理已迁移的外部帐户，则必须实施Adobe IMS并通过Adobe ID连接到Adobe Campaign。

  请注意，通过Adobe ID IMS登录的用户必须是 **数据连接器** Adobe Analytics帐户并拥有对的权限 **产品配置文件** 已提及 [以下](#analytics-product-profile).

问题是Data Connector的所有者不是登录Campaign并尝试与Analytics集成的用户。

* 如果您正在实施新连接器，实施Adobe IMS是可选的。 如果没有Adobe ID用户，Adobe Campaign将使用技术用户与Adobe Analytics同步。

为使这种集成正常工作，您必须创建专门用于Analytics连接器的Adobe Analytics产品配置文件。 然后，您需要创建一个Adobe I/O项目。

>[!AVAILABILITY]
>
> Adobe已弃用服务帐户(JWT)凭据，Campaign与Adobe解决方案和应用程序的集成现在必须依赖OAuth服务器到服务器凭据。 </br>
>
> * 如果您已实施与Campaign的入站集成，则必须迁移技术帐户，如中所述 [本文档](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). 现有服务账户(JWT)凭证将继续使用至2025年1月27日。 此外，从2024年6月3日开始，在开发人员控制台中创建新的服务帐户(JWT)凭据不再可能。 在此日期之后，无法创建新的服务帐户(JWT)凭据或将其添加到项目中。 </br>
>
> * 如果您实施了叫客集成，如Campaign-Analytics集成或Experience Cloud Triggers集成，则在2025年1月27日之前它们将继续工作。 但是，在该日期之前，您必须将Campaign环境升级到v7.4.1，并将技术帐户迁移到oAuth。 自2024年6月3日起，在开发人员控制台中不再可能创建新的服务帐户(JWT)凭据，因此，在此日期之后，您无法依赖JWT创建新的出站集成

## 创建Adobe Analytics产品配置文件 {#analytics-product-profile}

产品配置文件确定用户对其他Analytics组件的访问级别。

如果您已有Analytics产品配置文件，则仍应创建一个新的Adobe Analytics产品配置文件，专门用于Analytics连接器。 这将确保为您的产品配置文件设置此集成的正确权限。

有关产品配置文件的详细信息，请参阅 [Admin console文档](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. 从 [Admin console](https://adminconsole.adobe.com/)，选择您的Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. 单击 **[!UICONTROL New Profile]**。

   ![](assets/do-not-localize/triggers_2.png)

1. 添加 **[!UICONTROL Product profile name]**，我们建议使用以下语法： `reserved_campaign_classic_<Company Name>`. 然后，单击 **[!UICONTROL Next]**.

   此 **[!UICONTROL Product profile]** 应仅用于Analytics Connector，以防止出现配置错误错误。

1. 打开您新创建的 **[!UICONTROL Product profile]** 并选择 **[!UICONTROL Permissions]** 选项卡。

   ![](assets/do-not-localize/triggers_3.png)

1. 配置不同的功能，单击 **[!UICONTROL Edit]** 并选择要分配给您的的权限 **[!UICONTROL Product profile]** 单击加号(+)图标。

   有关如何管理权限的更多信息，请参阅 [Admin console文档](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. 对于 **[!UICONTROL Report Suites]** 功能，添加 **[!UICONTROL Report Suites]** 稍后需要使用。

   如果您没有任何报表包，则可以按以下方式创建它 [这些步骤](../../platform/using/gs-aa.md).

   ![](assets/do-not-localize/triggers_4.png)

1. 对于 **[!UICONTROL Metrics]** 功能，添加 **[!UICONTROL Metrics]** 稍后您需要进行配置。

   如果需要，您可以打开自动包含选项，该选项会将每个权限项添加到已包含列表中，并自动添加新权限项。

   ![](assets/do-not-localize/triggers_13.png)

1. 对于 **[!UICONTROL Dimensions]** 功能，添加 **[!UICONTROL Dimensions]** 未来配置需要。

   确保所选的Dimension与要在外部帐户中配置的帐户匹配，并与Adobe Analytics中对应的eVar编号一致。

1. 对于 **[!UICONTROL Report Suite Tools]** 功能，添加以下权限：

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. 对于 **[!UICONTROL Analytics Tools]** 功能，添加以下权限：

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

您的产品配置文件现已配置完成。 然后，您需要创建Adobe I/O项目。

## 创建Adobe I/O项目 {#create-adobe-io}

1. 访问Adobe I/O并以下列身份登录 **系统管理员** 您组织的名称。

   有关管理员角色的更多信息，请参阅此 [页面](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. 单击 **[!UICONTROL Create a new project]**。

   ![](assets/do-not-localize/triggers_5.png)

1. 单击 **[!UICONTROL Add to Project]** 并选择 **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. 选择 [!DNL Adobe Analytics] 并单击 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_7.png)

1. 选择 **[!UICONTROL Service Account (JWT)]** 作为身份验证类型，然后单击 **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_8.png)

1. 选择 **[!UICONTROL Option 1: Generate a Key-Pair]** 选项并单击 **[!UICONTROL Generate a Key-Pair]**.

   随后将自动下载config.zip文件。

   ![](assets/do-not-localize/triggers_9.png)

1. 单击 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_10.png)

1. 选择 **[!UICONTROL Product profile]** 在前面的步骤中创建，详见此 [部分](#analytics-product-profile).

1. 然后，单击 **[!UICONTROL Save Configured API]**.

   ![](assets/do-not-localize/triggers_11.png)

1. 从项目中，选择 [!DNL Adobe Analytics] 并将以下信息复制到 **[!UICONTROL Service Account (JWT)]**：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. 使用在步骤6中生成的私钥。

   如果您已使用这些凭据设置触发器，则此连接器配置的私钥必须相同。

1. 使用以下命令对私钥进行编码： `base64 ./private.key > private.key.base64`. 这会将base64内容保存到新文件中 `private.key.base64`.

   >[!NOTE]
   >
   >复制/粘贴私钥时，有时可以自动添加额外的行。 在编码私钥之前，请记得删除它。

1. 复制文件中的内容 `private.key.base64`.

1. 通过SSH登录到安装了Adobe Campaign实例的每个容器，并通过运行以下命令（如下所示）在Adobe Campaign中添加项目凭据 `neolane` 用户。 这将插入 **[!UICONTROL Technical Account]** 实例配置文件中的凭据。

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

您现在可以开始使用Analytics Connector并跟踪客户行为。
