---
product: campaign
title: 管理隐私请求
description: 了解隐私请求
feature: Privacy, Privacy Tools
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 92%

---

# 关于隐私请求 {#privacy-requests}



有关隐私管理的一般演示文稿，请参阅[此部分](privacy-management.md)。

此信息适用于 GDPR、CCPA、PDPA 和 LGPD。有关这些法规的更多信息，请参阅[此部分](privacy-management.md#privacy-management-regulations)。

>[!NOTE]
>
>[此部分](#sale-of-personal-information-ccpa)中说明了特定于 CCPA 的个人信息销售的选择退出。

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

为了帮助您促进隐私就绪，Adobe Campaign 允许您处理访问和删除请求。**访问权**&#x200B;和&#x200B;**被遗忘权**（删除请求）在[此部分](privacy-management.md#right-access-forgotten)中进行了描述。

Adobe Campaign 为数据控制者提供两种执行隐私访问和删除请求的方法：

* 通过 **Adobe Campaign 界面**：数据控制者在 Adobe Campaign 中为每项隐私请求创建新的隐私请求。请参阅[此小节](privacy-requests-ui.md)。
* 通过 **API**：Adobe Campaign 提供一个 API，允许使用 SOAP 自动处理隐私请求。请参阅[此小节](privacy-requests-api.md)。

>[!NOTE]
>
>* 有关个人数据以及管理数据的不同实体（数据控制者、数据处理方和数据主体）的更多信息，请参阅[个人数据和角色](privacy-and-recommendations.md#personal-data)。
>* 要了解有关隐私请求的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/privacy/privacy){target=_blank}。

<!--
## Prerequisites {#prerequesites}

Adobe Campaign offers Data Controllers tools to create and process Privacy requests for data stored in Adobe Campaign. However, it is the Data Controller's responsibility to handle the relationship with the Data Subject (email, customer care or a web portal).

It is therefore your responsibility as a Data Controller to confirm the identity of the Data Subject making the request and to confirm that the data returned to the requester is about the Data Subject.

## Installing the Privacy package {#install-privacy-package}

In order to use this feature, you need to install the **[!UICONTROL Privacy Data Protection Regulation]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]** menu. For more information on how to install packages, refer to the [detailed documentation](../../installation/using/installing-campaign-standard-packages.md).

Two new folders, specific to Privacy, are created under **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: this is where you will create your Privacy requests and track their evolution.
* **[!UICONTROL Namespaces]**: this is where you will define the field that will be used to identify the Data Subject in the Adobe Campaign database.

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, three technical workflows run every day to process Privacy requests.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: this workflow generates the recipient's data stored in Adobe Campaign and makes it available for download in the privacy request's screen.
* **[!UICONTROL Delete privacy requests data]**: this workflow deletes the recipient's data stored in Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: this workflow erases the access request files that are older than 90 days.

In **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**, the **[!UICONTROL Privacy Data Right]** named right has been added. This named right is required for Data Controllers in order for them to use privacy tools. This allows them to create new requests, track their evolution, use the API, etc.

![](assets/privacy-right.png)

## Namespaces {#namesspaces}

Before creating Privacy requests, you need to define the namespace you will use. This is the key that will be used to identify the Data Subject in the Adobe Campaign database.

Three namespaces are available out-of-the-box: email, phone and mobile phone. If you need a different namespace (a recipient custom field, for example), you can create a new one from **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>For optimal performance, it is recommended to use out-of-the-box namespaces.
-->