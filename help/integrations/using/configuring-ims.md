---
product: campaign
title: 配置IMS
description: 了解如何通过Adobe ID连接
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---

# 配置IMS{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>Adobe IMS实施严格由Adobe技术管理员负责。 请联系您的Adobe主管以开始实施过程。

## 先决条件 {#prerequisites}

要使用与IMS的集成，请执行以下操作：

* 您必须拥有Adobe Experience Cloud组织和IMS ID(在首次连接到Adobe Experience Cloud时提供)。
* 您必须在Experience Cloud中添加用户。 有关详细信息，请参见[此页面](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!NOTE]
>
>确保用户已链接到将与Adobe Campaign同步的Adobe Experience Cloud组。 请参阅[配置外部帐户](#configuring-the-external-account)。

## 更新控制台 {#updating-the-console}

要使用此功能，您必须安装最新版本的控制台。

## 安装包 {#installing-the-package}

必须安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包。 安装集成包与安装标准包相同，有关详细信息，请参阅[本页](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/ims_6.png)

## 配置外部帐户 {#configuring-the-external-account}

在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中配置&#x200B;**Adobe Experience Cloud**&#x200B;外部帐户。

>[!CAUTION]
>
>此配置为技术管理员保留。

![](assets/ims_5.png)

输入以下信息：

* 使用的IMS服务器的连接信息（ID和密钥）。 此信息由Adobe支持提供。 有关更多信息，请参阅[Adobe Experience Cloud管理员常见问题解答](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html)。

   **[!UICONTROL Callback server]**&#x200B;地址必须在&#x200B;**https**&#x200B;中指定。 此字段对应于您的Adobe Campaign实例的访问URL。

* IMS组织ID:此信息可在Experience Cloud（位于&#x200B;**[!UICONTROL Administration > Experience Cloud Details]**&#x200B;中）上获取，并在您首次连接到Adobe Experience Cloud时提供。
* 关联掩码：利用此字段，可定义语法，以允许将Enterprise Dashboard中的配置名称与Adobe Campaign中的组同步。 如果您使用语法“Campaign - tenant_id -(.*)”，则在Adobe Campaign中创建的安全组将链接到Enterprise Dashboard中的配置名称“Campaign - tenant_id - internal_name”。

   >[!CAUTION]
   >
   >关联掩码对于通过Adobe ID进行连接才能正常工作至关重要。

* Adobe Experience Cloud连接信息，特别是Adobe Experience Cloud租户的名称。
