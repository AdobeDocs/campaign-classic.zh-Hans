---
solution: Campaign Classic
product: campaign
title: 配置IMS
description: 了解如何通过Adobe ID连接
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: db595e59f4725ba5d125e688e7bfc6d1c1a03d9f
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---


# 配置IMS{#configuring-ims}

>[!IMPORTANT]
>
>Adobe IMS实施严格保留给Adobe技术管理员。 与Adobe主管联系以开始实施过程。

## 先决条件{#prerequisites}

要使用与IMS的集成：

* 您必须具有Adobe Experience Cloud组织和IMS ID(在您首次连接到Adobe Experience Cloud时提供)。
* 您必须在Experience Cloud中添加用户。 有关详细信息，请参见[此页面](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!NOTE]
>
>确保您的用户已链接到将与Adobe Experience Cloud同步的Adobe Campaign组。 请参阅[配置外部帐户](#configuring-the-external-account)。

## 更新控制台{#updating-the-console}

要使用此功能，必须安装最新版本的控制台。

## 安装程序包{#installing-the-package}

必须安装&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包。 安装集成包与安装标准包相同，详见[本页](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/ims_6.png)

## 配置外部帐户{#configuring-the-external-account}

在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中配置&#x200B;**Adobe Experience Cloud**&#x200B;外部帐户。

>[!CAUTION]
>
>此配置为技术管理员保留。

![](assets/ims_5.png)

输入以下信息：

* 使用的IMS服务器的连接信息（ID和密钥）。 此信息由Adobe支持提供。 有关详细信息，请参阅Adobe Experience Cloud Administrators](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html)的[常见问题解答。

   **[!UICONTROL Callback server]**&#x200B;地址必须在&#x200B;**https**&#x200B;中指定。 此字段对应于您的Adobe Campaign实例的访问URL。

* IMS组织ID:此信息可在Experience Cloud（**[!UICONTROL Administration > Experience Cloud Details]**&#x200B;中）上找到，并在您首次连接到Adobe Experience Cloud时提供。
* 关联蒙版：此字段允许您定义语法，该语法允许Enterprise 仪表板中的配置名称与Adobe Campaign中的组同步。 如果使用语法“活动 - tenant_id -(.*)“，在Adobe Campaign中创建的安全组将链接到企业仪表板中的配置名称“活动 - tenant_id - internal_name”。

   >[!CAUTION]
   >
   >关联蒙版是通过Adobe ID进行连接以正确工作的关键。

* Adobe Experience Cloud连接信息，特别是Adobe Experience Cloud租户的名称。

