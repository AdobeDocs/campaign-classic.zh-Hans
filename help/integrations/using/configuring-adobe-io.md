---
product: campaign
title: 为 Adobe Experience Cloud 触发器配置 Adobe I/O
description: 了解如何为Adobe Experience Cloud Triggers配置Adobe I/O
feature: Triggers
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 4%

---

# 为 Adobe Experience Cloud 触发器配置 Adobe I/O {#configuring-adobe-io}



>[!CAUTION]
>
>如果您通过oAuth身份验证使用旧版本的Triggers集成， **您需要按如下所述移至Adobe I/O**.
>请注意，在此移动到 [!DNL Adobe I/O]，某些传入的触发器可能会丢失。
>
>Campaign的旧版oAuth身份验证模式已于 **2021年10月20日**. 托管环境可从扩展中获益，直到 **2022年5月25日**. 作为内部部署或混合型部署客户，请联系Adobe客户关怀团队，将支持延长至 **2022年5月**. 您必须 [提供OAuth应用程序的应用程序ID](../../integrations/using/configuring-pipeline.md#step-optional) Adobe。

## 先决条件 {#adobe-io-prerequisites}

此集成仅适用于 **Campaign Classic20.2.4及更高版本、19.1.8和Gold Standard 11版本**.

在开始此实施之前，请检查您是否拥有：

* 有效的 **组织标识符**：组织ID是Adobe Experience Cloud中的唯一标识符，用于VisitorID服务和IMS单点登录(SSO)。 [了解详情](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans)
* a **开发人员访问权限** 添加到您的组织。 组织的系统管理员需要遵循 **将开发人员添加到单个产品配置文件** 详细过程 [本页内容](https://helpx.adobe.com/enterprise/using/manage-developers.html) 为提供开发人员访问权限 `Analytics - {tenantID}` 与触发器关联的Adobe Analytics产品的产品配置文件。

## 步骤1：创建/更新Adobe I/O项目 {#creating-adobe-io-project}

1. 访问 [!DNL Adobe I/O] 并使用贵组织的开发人员访问权限登录。

   >[!NOTE]
   >
   > 确保您已登录到正确的组织门户。

1. 从实例配置文件ims/authIMSTAClientId中提取现有集成客户端标识符（客户端ID）。 不存在或空属性表示未配置客户端标识符。

   >[!NOTE]
   >
   >如果客户端标识符为空，您可以直接 **[!UICONTROL Create a New project]** Adobe I/O中。

1. 使用提取的客户端标识符标识现有项目。 查找与上一步提取的客户端标识符相同的现有项目。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 选择 **[!UICONTROL + Add to Project]** 并选择 **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在 **[!UICONTROL Add an API]** 窗口，选择 **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. 选择 **[!UICONTROL Service Account (JWT)]** 作为身份验证类型。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果您的客户端ID为空，请选择 **[!UICONTROL Generate a key pair]** 创建公钥和私钥对。

   随后，这些密钥将自动下载，默认到期日期为365天。 过期后，您将需要创建新密钥对并在配置文件中更新集成。 利用选项2，您可以选择手动创建和上传 **[!UICONTROL Public key]** 到期日期更长的。

   有关如何替换过期证书密钥对的分步指南，请参阅 [此页面](https://developer.adobe.com/developer-console/docs/guides/email-alerts/cert-expiry/#a-step-by-step-guide-to-replacing-expiring-certificate-key-pairs).


   >[!CAUTION]
   >
   >出现下载提示时，您应该保存config.zip文件，因为您将无法再次下载。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 单击 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 选择任何现有的 **[!UICONTROL Product profile]** 或根据需要创建一个新版本。 无需权限 **[!UICONTROL Product profile]**. 有关的详细信息 [!DNL Analytics] **[!UICONTROL Product Profiles]**，请参阅 [Adobe Analytics文档](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console).

   然后，单击 **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. 从项目中，选择 **[!UICONTROL Adobe Analytics]** 并将以下信息复制到 **[!UICONTROL Service Account (JWT)]**：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O证书将在12个月后过期。 您需要每年生成一个新的密钥对。

## 步骤2：在Adobe Campaign中添加项目凭据 {#add-credentials-campaign}

>[!NOTE]
>
>如果中的客户端标识符不为空，则不需要执行此步骤 [步骤1：创建/更新Adobe I/O项目](#creating-adobe-io-project).

私钥应采用base64 UTF-8格式编码。 为实现此操作，请执行以下步骤：

1. 使用在中生成的私钥 [步骤1：创建/更新Adobe I/O项目部分](#creating-adobe-io-project). 私钥应与用于创建集成的私钥相同。

1. 使用以下命令对私钥进行编码： `base64 ./private.key > private.key.base64`. 这会将base64内容保存到新文件中 `private.key.base64`.

   >[!NOTE]
   >
   >复制/粘贴私钥时，有时可以自动添加额外的行。 在编码私钥之前，请记得删除它。

1. 复制文件中的内容 `private.key.base64`.

1. 通过SSH登录到安装了Adobe Campaign实例的每个容器，并通过运行以下命令（如下所示）在Adobe Campaign中添加项目凭据 `neolane` 用户。 这将插入 **[!UICONTROL Technical Account]** 实例配置文件中的凭据。

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## 步骤3：更新管道标记 {#update-pipelined-tag}

>[!NOTE]
>
>如果中的客户端标识符不为空，则不需要执行此步骤 [步骤1：创建/更新Adobe I/O项目](#creating-adobe-io-project).

更新 [!DNL pipelined] 标签中，您需要更新身份验证类型以在配置文件中Adobe I/O项目 **config-&lt; instance-name >.xml** 如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```

然后，运行 `config -reload` 以及重启 [!DNL pipelined] 以考虑更改。
