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
source-git-commit: 25673f33c626edd5b7f4c7ba240364b3ea8d616a
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 6%

---


# 为 Adobe Experience Cloud 触发器配置 Adobe I/O {#configuring-adobe-io}

>[!CAUTION]
>
>如果您使用的是通过身份验证进行触发器集成的旧版本，**您需要按如下所述移动到Adobe I/O。**&#x200B;旧版 oAuth 身份验证模式将于 2021 年 4 月 30 日停用。[了解详情](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>请注意，在移动到Adobe I/O期间，某些传入触发器可能会丢失。

## 先决条件{#adobe-io-prerequisites}

此集成仅适用于从&#x200B;**Campaign Classic 20.3、20.2.4、19.1.8和Gold Standard 11版本**&#x200B;开始。

在启动此实施之前，请检查您拥有：

* 有效的&#x200B;**组织标识符**:Identity Management系统(IMS)组织标识符是Adobe Experience Cloud内的唯一标识符，用于VisitorID服务和IMS单点登录(SSO)。 [了解详情](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **开发人员对您组织的访问**。  如果您需要请求IMS组织的系统管理员权限，请按照本页](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html)中详细的[过程为所有产品用户档案提供此访问权限。

## 第1步：创建/更新Adobe I/O项目{#creating-adobe-io-project}

1. 访问Adobe I/O，并与IMS组织的系统管理员一起登录。

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

   ![](assets/do-not-localize/adobe_io_4.png)

1. 上传公钥，然后单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 选择名为&#x200B;**Analytics-&lt;组织名称>**&#x200B;的产品用户档案，然后单击&#x200B;**[!UICONTROL Save configured API]**。

   ![](assets/do-not-localize/adobe_io_6.png)

1. 在您的项目中，选择&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;并复制以下信息：
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

>[!NOTE]
>
>应将私钥以base64 UTF-8格式进行编码。 在对新行进行编码之前，请记住从密钥中删除新行，但私钥除外。 私钥必须与用于创建集成的私钥相同。 要测试私钥的base64编码，可以使用[此网站](https://www.base64encode.org/)。

## 第3步：更新流水线标记{#update-pipelined-tag}

要更新[!DNL pipelined]标记，您需要将身份验证类型更新为配置文件&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的Adobe I/O项目，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```
