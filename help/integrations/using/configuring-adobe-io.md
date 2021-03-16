---
solution: Campaign Classic
product: campaign
title: 为 Adobe Experience Cloud 触发器配置 Adobe I/O
description: 了解如何为Adobe Experience Cloud Triggers配置Adobe I/O
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 42166334d361ffdac13842cd9d07ca7c9859bbb2
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 6%

---


# 为 Adobe Experience Cloud 触发器配置 Adobe I/O {#configuring-adobe-io}

>[!CAUTION]
>
>如果您使用的是通过身份验证进行触发器集成的旧版本，**您需要按如下所述移动到Adobe I/O。**&#x200B;旧版 oAuth 身份验证模式将于 **2021 年 4 月 30 日**&#x200B;停用。[了解详情](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email)。
>
>请注意，在移动到[!DNL Adobe I/O]期间，某些传入触发器可能会丢失。

## 先决条件{#adobe-io-prerequisites}

此集成仅适用于从&#x200B;**Campaign Classic 20.3、20.2.4、19.1.8和Gold Standard 11版本**&#x200B;开始。

在启动此实施之前，请检查您拥有：

* 有效的&#x200B;**组织标识符**:Identity Management系统(IMS)组织标识符是Adobe Experience Cloud内的唯一标识符，用于VisitorID服务和IMS单点登录(SSO)。 [了解详情](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **开发人员对您组织的访问**。  如果您需要请求IMS组织的系统管理员权限，请按照本页](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html)中详细的[过程为所有产品用户档案提供此访问权限。

## 第1步：创建/更新Adobe I/O项目{#creating-adobe-io-project}

1. 访问[!DNL Adobe I/O]并使用IMS组织的系统管理员权限登录。

   >[!NOTE]
   >
   > 确保您已登录到正确的组织门户。

1. 从实例配置文件ims/authIMSTAClientId提取现有集成客户端标识符（客户端ID）。 非现有或空属性表示未配置客户端标识符。

   >[!NOTE]
   >
   >如果您的客户端标识符为空，则可以直接&#x200B;**[!UICONTROL Create a New project]**&#x200B;使用Adobe I/O。

1. 使用提取的客户端标识符标识现有项目。 查找具有与上一步提取的相同客户端标识符的现有项目。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 选择&#x200B;**[!UICONTROL + Add to Project]**&#x200B;并选择&#x200B;**[!UICONTROL API]**。

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在&#x200B;**[!UICONTROL Add an API]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Adobe Analytics]**。

   ![](assets/do-not-localize/adobe_io_2.png)

1. 选择&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;作为身份验证类型。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果您的客户端ID为空，请选择&#x200B;**[!UICONTROL Generate a key pair]**&#x200B;以创建公钥和私钥对。

   然后，将自动下载密钥，默认到期日期为365天。 到期后，您需要创建新密钥对并更新配置文件中的集成。 使用选项2，您可以选择手动创建并上传具有较长到期日期的&#x200B;**[!UICONTROL Public key]**。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 单击 **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. 选择任何现有的&#x200B;**[!UICONTROL Product profile]**，或根据需要创建新的。 然后，单击&#x200B;**[!UICONTROL Save configured API]**。

   有关[!DNL Analytics] **[!UICONTROL Product Profiles]**&#x200B;的详细信息，请参阅[Adobe Analytics文档](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console)。

   ![](assets/do-not-localize/adobe_io_6.png)

1. 在您的项目中，选择&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;并复制&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;下的以下信息：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O证书将在12个月后过期。 您需要每年生成新的密钥对。

## 第2步：在Adobe Campaign{#add-credentials-campaign}中添加项目凭据

要在Adobe Campaign中添加项目凭据，请在Adobe Campaign实例的所有容器上以“neolane”用户身份运行以下命令，以将&#x200B;**[!UICONTROL Technical Account]**&#x200B;凭据插入实例配置文件。

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

私钥应以base64 UTF-8格式进行编码。 为实现此操作，请执行以下步骤：

1. 使用在[步骤1中生成的私钥：创建/更新Adobe I/O项目部分](#creating-adobe-io-project)。 私钥必须与用于创建集成的私钥相同。

1. 使用以下命令对私钥进行编码：```base64 ./private.key```。

   >[!NOTE]
   >
   >有时，在复制/粘贴私钥时可以自动添加其他行。 请记住，在对私钥进行编码之前删除它。

1. 使用以base64 UTF-8格式编码的新生成的私钥运行上述详细命令。

## 第3步：更新流水线标记{#update-pipelined-tag}

要更新[!DNL pipelined]标记，您需要将身份验证类型更新为配置文件&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的Adobe I/O项目，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```
