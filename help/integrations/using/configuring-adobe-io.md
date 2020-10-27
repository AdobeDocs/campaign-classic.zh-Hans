---
title: 为Adobe Experience Cloud触发器配置AdobeIO
seo-title: 为Adobe Experience Cloud触发器配置AdobeIO
description: 为Adobe Experience Cloud触发器配置AdobeIO
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# 为Adobe Experience Cloud触发器配置AdobeIO {#configuring-adobe-io}

先决条件配置包括：

* Adobe Campaign Classic建造ACC-19.1.9或ACC-20.2.1及更高版本。
* 有效的IMSOrgID。
* 开发者访问IMS组织。您需要请求IMS组织的系统管理员权限才能按照本页中详细的 [过程](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) ，为所有产品用户档案提供此访问权限。

## 第1步：创建／更新AdobeIO项目 {#creating-adobe-io-project}

1. 访问AdobeIO，并与IMSorg的系统管理员一起登录。

   >[!NOTE]
   >
   > 确保您登录到正确的IMSorg门户。

1. 从实例配置文件ims/authIMSTAClientId提取现有集成客户端ID。 非现有或空属性表示未配置客户端ID。

   >[!NOTE]
   >
   >如果客户端ID为空，则可以直接 **[!UICONTROL Create a New project]** 在AdobeIO中。

1. 您现在需要使用提取的客户端ID来标识现有项目。 查找与上一步提取的客户端ID相同的现有项目。

   ![](assets/adobe_io_8.png)

1. 选择 **[!UICONTROL + Add to Project]** 并选择 **[!UICONTROL API]**。

   ![](assets/adobe_io_1.png)

1. 在窗口中， **[!UICONTROL Add an API]**&#x200B;选择 **[!UICONTROL Adobe Analytics]**。

   ![](assets/adobe_io_2.png)

1. 选择 **[!UICONTROL Service Account (JWT)]** 身份验证类型。

   ![](assets/adobe_io_3.png)

1. 如果您的客户端ID为空，则选择 **[!UICONTROL Generate a key pair]** 以创建公共和专用密钥对。

   ![](assets/adobe_io_4.png)

1. 上传您的公钥并单击 **[!UICONTROL Next]**。

   ![](assets/adobe_io_5.png)

1. 选择名为Analytics-&lt;组 **织名称>的产品用户档案** ，然后单击 **[!UICONTROL Save configured API]**。

   ![](assets/adobe_io_6.png)

1. 从您的项目中，选 **[!UICONTROL Service Account (JWT)]** 择并复制以下信息：
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/adobe_io_7.png)

## 第2步：在Adobe Campaign中添加项目凭据 {#add-credentials-campaign}

要在Adobe Campaign中添加项目凭据，请以新用户身份对Adobe Campaign实例的所有容器运行以下命令，以将凭据插 **[!UICONTROL Technical Account]** 入实例配置文件中。

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>您应以base64 UTF-8格式对私钥进行编码。 在编码新行之前，请记住从密钥中删除新行，但私钥除外。 私钥必须与用于创建集成的私钥相同。

## 第3步：更新管道化标签 {#update-pipelined-tag}

要更新 [!DNL pipelined] 标签，您需要将身份验证类型更新为配置文件 **config-&lt; instance-name >.xml中的AdobeIO项** 目，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```

>[!NOTE]
>
>如果您使用旧版JWT令牌使用旧版触发器集成，则还应添加AdobeIO API(详见第 [!DNL Adobe Analytics] 一步)，以自动迁移到新的触发器身份验证。
