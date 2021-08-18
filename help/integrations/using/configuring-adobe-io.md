---
product: campaign
title: 为 Adobe Experience Cloud 触发器配置 Adobe I/O
description: 了解如何为Adobe Experience Cloud Triggers配置Adobe I/O
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 550c4afc5cc77867b56d17565bef3f18b1df12a2
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 3%

---

# 为 Adobe Experience Cloud 触发器配置 Adobe I/O {#configuring-adobe-io}

>[!CAUTION]
>
>如果您通过oAuth身份验证使用旧版Triggers集成，则&#x200B;**您需要按照以下**所述移至Adobe I/O。
>请注意，在迁移到[!DNL Adobe I/O]期间，某些传入触发器可能会丢失。
>
>Campaign [的旧版oAuth身份验证模式已在&#x200B;**2021年8月18日**&#x200B;停用](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。 托管环境将从扩展中受益，直到2021年11月30日&#x200B;**。**&#x200B;作为内部部署或混合型客户，请联系Adobe客户关怀团队，将支持延长至2021年11月30日。 您必须提供[OAuth应用程序](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)的AppID才能Adobe。

## 先决条件 {#adobe-io-prerequisites}

此集成仅适用于从&#x200B;**Campaign Classic20.3、20.2.4、19.1.8和[!DNL Gold Standard] 11版本**&#x200B;开始的版本。

在启动此实施之前，请检查您具有：

* 有效的&#x200B;**组织标识符**:Identity Management系统(IMS)组织标识符是Adobe Experience Cloud中的唯一标识符，例如用于VisitorID服务和IMS单点登录(SSO)。 [了解详情](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **开发人员对贵组织的访问**。 IMS组织的系统管理员需要遵循&#x200B;**将开发人员添加到单个产品配置文件**
本页](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html)中详细的[过程，以提供与触发器关联的Adobe Analytics产品`Analytics - {tenantID}`产品配置文件的开发人员访问权限。

## 步骤1:创建/更新Adobe I/O项目 {#creating-adobe-io-project}

1. 访问[!DNL Adobe I/O] ，然后使用IMS组织的开发人员访问权限登录。

   >[!NOTE]
   >
   > 确保您已登录到正确的组织门户。

1. 从实例配置文件ims/authIMSTAClientId中提取现有集成客户端标识符（客户端ID）。 非现有或空属性表示未配置客户端标识符。

   >[!NOTE]
   >
   >如果您的客户端标识符为空，则可以直接&#x200B;**[!UICONTROL Create a New project]** Adobe I/O。

1. 使用提取的客户端标识符标识现有项目。 查找具有与上一步中提取的相同客户端标识符的现有项目。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 选择&#x200B;**[!UICONTROL + Add to Project]**，然后选择&#x200B;**[!UICONTROL API]**。

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在&#x200B;**[!UICONTROL Add an API]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Adobe Analytics]**。

   ![](assets/do-not-localize/adobe_io_2.png)

1. 选择&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;作为身份验证类型。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果您的客户端ID为空，请选择&#x200B;**[!UICONTROL Generate a key pair]**&#x200B;以创建公钥和私钥对。

   然后，将自动下载密钥，默认到期日期为365天。 过期后，您将需要创建新密钥对并更新配置文件中的集成。 使用选项2，您可以选择手动创建并上传具有较长过期日期的&#x200B;**[!UICONTROL Public key]**。

   >[!CAUTION]
   >
   >当出现下载提示时，您应保存config.zip文件，因为您将无法再次下载它。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 单击 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 选择任意现有的&#x200B;**[!UICONTROL Product profile]**，或根据需要创建新的。 此&#x200B;**[!UICONTROL Product profile]**&#x200B;不需要权限。 有关[!DNL Analytics] **[!UICONTROL Product Profiles]**&#x200B;的更多信息，请参阅[Adobe Analytics文档](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console)。

   然后，单击&#x200B;**[!UICONTROL Save configured API]**。

   ![](assets/do-not-localize/adobe_io_6.png)

1. 在您的项目中，选择&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;并复制&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;下的以下信息：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O证书将在12个月后过期。 您每年需要生成一个新的密钥对。

## 步骤2:在Adobe Campaign中添加项目凭据 {#add-credentials-campaign}

>[!NOTE]
>
>如果您的客户端标识符在[步骤1中不为空，则不需要此步骤：创建/更新Adobe I/O项目](#creating-adobe-io-project)。

私钥应以base64 UTF-8格式进行编码。 为实现此操作，请执行以下步骤：

1. 使用在[步骤1中生成的私钥：创建/更新Adobe I/O项目部分](#creating-adobe-io-project)。 私钥必须与用于创建集成的私钥相同。

1. 使用以下命令对私钥进行编码：`base64 ./private.key > private.key.base64`。 这会将base64内容保存到新文件`private.key.base64`中。

   >[!NOTE]
   >
   >有时，在复制/粘贴私钥时，会自动添加额外的行。 在对私钥进行编码之前，请记得将其删除。

1. 从文件`private.key.base64`复制内容。

1. 通过SSH登录到安装了Adobe Campaign实例的每个容器，并通过以`neolane`用户身份运行以下命令在Adobe Campaign中添加项目凭据。 这将在实例配置文件中插入&#x200B;**[!UICONTROL Technical Account]**&#x200B;凭据。

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## 步骤3:更新流水线标记 {#update-pipelined-tag}

>[!NOTE]
>
>如果您的客户端标识符在[步骤1中不为空，则不需要此步骤：创建/更新Adobe I/O项目](#creating-adobe-io-project)。

要更新[!DNL pipelined]标记，您需要更新身份验证类型以Adobe I/O配置文件&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的项目，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```

然后，运行`config -reload`并重新启动[!DNL pipelined]以便考虑所做的更改。
