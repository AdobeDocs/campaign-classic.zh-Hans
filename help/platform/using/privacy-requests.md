---
product: campaign
title: 管理隐私请求
description: 了解隐私请求
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: a8044037e889f59d4288a0746001e84d319f6bcf
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 98%

---

# 关于隐私请求 {#privacy-requests}

![](../../assets/v7-only.svg)

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
>有关个人数据以及管理数据的不同实体（数据控制者、数据处理方和数据主体）的更多信息，请参阅[个人数据和角色](privacy-and-recommendations.md#personal-data)。

## 先决条件 {#prerequesites}

Adobe Campaign 为数据控制者提供用于创建和处理 Adobe Campaign 中存储的数据的隐私请求的工具。但是，数据控制者负责处理与数据主体（电子邮件、客户关怀或 Web 门户）的关系。

因此，作为数据控制者，您的职责是确认发出请求的数据主体的身份，并确认返回给请求者的数据与数据主体有关。

## 安装隐私包 {#install-privacy-package}

要使用此功能，您需要通过 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**&#x200B;菜单安装 **[!UICONTROL Privacy Data Protection Regulation]** 包。有关如何安装隐私包的更多信息，请参阅[有详细说明的文档](../../installation/using/installing-campaign-standard-packages.md)。

在 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** 下创建了两个专用于隐私的新文件夹：

* **[!UICONTROL Privacy Requests]**：您将在此处创建隐私请求并跟踪其演变。
* **[!UICONTROL Namespaces]**：您将在此处定义用于识别 Adobe Campaign 数据库中的数据主体的字段。

![](assets/privacy-folders.png)

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** 中，每天运行三个技术工作流以处理隐私请求。

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**：此工作流会生成存储在 Adobe Campaign 中的收件人数据，并在隐私请求屏幕中提供下载。
* **[!UICONTROL Delete privacy requests data]**：此工作流会删除存储在 Adobe Campaign 中的收件人数据。
* **[!UICONTROL Privacy request cleanup]**：此工作流会清除 90 天以前的访问请求文件。

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]** 中，已添加 **[!UICONTROL Privacy Data Right]** 指明权限。数据控制者必须具有这项指明权限才能使用隐私工具。这使得他们可以创建新请求、跟踪其演变、使用 API 等。

![](assets/privacy-right.png)

## 命名空间 {#namesspaces}

在创建隐私请求之前，您需要定义将要使用的命名空间。这是将用于识别 Adobe Campaign 数据库中的数据主体的键。

开箱即用的三种命名空间：电子邮件、电话和手机。如果您需要其他命名空间（例如，收件人自定义字段），则可以从 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]** 创建新命名空间。

>[!NOTE]
>
>为获得最佳性能，建议使用现成的命名空间。
