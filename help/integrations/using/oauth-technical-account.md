---
product: campaign
title: 为API创建和配置您的Adobe技术帐户
description: 详细了解如何创建AdobeAPI帐户
role: User, Admin
level: Beginner
source-git-commit: efd09fd71069878a5096bfa3592e6ebbaa9dd4e4
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# 创建您的Adobe技术帐户 {#create-service-account}

服务器到服务器身份验证凭据允许应用程序的服务器生成访问令牌并代表应用程序本身进行API调用。 [了解更多信息](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## 迁移现有集成 {#migrate-jwt}

Adobe正在弃用服务帐户(JWT)凭据。 Campaign与Adobe解决方案和应用程序的集成现在必须依赖OAuth服务器到服务器凭据。

如果您在2024年6月之前已实施与Campaign的入站或出站集成，则必须将您的Campaign环境升级到v7.4.1，并根据详细信息将您的技术帐户迁移到oAuth [本文档内容](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. 现有服务帐户(JWT)凭据将继续工作，直到 **2025年1月27日**.

完成迁移后，必须将新凭据关联到Campaign，如中所述 [本节](#add-credentials).

## 为新集成创建新的OAuth技术帐户 {#oauth-service}

要为新集成创建您的OAuth技术帐户，请执行以下步骤：

1. 访问Adobe Developer控制台并以以下身份登录 **系统管理员** 您组织的名称。

   有关管理员角色的更多信息，请参阅此 [页面](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. 单击 **[!UICONTROL Create a new project]**。

   ![](assets/api-account-1.png)

1. 单击 **[!UICONTROL Add to Project]** 并选择 **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. 选择要与Campaign集成的产品，然后单击 **[!UICONTROL Next]**.

1. 选择 **[!UICONTROL OAuth Server-to-Server]** 作为身份验证类型，然后单击 **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. 选择 **[!UICONTROL Product profile]** 链接至您的项目。

   如果需要，您可以创建新插件。 [了解更多信息](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. 然后，单击 **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. 在项目中的凭据下，选择 [!DNL OAuth Server-to-Server] 并复制以下信息：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## 在Adobe Campaign中添加Oauth项目凭据 {#add-credentials}

请按照以下步骤在Adobe Campaign中添加OAuth项目凭据：

1. 通过SSH登录到安装了Adobe Campaign实例的每个容器。

1. 通过以下命令在Adobe Campaign中添加您的OAuth项目凭据： `neolane` 用户。 这将插入 **[!UICONTROL Technical Account]** 实例配置文件中的凭据。

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```
